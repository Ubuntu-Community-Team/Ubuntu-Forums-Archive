---
title: "apache on ubuntu"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by alambre on 2009-10-16
i want to automatically add "www" whenever i type my site and has included this script already to ".htaccess" but turn out no good. i'm running apache server on ubuntu jaunty 9.04. it runs good on windows server but i'm migrating to ubuntu linux... all of your help wud be appreciated, thank you :D GOD BLESS :-)

RewriteEngine On
RewriteBase /
RewriteCond %{HTTP_HOST} !^example.com$ [NC]
RewriteRule ^(.*)$ http://www.example.com/$1 [L,R=301]

---

