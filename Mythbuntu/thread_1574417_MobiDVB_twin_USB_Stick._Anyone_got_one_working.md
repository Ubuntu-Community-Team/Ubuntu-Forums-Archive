---
title: "MobiDVB twin USB Stick. Anyone got one working?"
date: 2010-09-14
forum: Mythbuntu
---

### Post by twin--turbo on 2010-09-14
10.04 + Myth.23
 
I purchased a USB twin DVB tuner of ebay hopign to get it working. 
 
 
in lsusb it reports as an with ID 15a4:1001
 
which mathces the ezcap DVBT 
 
[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices)
 
[http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick](http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick)
 
I have followed the how-to.
 
But when I insert the pen drive it shows a driver load in /var/log/messages 
 
but fails with error 9. 
 
( sorry I am not near the machien at the moment to copy the full text.
 
Has anyone managed to get one working?
 
 
Thanks
 
Rob

---

### Post by LowSky on 2010-09-14
I cant find any product named MobiDVB twin USB on ebay or google...hmmm

Can we see the output of lspci and when you can the outpu of /var/log/messages

sorry we can not really do much without full knowlege of the device and the problem you are having.

---

### Post by piginabox on 2010-09-16
I never had any luck with it. It's an AF9035 based one i think. Some forums suggest it can be got working. The first problem on Ubuntu is that the system incorrectly identifies it as a keyboard device.

---

### Post by twin--turbo on 2010-09-27
[http://cgi.ebay.co.uk/DUAL-HDTV-USB-FREEVIEW-DVB-T-DIGITAL-TV-TUNER-Laptop-PC-/270636698526?pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item3f03344b9e](http://cgi.ebay.co.uk/DUAL-HDTV-USB-FREEVIEW-DVB-T-DIGITAL-TV-TUNER-Laptop-PC-/270636698526?pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item3f03344b9e)
 
 
it is indeed an af9035, 
 
Think it's a bit of a dead loss, and as it stands my front end machine now seems to be dead. 
 
I was hoping to consolidate from the big power hungry P4 back end machine + front end ( a tiny little acer Veriton L410 ) to just the Acer. Hopefully I can get the Acer running again. 
 
If so I guess I will have to invest in a Haupage DVB USB tuner.
 
Cheers
 
Rob

---

### Post by kuro_man on 2010-11-18
I am in the same boat - didn't see this post

For my efforts, see:
[http://ubuntuforums.org/showthread.php?t=1624764](http://ubuntuforums.org/showthread.php?t=1624764)

---

