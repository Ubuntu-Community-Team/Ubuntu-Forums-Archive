---
title: "Apache2 virtual host config"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by jlhughes on 2009-01-17
I have apache2 installed and working. I'm now adding virtual hosts.

I can access "free.mydomain.com/index.html" but I get "Forbidden" when I attempt to access "free.mydomain.com"

I know this is an easy fix, but I can't remember the solution.

Here's the site-available file (with mydomain.com substituted):

<VirtualHost *>
ServerAdmin [email]webmaster@mydomain.com[/email]
#We want to be able to access the web site using [www.dev.example.com](www.dev.example.com) or dev.example.com
ServerName free.mydomain.com
DocumentRoot /home/www/free
CustomLog /var/log/apache2/freefriday-access.log combined

# Protect files and directories from prying eyes:
<Files ~ "(\.(conf|inc|module|pl|sh|sql|theme|engine|xtmpl)|Entries|Repositories|Root|scripts|updates)$">
  order deny,allow
  deny from all
</Files>

# Set some options
Options -Indexes
Options +FollowSymLinks

# Customized server error messages:
ErrorDocument 404 /index.php

</VirtualHost>

---

### Post by superprash2003 on 2009-01-18
[http://www.cyberciti.biz/faq/apache-403-forbidden-error-and-solution/](http://www.cyberciti.biz/faq/apache-403-forbidden-error-and-solution/)

---

