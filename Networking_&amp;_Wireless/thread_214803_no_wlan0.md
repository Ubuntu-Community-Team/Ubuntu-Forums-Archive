---
title: "no wlan0??"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by zjcim on 2006-07-13
i get a dlnk dwl-650 pcmcia card
when i insert to the slot ,the ¨ACT¨ on the card light up
and i try iwconfig ,the found no wlan0 something like that

maybe ndiswrapper should work? So i apt-get install the ndiswrapper,ndiswrapper -l install then winxp driver,dmesg show #@$@$,loaded,and modprobe ndiswrapper ,the dlink card seems no response,just the ACT light there always,the i try iwconfig ,there´s still no wlan0


what should i do ?

---

### Post by alecjw on 2006-07-14
Shouldn't it be called eth1 if you have an LAN controller or eth0 if you don't?

---

