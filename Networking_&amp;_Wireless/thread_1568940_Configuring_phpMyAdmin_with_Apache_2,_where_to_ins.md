---
title: "Configuring phpMyAdmin with Apache 2, where to insert line in apache2.conf?"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by tswann on 2010-09-06
Hi

I'm trying to follow the guide for setting up phpMYAdmin with apache2. The guide says the following:

> To set up under Apache all you need to do is include the following line in /etc/apache2/apache2.conf.

Include /etc/phpmyadmin/apache.conf

My question is, where are you supposed to insert that line?  The guide doesn't say anything and the apache2.conf seems to have a few places where you could insert it.  Any help would be appreciated.

Thanks.

Yours,

Thomas

---

### Post by Waappu on 2010-09-06
Hi,

Insert it at end of /etc/apache2/apache2.conf

Or if you do not like change original config files
create new file to /etc/apache2/conf.d/
```

sudo nano /etc/apache2/conf.d/php.conf

```
And insert line to that file.
That folder files are loaded in apache2.conf and are ment to custom setup

---

