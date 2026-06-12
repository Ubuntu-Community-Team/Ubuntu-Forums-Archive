---
title: "Installing Apache on Ubuntu"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by redbikemaster on 2011-05-09
I don't mean to sound like a total newbie, but how do you install Apache Web Server on Ubuntu 11.04?

This thread might be in the wrong forum, not sure. This seemed like the best place.

---

### Post by uncaspi on 2011-05-09
sudo apt-get install httpd 
to see the apache2 alternatives

---

### Post by Blasphemist on 2011-05-09
Here are some good links though they describe doing more than your question describes.

[http://vmirgorod.name/11/1/20/drupal-development-environment-based-ubuntu-1010](http://vmirgorod.name/11/1/20/drupal-development-environment-based-ubuntu-1010)
[http://httpd.apache.org/docs/2.1/configuring.html](http://httpd.apache.org/docs/2.1/configuring.html)
[http://drupal.org/node/823990](http://drupal.org/node/823990)

---

### Post by redbikemaster on 2011-05-09
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package apache2-mpm-worker 2.2.17-1ubuntu1
E: Couldn't find any package by regex 'apache2-mpm-worker 2.2.17-1ubuntu1'

```

What does this mean? I want to use Apache, but it won't let me install it.

---

### Post by Blasphemist on 2011-05-09
I followed the instructions in the first page I linked in my post.

> Add repositories
sudo add-apt-repository ppa:sun-java-community-team/sun-java6
sudo add-apt-repository ppa:chromium-daily/stable
sudo apt-get update

Install web-server software
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk tasksel subversion cvs git-core apache2 php5-mysql libapache2-mod-php5 mysql-server php5-dev php-pear libevent-dev memcached curl libcurl3 libcurl3-dev php5-curl postgresql postfix postfix-pcre phpmyadmin phppgadmin

I've also done it without all of these packages but this is my recommendation.

---

### Post by hamiljf on 2011-05-09
just installed 11.04 workstation on 'fresh' machine and want to do server work as well.  couldn't find the server stuff in the software centre, so tried the recipe above and got the following...

apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk tasksel subversion cvs git-core apache2 php5-mysql libapache2-mod-php5 mysql-server php5-dev php-pear libevent-dev memcached curl libcurl3 libcurl3-dev php5-curl postgresql postfix postfix-pcre phpmyadmin phppgadmin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libcurl4-openssl-dev' instead of 'libcurl3-dev'
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Unable to locate package sun-java6-bin
E: Package 'sun-java6-jdk' has no installation candidate

btw, also found (elsewhere) suggestion to use

apt-get install lamp-server

that didn't work either... no package found

ideas... please note, not wanting to install ubuntu server, 'cos I want a desktop for dev work on this machine.

used to be simple a few releases back <sigh>

---

### Post by hamiljf on 2011-05-09
This is almost embarrassing... but the default installation includes the synaptic package manager and... joy... all the stuff is there, just like it used to be. installed apache2, php5, etc and 'it works'

---

### Post by redbikemaster on 2011-05-09
I've got a window open here. 
It is for configuring mahara.
It says 
```

Database type: [postgres8 or mysql5]

```
Which one?

---

### Post by Blasphemist on 2011-05-09
Postgre doesn't involve Oracle and is therefore considered a better FOSS player by many. Both work fine though I think mysql is considered to perform somewhat better.

---

### Post by redbikemaster on 2011-05-09
How do I get to Apache? When I try it in the CLI I get:
```

apache2: Syntax error on line 230 of /etc/apache2/apache2.conf: Syntax error on line 72 of /etc/apache2/sites-enabled/gforge: Could not open configuration file /etc/gforge/httpd.secrets: Permission denied

```
Help, please.
I'm sorry I'm such a newbie to this.

---

### Post by Blasphemist on 2011-05-09
I'm not sure just what you mean. If you go to the address in your browser: 
```
localhost
```
you should see, 
> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

This is the documentation for Apache 2.2
[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

BTW, you could have installed LAMP using what are called the LAMP or XAMP appliances. But you are learning more this way. You are thinking things through and learning about the interaction.

---

### Post by redbikemaster on 2011-05-09
Thanks. Going to bed.

---

### Post by Blasphemist on 2011-05-09
Keep me posted if you have other questions. I didn't think long enough or I'd have mentioned the lamp option from the start. I did that when I first started but when I created a new build a while back I did what I did recommend, install a good development platform and am very happy I did. I had done most of what was in the development environment post but not in a good and organized way. Anyway, enjoy.

---

### Post by redbikemaster on 2011-05-12
Sorry it took so long to get back. I worked it out.

---

