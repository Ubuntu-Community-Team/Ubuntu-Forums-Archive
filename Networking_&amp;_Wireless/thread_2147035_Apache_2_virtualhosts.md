---
title: "Apache 2 virtualhosts"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by verbin on 2013-05-20
Hey all,

i've got a problem with my apache2 virtualhosts configuration.

There are a few sites in /etc/apache2/sites-avaiable/ ([www.tvbeugelsenmeer.nl]("http://www.tvbeugelsenmeer.nl"), [www.lauravanderheide.nl]("http://www.lauravanderheide.nl"))

They are enabled with a2ensite so there is a symlink in /etc/apache2/sites-enabled/
now when i do a # /etc/inint.d/apache2 reload
i get the following output 
```

Reloading web server config: apache2[Mon May 20 20:52:17 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Mon May 20 20:52:17 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Mon May 20 20:52:17 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Mon May 20 20:52:17 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
.

```

but what really counts is the inside of my [www.lauravanderheiden.nl]("http://www.lauravanderheiden.nl") and [www.tvbeugelsenmeer.nl]("http://www.tvbeugelsenmeer.nl") files which is listed here:

[www.tvbeugelsenmeer.nl]("http://www.tvbeugelsenmeer.nl")
```

<VirtualHost *:80>
        ServerAdmin test@hotmail.com
        ServerName  www.tvbeugelsenmeer.nl
        ServerAlias tvbeugelsenmeer.nl

        # Indexes + Directory Root.
        DirectoryIndex index.html index.php
        DocumentRoot /home/tvbeugelsenmeernl/

</VirtualHost>

```

[www.lauravanderheide.nl]("http://www.lauravanderheide.nl")
```

<VirtualHost *:80>
        ServerAdmin test@hotmail.com
        ServerName  www.lauravanderheide.nl
        ServerAlias lauravanderheide.nl

        # Indexes + Directory Root.
        DirectoryIndex index.html index.php
        DocumentRoot /home/lauravanderheidenl/

</VirtualHost>


```

So why do i get these errors?

---

### Post by linuxtechguy on 2013-05-21
Because your namevirtualhost setting probably has x.x.x.x:80 and not *:80. Either change your namevirtualhost setting or your virtualhost

---

