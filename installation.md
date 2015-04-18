# Installation

- Install Composer
- Install Pingpong CMS
- Server Requirements

## Install Composer

Pingpong CMS utilizes [Composer](http://getcomposer.org/) to manage its dependencies. So, before using Pingpong CMS, you will need to make sure you have Composer installed on your machine.

## Install Pingpong CMS

### Via Pingpong CMS Installer

First, download the Pingpong CMS installer using Composer.

```
composer global require "pingpongcms/installer=~1"
```

Make sure to place the `~/.composer/vendor/bin` directory in your `PATH` so the `pingpongcms` executable can be located by your system.

Once installed, the simple `pingpongcms new` command will create a fresh Pingpong CMS installation in the directory you specify. For instance, `pingpongcms new blog` would create a directory named `blog` containing a fresh Pingpong CMS installation with all dependencies installed. This method of installation is much faster than installing via Composer:

```
pingpongcms new blog
```

### Via Composer Create-Project

You may also install Pingpong CMS by issuing the Composer `create-project` command in your terminal:

```
composer create-project pingpongcms/pingpongcms --prefer-dist
```

## Server Requirements

The Pingpong CMS framework has a few system requirements:

- PHP >= 5.4
- Mcrypt PHP Extension
- OpenSSL PHP Extension
- Mbstring PHP Extension
- Tokenizer PHP Extension

As of PHP 5.5, some OS distributions may require you to manually install the PHP JSON extension. When using Ubuntu, this can be done via `apt-get install php5-json`.

## Permissions

Pingpong CMS may require some permissions to be configured: folders within `storage` and `vendor` require write access by the web server.

## Pretty URLs

### Apache

The framework ships with a `public/.htaccess` file that is used to allow URLs without `index.php`. If you use Apache to serve your Pingpong CMS application, be sure to enable the `mod_rewrite` module.

If the `.htaccess` file that ships with Pingpong CMS does not work with your Apache installation, try this one:

```
Options +FollowSymLinks
RewriteEngine On

RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^ index.php [L]
```

### Nginx

On Nginx, the following directive in your site configuration will allow "pretty" URLs:

```
location / {
    try_files $uri $uri/ /index.php?$query_string;
}
```

Of course, when using Homestead, pretty URLs will be configured automatically.