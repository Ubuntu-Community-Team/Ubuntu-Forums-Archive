---
title: "system sock proxy settings not working"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by goof on 2013-06-22
hi i am setting system proxy through bash fiile with command

#!/bin/bash
gsettings set org.gnome.system.proxy.socks host '127.0.0.1'
gsettings set org.gnome.system.proxy.socks port 9050
gsettings set org.gnome.system.proxy mode 'manual'

this seems to workkm fine in my browser firefox but when i get my ip through wget with commands

wget [http://ipecho.net/plain](http://ipecho.net/plain) -O - -q ; echo

it returns my unproxied ip how ome and how can i fix this i tought sysyetem proxy dealth with all my traffic

---

### Post by goof on 2013-06-23
does anyone know how to route all traffic through proxy?

---

### Post by goof on 2013-06-24
sorry just to be clear i want to set a proxy for all type of net traffic 
[TABLE]
[TR]
[TD="class: ComparisonChrt_td2_ColmnHead"]FTP[/TD]
         [TD="class: ComparisonChrt_td2_ColmnHead"]FTPS[/TD]
         [TD="class: ComparisonChrt_td2_ColmnHead"]SFTP[/TD]
         [TD="class: ComparisonChrt_td2_ColmnHead"]HTTP[/TD]
         [TD="class: ComparisonChrt_td2_ColmnHead"]HTTPS and anything lse that goes to the web like a vpn thanks
[/TD]
[/TR]
[/TABLE]

---

### Post by dentaku65 on 2013-06-25
If you have set Tor as proxy and running (seems so to me because server: 127.0.0.1 and port: 9050), try to execute the shell command in this way:
```
torsocks wget http://ipecho.net/plain -O - -q ; echo
```
Torsocks command should be able to manage all the tor connections outside the browser.

---

