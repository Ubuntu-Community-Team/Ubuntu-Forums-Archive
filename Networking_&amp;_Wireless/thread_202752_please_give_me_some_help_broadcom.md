---
title: "please give me some help broadcom"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by kcallstar7 on 2006-06-24
got my dv4000 laptop ... and so i blacklist bcm43xx from my modprob.d blacklist ... but when i do that when i reboot i dont have any option at all for wireless support... when i take it off the blacklist... i get the option to enable my wireless but when i activate it it still wont connect... why is it so hard to get this broadcom wireless thing on one page... i really need to get my wireless up and running i nothing seems to help when i take it of modprobe.d. blacklist and do iwconfig i get:
lo no wireless extensions.

eth1 IEEE 802.11b/g ESSIDff/any Nickname:"Broadcom 4318"
Mode:Managed Access Point: Invalid Bit Rate=1 Mb/s
RTS thrff Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth0 no wireless extensions.

sit0 no wireless extensions.

please i want to get linux wireless someone help!!

---

### Post by Dr. Nick on 2006-06-24
ok, Let me preface this by saying I dont have a broadcom chipset so cant help with some specifics but can be of some help hopefully

when you blacklisted it I assume it does not show up anywhere when you run **lsmod** correct? I would think thats a yes since you seem to lose all wireless config options.

Also if you sucesfully blacklist it what do you expect to use in its place? Have you setup ndiswrapper correctly?


Blacklisting the broadcom module and not using ndiswrapper means that linux isnt loading any wireless drivers, thus you cant configure your card.

Thier is alot of broadcom info here like [this]("http://ubuntuforums.org/showthread.php?t=195136") thread, not sure where the poster ended up on it, but it has some good suggestions of things to look at

---

### Post by jhr79 on 2006-06-24
This will probably help you at least to start [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

