---
title: "XAMPP php.ini missing zend_extension` section. Trying to install ionCube loader."
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by cosname on 2013-09-01
I installed [XAMPP]("http://www.apachefriends.org/ru/xampp.html")
So the problem is such:
in php.ini have no records such like:
[zend]
zend_extension: ...
The ionCube requires to add one like that:
[COLOR=#202060][FONT=monospace]zend_extension = /path/to/ioncube_loader_lin_5.2.so

[/FONT][/COLOR]I`m not good with Apache configuration, and just can`t make that done :(
Please help!


RELEASENOTES
```

[2012-09-30] XAMPP for Linux 1.8.1


This version of XAMPP includes:
    - Apache 2.4.3
    - MySQL 5.5.27
    - PHP 5.4.7
    - Perl 5.14.2
    - ProFTPD 1.3.4a
    - phpMyAdmin 3.5.2.2
    - OpenSSL 1.0.1c
    - GD 2.0.1
    - Freetype 2.1.7
    - libjpeg 6b
    - libpng 1.2.12
    - gdbm 1.8.0
    - zlib 1.2.3
    - expat 1.95.2
    - Sablotron 1.0
    - libxml 2.7.6
    - libxslt 1.1.26
    - Ming 0.4.3
    - Webalizer 2.21-02
    - pdf class 009e
    - ncurses 5.7
    - mod_perl 2.0.5
    - FreeTDS 0.63
    - gettext 0.17
    - IMAP C-Client 2007e
    - OpenLDAP (client) 2.4.21
    - mhash library 0.8.18
    - mcrypt library 2.5.7
    - cURL 7.21.0
    - SQLite 2.8.17 (for PHP4 + PHP5)
    - SQLite 3.6.16 (for PHP5 PDO SQLite)
    - libapreq 2.12
    - eAccelerator 0.9.6.1
    - FPDF 1.6
    - bzip2 (library) 1.0.5
    - PBXT 1.0.11-6-pre-ga
    - PBMS 0.5.15 (but disabled)
    - PBMSlib 0.5.15
    - ICU4C Library 4.2.1
    - APR 1.4.6
    - APR-utils 1.4.1


New in this version of XAMPP:
    - New version of Apache (2.4.3)
    - New version of PHP (5.4.7)
    - New version of MySQL (5.5.27)
    - Nev version of phpMyAdmin (3.5.2.2)

```

---

### Post by cosname on 2013-09-01
Guys i know nothing about proper understanding of Apache configuration...
But seems that i`v manage this alone....

```
[zend]
zend_extension = /opt/lampp/lib/php/ioncube/ioncube_loader_lin_5.4.so
```

Just before
```
[gd]
```

Note: i had no [zend] record in my /opt/lampp/etc/php.ini file. Managed for local development only...

---

