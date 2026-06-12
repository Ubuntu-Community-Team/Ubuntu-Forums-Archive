---
title: "Avermedia VolarX remote problem"
date: 2009-09-06
forum: Multimedia Software
---

### Post by kaar3l on 2009-09-06
I have RM-KS remote. Usb tv card works okay, but remote is a hard thing. I am trying to get it working with lirc. When i press a button the button just keeps pressed all the time, until I disconnect the tv card.

I have tried this [http://www.linuxtv.org/wiki/index.php/Avermedia_DVB-T_Volar_X](http://www.linuxtv.org/wiki/index.php/Avermedia_DVB-T_Volar_X) , but it doesn't work. :(

Does anybody have some good workarounds?

---

### Post by kaar3l on 2009-09-09
I got it working, but i have to use this line:
sudo rmmod usbhid && sudo modprobe usbhid quirks=0x07ca:0xa815:0x0004
Putting the quirks into the modprobe.d folder doesn't work. :/

---

