---
title: "My sound won't work!"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by mrstarware on 2007-09-12
Hi, I'm using ubuntu 7 and my logitech headset will only "partially" work.

It's suppose to be "plug in play" and is so on windows, however on ubuntu after switching the settings to "USB AUDIO" I can hear the little beeping tests however the main sound such as the system login or a youtube video won't work. 

Please let me know if you need more information


Thanks,


mrstarware

---

### Post by mrstarware on 2007-09-12
Well it appears that kaffine can play sound so I guess my only problem is getting sound from a web browser to my computer?

---

### Post by heimo11656 on 2007-09-14
I'm having the same problem with my logitech usb headset.

I hear that beep when i test in sound config, but any other sound comes only from my speakers.

lsusb returns the following:

Bus 003 Device 004: ID 046d:0a02 Logitech, Inc. 
Bus 003 Device 005: ID 047d:1029 Kensington 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

---

### Post by mrstarware on 2007-09-16
Mine returns this

Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 046d:0a02 Logitech, Inc. 
Bus 004 Device 002: ID 05fe:1010 Chic Technology Corp. 
Bus 004 Device 001: ID 0000:0000  


Also I did get my headset working however it's stopped again and I don't know why.

---

### Post by mrstarware on 2007-09-16
I think this is the solution

[https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12](https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760/comments/12)

---

