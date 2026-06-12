---
title: "Proxy HostName:PortNumber to HostName/PageName"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by QuinRiva on 2011-07-17
I currently run a bunch of programs accessible through WebUI's on my Headless Ubuntu Server 11.04, and I want to redirect the unintuitive [https://ServerName:PortNumber](https://ServerName:PortNumber) to [https://ServerName/PageName](https://ServerName/PageName).
I have tried following these directions for Webmin:
> [LIST=1][*]Make sure [FONT="Courier New"]mod_proxy[/FONT] is installed on your Apache webserver.
[*]Add the following directives to the Apache configuration file:
```
ProxyPass /webmin/ [http://localhost:10000/](http://localhost:10000/)
ProxyPassReverse /webmin/ [http://localhost:10000/](http://localhost:10000/)
<Proxy *>
allow from all
</Proxy>
```
[*]Add the lines [FONT="Courier New"]webprefix=/webmin[/FONT] and [FONT="Courier New"]webprefixnoredir=1[/FONT] to [FONT="Courier New"]/etc/webmin/config[/FONT].
[*]In [FONT="Courier New"]/etc/webmin/config[/FONT], add the line [FONT="Courier New"]referer=apachehost[/FONT], where *apachehost* is the hostname from the URL used to access Webmin via Apache. If the [FONT="Courier New"]referer[/FONT] line already has some hosts listed, add *apachehost* to it.
[*]Re-start Apache to apply the configuration.[/LIST]

As well as disabling ssl in miniserv.conf, however when I go to [http://ServerName/Webmin](http://ServerName/Webmin) I get a 404 error.  The apache2 error log just states:
```
[client 192.168.1.2] File does not exist: /var/www/favicon.ico
[client 192.168.1.2] File does not exist: /var/www/webmin
```

Given that I would like to redirect:
[LIST]
[*]Webmin
[*]SABnzbd+
[*]SickBeard
[*]Deluge
[*]Transmission
[*]CouchPotato
[/LIST]

Is there a simpler way of doing this?

---

### Post by anuvnu387 on 2011-10-13
Bump!

I am looking for a solution to this as well.

OP, if you already figured it out could you please let me know what you did?

Thanks

---

