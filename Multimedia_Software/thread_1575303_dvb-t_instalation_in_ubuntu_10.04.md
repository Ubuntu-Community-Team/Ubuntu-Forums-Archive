---
title: "dvb-t instalation in ubuntu 10.04"
date: 2010-09-15
forum: Multimedia Software
---

### Post by hodged02 on 2010-09-15
Hi all, I need help getting my usb dvb-t stick working the stick works great in windows using Arcsoft Totalmedia software, but i need to get it working on ubuntu 10.04, but I still cannot find the device in any software used, i have used mythTV and Kaffine, but when I try to add the device in the settings I cannot see it, I have basic knowlage of terminal commands so step by step help would be good.

this is my dvb-t usb stick:-
[http://www.tvstick.co.uk/products/productinfo.asp?catid=1&prodid=4](http://www.tvstick.co.uk/products/productinfo.asp?catid=1&prodid=4)

found out that its a geniatech t680
windows drivers are:
[http://www.geniatech.com/dwonloadf/DownloadFile01.asp?Keyword=t680&sel_os=windows%20xp](http://www.geniatech.com/dwonloadf/DownloadFile01.asp?Keyword=t680&sel_os=windows%20xp)
but can't even use these as not seen in hardware drivers

:popcorn:

---

### Post by jimmers on 2010-09-16
Try installing :-

DVB-APPS
W-SCAN
GXINE
 All available through Synaptic, I installed them and my DVB-T Stick works great, not the same stick as yours, but worth a try, Gxine I need to get Kaffeine to work, but with them installed I get 42 TV Channels and 21 Radio Channels.

May not work for you, but as I said worth a try.


Luck


Jim

---

### Post by hodged02 on 2010-09-16
hi Jim

I had DVB-APPS and W-SCAN, installed already, added GXINE, but still nothing, usb stick still looks dead, but in terminal if I use

lsusb I get:

Bus 001 Device 006: ID 04b4:8613 Cypress Semiconductor Corp. CY7C68013 EZ-USB FX2 USB 2.0 Development Kit

so ubuntu sees it but nothing else works

---

