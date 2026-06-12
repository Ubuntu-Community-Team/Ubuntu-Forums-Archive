---
title: "ampache setup: No way to select language in installation process"
date: 2016-05-30
forum: Multimedia Software
---

### Post by Null_Sieben on 2016-05-30
Ubuntu 16.04
Apache 2.4
PHP 7.0.4
MySQL

# apt-get install ampache
# service apache2 restart

Browsers Firefox or Chrome:  [http://localhost/ampache](http://localhost/ampache)

[ATTACH=CONFIG]269364[/ATTACH]

Any idea what's wrong here?

---

### Post by info-tvnr on 2016-07-26
**same to me :( the select button is gone :(**:confused: I am searching for the problem but there is nothing about it

---

### Post by t-1 on 2016-08-06
Same problem here. Tried several browsers. The error in the apache web server reads:

> [FONT=Menlo]PHP Fatal error:  Uncaught Error: Call to undefined method Error::display() in /usr/share/ampache/www/templates/show_install_lang.inc.php:30\nStack trace:\n#0 /usr/share/ampache/www/install.php(147): require_once()\n#1 {main}\n  thrown in /usr/share/ampache/www/templates/show_install_lang.inc.php on line 30[/FONT]

[FONT=Menlo]Could be a PHP version error. still investigating.[/FONT]

[FONT=Menlo]Some further investigation: it looks like ubuntu xenial is installing a fairly old version of ampache, which may not work with the latest php version that's available in 16.04. continuing investigation...



Found the bug report, it's what I suspected: [/FONT]https://bugs.launchpad.net/ubuntu/+source/ampache/+bug/1578201

---

