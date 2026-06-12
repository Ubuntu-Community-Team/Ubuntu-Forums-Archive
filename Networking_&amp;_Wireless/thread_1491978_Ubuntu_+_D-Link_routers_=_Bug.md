---
title: "Ubuntu + D-Link routers = Bug?"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by Pontus Ohman on 2010-05-24
Hey folks!

I'm turning over hear due to no responds in Sweden where two as far as I  know got problems with Ubuntu 10.04 and two diffrent D-Link routers.  I'm one of them that got BIG problems with Ubuntu and a D-Link DIR-635  router, the other got the exact same problems as I have but with a  D-Link DIR-615.

I want to check if this is a bug before i spend money to call D-Link and  report this failure.

The problem is that when you try connect to the router, it dosen't  matter how many times you enter the correct password. The connections  fails, first after about 30 minutes, Ubuntu gets the connections with  the router and accept the password. The password I have tried under 30  minutes...

I found the solution that I went upstairs to a computer that then had  Windows Vista and removed the network, and re-enter the password for it.  THEN the router accepted my password from my Ubuntu lappy...

Therefore, is this i bug under Ubuntu, or not?

Best regards
Pontus Ohman
Sundsvall GNU/Linux User Group

---

### Post by puppywhacker on 2010-05-24
I took a DIR-615 fresh from the package and hooked the LAN-1 directly to my Ubuntu 10.04 Desktop. The internet connector didn't work for me. I manually set the ip-address on the ubuntu to 192.168.0.1 and immediately could connect to the admin-gui [http://192.168.0.1/](http://192.168.0.1/) it accepted admin as user and the empty password. At first I disabled the DHCP server on the 4 Lan-ports, but after configuring the WLAN I enabled it again since my Ubuntu 10.04 laptop didn't connect to the wireless at first because the Ubuntu Network-Manager was set to auto and I disabled the DHCP server. It is NM that therefor didn't want to connect.

So in short I do not have the same issues as you reported, I think calling D-Link is a waste of time.

When you do call them, ask them where to disable the admin-gui over the WLAN. And ask them to disable this in the future by default. The box is not secure by default.

---

### Post by leclerc65 on 2010-05-24
I have no problem with D-Link (Dir-524, Dir-628) , but I use Mac filter instead of WEP, WPA.

---

