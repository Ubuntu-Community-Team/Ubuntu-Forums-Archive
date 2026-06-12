---
title: "need help with 2wire modem/router to linksys router setup"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by miasmablk on 2012-02-26
so today i discerned that the wireless router half of my 2wire modem/router was indeed failing.. so i decided that i would just "bridge" it with my linksys WRT54g2 to correct the problem. not so easy, i found out. there were 9 devices in total connected to the 2wire before.   At the moment i have only been able to succesfully reconnect 4. (roku 2xs, Dell 1545 running 1545, Samsung Captivate rooted running ICS and an xbox 360)

to achieve the bridged connection I have enable DMZ + mode on the 2wire, disabled wireless on the 2wire, connected the two VIA WAN1 on either devices, I can't enable WPA or WEP of any sort on the linksys for some reason or my roku refuses to connect so i can only disable broadcasting of SSID.

now i have 3 other Windows 7 computers that can connect to the linksys but have no internet access, and two android devices which connect and also have no internet access. (samsung infuse stock 2.2 froyo and samsung galaxy s2 stock 2.3.6 gingerbread) what can i do to correct this..im not really a networking guy so i need all the help i can get :confused:

---

### Post by miasmablk on 2012-02-26
never mind tinkered with it for a little while messed with the NAT settings and also found that WPA being enabled on the 2wire even though wireless was disabled was causing some problems also.. i set up a supplementary network in the broadband settings (although i assumed the router behind router mode would take care of this) now everything works.

---

