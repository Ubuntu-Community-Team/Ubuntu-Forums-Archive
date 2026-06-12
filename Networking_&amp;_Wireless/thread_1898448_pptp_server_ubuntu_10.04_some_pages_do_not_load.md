---
title: "pptp server ubuntu 10.04 some pages do not load"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by karentom on 2011-12-21
Hy to all users here. This is my first post on the forum so thank you all in advance on your future replies.
My problem is that I successfully set up ubuntu 10.04 LTS as my PPTP vpn server and I can successfully connect from my windows clients (WinXP and Win7) and I can surf the web quite ok (ubuntu server is VPN gateway), but some pages can not load, for example: [https://www.facebook.com/](https://www.facebook.com/) (SSL) 
or
[https://connect.facebook.net/hr_HR/all.js](https://connect.facebook.net/hr_HR/all.js).

I followed this tutorial for my setup:
[http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)
server software is pptpd

Majoriti web pages load ok, even https or just plain http protocol, but some not.
Can you please help?

---

### Post by jonobr on 2011-12-21
Hey There


Given that some are working and some are not,

Do you think it may be related to [this]("http://ubuntuforums.org/showthread.php?t=1788411") thread?

---

### Post by karentom on 2011-12-21
Thank you on your reply!
I think it is not related.
When I try to load this pages from the Ubuntu machine everyithing is good and all pages work, but when the Ubuntu acts like VPN PPTP server (gateway to the internet) it is not possible to load those pages in client machine browser and in the same time aprox. 90% of pages around internet loads ok in client browser but some not and I can not figure it out what is the reason and how to repair that.
I think that this is related with this tread: [http://ubuntuforums.org/showthread.php?t=1790022](http://ubuntuforums.org/showthread.php?t=1790022)
I found it after I opened this thread.

---

### Post by jonobr on 2011-12-21
Hello


Did you try to ping these websites when the tunnel was up and you were having trouble?

Is it always the same websites?

When you have trouble getting to a website eg [http://website.com](http://website.com)

did you try an nslookup website.com 
command to make sure dns resolution is working ok?
If that returns an ip address, try putting that IP into a browser


Thnaks

Jonobr

---

### Post by karentom on 2011-12-23
When the pptp tunel is on and when Ubuntu VPN server is gateway for my windows clients i tried what you asked and:
- I can successfully ping site connect.facebook.net
- nslookup work ok and resolves ip 2.21.111.139
- I can successfully load [http://connect.facebook.net](http://connect.facebook.net) **but I can not load [https://connect.facebook.net](https://connect.facebook.net)**  in the client browser (Firefox, IE, Opera... no meter what).
- **same problem** is when I use the ip address 2.21.111.139 instead of domain - http ok and https NOT ok
- when pptp connection is closed everything is back to ok and I can successfully load [http://connect.facebook.net](http://connect.facebook.net) and http**s**://connect.facebook.net in client browser

---

### Post by karentom on 2011-12-27
I tested the problem with configuration in wich I replaced Ubuntu VPN server with Debian 6.0 with pptpd server and the problem is same, so I can replicate the problem on completly different machine with same setup beside Ubuntu is changed with Debian.

I am pretty sure that the problem is something with routing - iptables or similar on Ubuntu (or Debian) in my configuration. Can someone please check if this guide (that I followed) is ok and if there is something missed that should be done. Guide is: [http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)

_***Especially***_:

**1.) ***sudo nano /etc/rc.local*
 Add the following line
**iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE**



**2.)**  sudo nano /etc/sysctl.conf
uncomment
**net.ipv4.ip_forward=1**
 


Tnx in advance!

---

### Post by karentom on 2011-12-30
Anyone have some idea? Anything to try at least. TNX in advance

---

