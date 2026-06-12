---
title: "apache2 not following symlinks outside /var/www tree"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by rasti121 on 2012-08-30
Hi,

I have upgraded to LTS 12.04.1 last night. Didn't let the upgrader change my config files. I have squirrelmail and phpmyadmin installed from packages (they are installed in /usr/share). I have a symlink from /var/www/virtualserver/closed to /var/www/closed. /var/www/closed is a password digest protected directory (through .htaccess) which contains links to /usr/share/squirrelmail and /usr/share/phpmyadmin. The virtual server is set to follow symlinks.

I cannot access the /var/www/closed/squirrelmail (and .../phpmyadmin), but I can access the /var/www/closed. This means the apache2 server is honouring and following the 1st symlink (accessing /var/www/virtualserver/closed) but not the 2nd which points outside of web root (to /share/usr, my web root being default /var/www).

I'm currently using an Alias directive to access /share/usr/squirrelmail, but had to copy a .htaccess file in there to control access and would have to do it for each directory outside www root again. I chaecked the priority on the files it's always r+x (or 5) for other.

Anyone had a problem following symlinks outside web root with the new 12.4.1 LTS server?

In case it's not obvious this was all working in 10.4.4 LTS before upgrading to 12.4.1 LTS and some kind of phpmyadmin database upgrade failed during the upgrade procedure, no other errors.

Thanks for help.

---

### Post by SlugSlug on 2012-08-30
am pretty sure www-data will need perms to each parent folder so
/share & /share/usr

I've had similar probs - but wait for someone a bit more clued up on it than me :)

---

### Post by rasti121 on 2012-08-30
> **SlugSlug said:**
> am pretty sure www-data will need perms to each parent folder so
/share & /share/usr

I've had similar probs - but wait for someone a bit more clued up on it than me :)

Yes, it does, that's why I checked that /usr/share has read and execute for "other" (i.e. including www-data user). File is own by root.

---

### Post by SlugSlug on 2012-08-30
does 

```
tail /var/log/apache/error.log
```

show you anything

---

### Post by rasti121 on 2012-08-30
> **SlugSlug said:**
> does 

```
tail /var/log/apache/error.log
```

show you anything

"Symbolic link not allowed or link target not accessible"

(I do have

Options +Indexes +FollowSymLinks

in the /var/www/closed's VirtualHost definition)

---

### Post by rasti121 on 2012-09-12
I uncommented all following lines from <Directory> in sites-enabled and also the links outside /var/www are followed now:

                AllowOverride All
                Order allow,deny
                allow from all

Must be (???) a behaviour change between apache2 (10.4.4->12.4.1) versions.

---

