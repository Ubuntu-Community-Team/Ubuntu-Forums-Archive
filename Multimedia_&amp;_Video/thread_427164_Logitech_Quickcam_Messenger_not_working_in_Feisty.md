---
title: "Logitech Quickcam Messenger not working in Feisty"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by huckey on 2007-04-29
Hi,
   I have Logitech Quickam Messenger webcam (here is a picture of how it looks: [http://www.logitech.com/lang/images/0/961.gif]("http://www.logitech.com/lang/images/0/961.gif"))

   I can not make it to work with my Feisty. I have tried various tips found in this forum but to no avail.

   Here is my lsusb:
```
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08f6 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 05e3:070e Genesys Logic, Inc. 
Bus 001 Device 005: ID 1058:0901 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 04b8:0122 Seiko Epson Corp. 
Bus 001 Device 001: ID 0000:0000  

```

   I noticed that a difference in my lsusb listing compared to all other listings I could find in the forum is that there is no name of the webcam after "Logitech, Inc.". This makes me wonder that I must be missing something in the system.

   I think I have V4L installed properly (I am a newbie to Linux). I try to capture picture from my webcam with Camorama but get: "Could not connect to video devide (/dev/video0). Please check connection".

  Can you help me with getting my webcam to work on Feisty?

  Thanks!

Huckey

---

### Post by huckey on 2007-04-29
Hi,
   just for anyone who happened to read this thread. In my case it worked with this driver (and it did not with any other i tried): [URL="http://kanotix.com/debian/pool/main/q/qc-usb-messenger/qc-usb-messenger-source_1.1-2_all.deb"]http://kanotix.com/debian/pool/main/q/qc-usb-messenger/qc-usb-messenger-source_1.1-2_all.deb.
[/URL]
Huckey

---

