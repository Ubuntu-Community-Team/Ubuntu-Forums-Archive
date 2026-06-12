---
title: "force static Ip on Apache server"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by Gordonisnz on 2013-01-24
I have made apache server boot up automatically when I start the PC.

in my IFCONFIG, i see :-

inet addr:192.168.1.76  Bcast:192.168.1.255  Mask:255.255.255.0

Now if I put 192.168.1.76 into my browser  - I see my local server.

Problem - the last figure "76" keeps on changing each time Apache starts / the PC starts up.


PS - i Do know  this IP is 'local' only to my PC & anyone connected to my Computer via Wifi. 

I do not want anyone in Africa, china, UK, USA or Australia etc accessing my files - I just use it for wifi / local use.

I also know that the ISP's assign random IP addresses to users - but this part is controlled by my local machine (I do not need an external source like no-ip.com). I do not need a static IP through my ISP.

Is there a way of forcing apache to stick to a single IP address ? - so anyone within range of my wifi (& who knows my wifi password), can access the apache server.


PS (EDIT) - i do not mind if i name a server.

Eg - [http://myserver/](http://myserver/) will bring up my apache server - & anyone connected with wifi.  (anyone out of range & not connected to my wifi will not see the server).

Is it possible / easy to 'name' an Apache server - regardless of what IP address it has been assigned at logon ?

---

### Post by Cheesemill on 2013-01-24
Either edit your router configuration so that it always assigns your server the same IP address or set up the server with a static IP.

To give your server a static IP address simply edit the /etc/network/interfaces file and edit the section that looks like this...
```
auto eth0
iface eth0 inet dhcp
```
So that it looks like the following (obviously you may need to change the numbers and interface)...
```
auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 192.168.1.1
```

---

