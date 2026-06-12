---
title: "help with wireless"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by PriceChild on 2006-04-11
Hey :) I'm trying to connect two computers together over wireles, both are using RT2500 ralink cards.

In ubuntu, i've used gtkwifi to scan for and find the network of the windows pc which i created on it. It connects, however, i can't even ping either computer, even after setting the ips on both machines.

Any ideas?

Pricey

---

### Post by spanishwasabi on 2006-04-11
Are you using ad-hoc or an AP based network?

Check your routing in case of:
route -n

Enjoy,

G

---

### Post by PriceChild on 2006-04-11
adhoc.

I really really should splash out on an adsl wireless router shouldn't i :)

---

### Post by spanishwasabi on 2006-04-12
:-)

Let's say an AP simplifies things quite a bit.

But if I remember well, there's a way of putting a wireless card under ad-hoc with the command line:
iwconfig eth0 mode ad-hoc

Or try this in both computers for a long term solution.
In /etc/network/interfaces :

> 
auto eth1
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
wireless-essid mynetwork
wireless-channel 6
wireless-mode ad-hoc


then ifdown eth1 to bring it down
then ifup eth1 to bring it up

This has no wep or wpa, but you should add it if you are concerned about security.

Enjoy,

G

---

### Post by Bezvardis on 2006-07-10
> This has no wep or wpa, but you should add it if you are concerned about security.
does ad-hoc really allow wep or wpa keys? I used to have ad-hoc wereless network at home with Windows and there in all instructions it said that ad-hoc (or peer-to-peer) wireless networks don't allow for wep or wpa to be used. Now, I have set up ad-hoc network (with internet sharing) with Ubuntu desctop and Mac PowerBook. But as soon as I would try putting the encription (system>networking>wireless devices), the connection would stop. I tried just for experimenting purposes a key 123456 (both under Hexidecimal and ASCII) but with the same negative result. Maybe I am trying a wrong key? Is there a definite length of the key?

---

### Post by spanishwasabi on 2006-07-10
> **Bezvardis said:**
> does ad-hoc really allow wep or wpa keys? I used to have ad-hoc wereless network at home with Windows and there in all instructions it said that ad-hoc (or peer-to-peer) wireless networks don't allow for wep or wpa to be used. Now, I have set up ad-hoc network (with internet sharing) with Ubuntu desctop and Mac PowerBook. But as soon as I would try putting the encription (system>networking>wireless devices), the connection would stop. I tried just for experimenting purposes a key 123456 (both under Hexidecimal and ASCII) but with the same negative result. Maybe I am trying a wrong key? Is there a definite length of the key?

Mmm... you made me doubt... theorically speacking there's no reason why ad-hoc could not have WEP.

A quick look in Google tend to confirm my impression:
[http://forums.wi-fiplanet.com/archive/index.php/t-2806.html](http://forums.wi-fiplanet.com/archive/index.php/t-2806.html)
[http://www.wi-fiplanet.com/tutorials/article.php/3494246](http://www.wi-fiplanet.com/tutorials/article.php/3494246)
[http://www.microsoft.com/windowsxp/using/networking/expert/bowman_02april08.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/bowman_02april08.mspx)   
(yeah, I know the last one is Microsoft, but we're talking about Wireless, if Microsoft can do it we can too).

It seems that the key must be 40 bit long. Try to set it up from the command line instead...

Sorry I can not help you more.

G

---

