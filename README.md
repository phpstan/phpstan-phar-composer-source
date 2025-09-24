phpstan.phar Composer source
------------------------

When the user installs PHPStan with Composer with preference for source instead of dist:

```
composer require phpstan/phpstan --prefer-source
```

Composer would clone the entire [`phpstan/phpstan`](https://github.com/phpstan/phpstan) repository which has multiple gigabytes in size, because it contains all compiled phpstan.phar files for each [phpstan-src](https://github.com/phpstan/phpstan-src) commit in its history.

Cloning the entire repository often fails with timeouts and leads to bad initial user experience for users who configured Composer to clone entire repositories instead of downloading small dist .zip files.

Thanks to an undocumented Composer feature, it's possible to override which repository will Composer clone during installation.

This repository (`github.com/phpstan/phpstan-phar-composer-source`)  is referenced in `source` key in `phpstan/phpstan` [composer.json](https://github.com/phpstan/phpstan/blob/2.1.x/composer.json) file.

When the user tries to use PHPStan with this repository in their `vendor/` directory, a script downloads `phpstan.phar` from [GitHub releases](https://github.com/phpstan/phpstan/releases) and prints a short warning before running PHPStan as usual.
