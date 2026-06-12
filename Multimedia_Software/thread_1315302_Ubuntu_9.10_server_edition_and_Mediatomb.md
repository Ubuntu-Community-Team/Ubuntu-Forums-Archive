---
title: "Ubuntu 9.10 server edition and Mediatomb"
date: 2009-11-05
forum: Multimedia Software
---

### Post by spikecity on 2009-11-05
Hi guys,
 
Finally gutsy enough to build a nix server based on Ubuntu 9.10 Server edition and ISPControl 3 to set the web/mail/ftp and server stuff from a browser.
 
All working like a champ until I decided to install a UPNP media server.
First I tried Firefly, installed correctly, visible in netstat as a listening process, but no web gui on the given address.... Connection error in browser
 
Uninstalled Firefly, installed Mediatomb, no problems whatsoever, running in netstat
 
> 
root@mail:/var# netstat -tulpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 0.0.0.0:25 0.0.0.0:* LISTEN 1932/master
[COLOR=red]tcp 0 0 0.0.0.0:49152 0.0.0.0:* LISTEN 4754/mediatomb[/COLOR]
tcp 0 0 127.0.0.1:10024 0.0.0.0:* LISTEN 974/amavisd (master
tcp 0 0 127.0.0.1:10025 0.0.0.0:* LISTEN 1932/master
tcp 0 0 0.0.0.0:3306 0.0.0.0:* LISTEN 1114/mysqld
tcp 0 0 127.0.0.1:783 0.0.0.0:* LISTEN 1188/spamd.pid
tcp 0 0 0.0.0.0:111 0.0.0.0:* LISTEN 670/portmap
tcp 0 0 0.0.0.0:53620 0.0.0.0:* LISTEN 709/rpc.statd
tcp 0 0 0.0.0.0:21 0.0.0.0:* LISTEN 1945/pure-ftpd (SER
tcp 0 0 192.168.1.5:53 0.0.0.0:* LISTEN 1844/mydns
tcp 0 0 127.0.0.1:53 0.0.0.0:* LISTEN 1844/mydns
tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN 2444/sshd
tcp6 0 0 :::443 :::* LISTEN 4859/apache2
tcp6 0 0 :::445 :::* LISTEN 1963/smbd
tcp6 0 0 :::993 :::* LISTEN 1802/couriertcpd
tcp6 0 0 :::995 :::* LISTEN 1840/couriertcpd
tcp6 0 0 :::139 :::* LISTEN 1963/smbd
tcp6 0 0 :::110 :::* LISTEN 1819/couriertcpd
tcp6 0 0 :::143 :::* LISTEN 1776/couriertcpd
tcp6 0 0 :::8080 :::* LISTEN 4859/apache2
tcp6 0 0 :::80 :::* LISTEN 4859/apache2
tcp6 0 0 :::21 :::* LISTEN 1945/pure-ftpd (SER
tcp6 0 0 ::1:53 :::* LISTEN 1844/mydns
tcp6 0 0 :::22 :::* LISTEN 2444/sshd
[COLOR=red]udp 0 0 0.0.0.0:1900 0.0.0.0:* 4754/mediatomb[/COLOR]
udp 0 0 0.0.0.0:111 0.0.0.0:* 670/portmap
udp 0 0 0.0.0.0:50803 0.0.0.0:* 709/rpc.statd
udp 0 0 0.0.0.0:885 0.0.0.0:* 709/rpc.statd
udp 0 0 192.168.1.5:123 0.0.0.0:* 2502/ntpd
udp 0 0 127.0.0.1:123 0.0.0.0:* 2502/ntpd
udp 0 0 0.0.0.0:123 0.0.0.0:* 2502/ntpd
udp 0 0 192.168.1.5:137 0.0.0.0:* 1959/nmbd
udp 0 0 0.0.0.0:137 0.0.0.0:* 1959/nmbd
udp 0 0 192.168.1.5:138 0.0.0.0:* 1959/nmbd
udp 0 0 0.0.0.0:138 0.0.0.0:* 1959/nmbd
udp 0 0 192.168.1.5:53 0.0.0.0:* 1844/mydns
udp 0 0 127.0.0.1:53 0.0.0.0:* 1844/mydns
[COLOR=red]udp 0 0 127.0.0.1:49869 0.0.0.0:* 4754/mediatomb[/COLOR]
udp6 0 0 fe80::20c:76ff:fe8a:123 :::* 2502/ntpd
udp6 0 0 ::1:123 :::* 2502/ntpd
udp6 0 0 :::123 :::* 2502/ntpd
udp6 0 0 ::1:53 :::* 1844/mydns

 
But again no web gui at the [http://192.168.1.5:49152](http://192.168.1.5:49152).... dead as a horse, connection error in the browser (so not a 404 page not found).
 
So it seems that this isn't a problem with one of the media server packages, but with my Ubuntu setup....
 
ufw is inactive, so no firewall, apache running and serving up websites...
 
Actually I'm kind of lost now as a nix newby... so any assistance is greatly appreciated to get mediatomb working.

---

### Post by sdowney717 on 2009-11-14
try minidlna or ushare
[http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)

---

