---
title: "Help needed installing Hauppage DEC 3000-s on Edgy"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by gh0st on 2007-02-25
I'm trying to use my Hauppage DEC 3000-s with Edgy and I don't seem to be getting anywhere. It's a dvb-s external usb box and I have searched like mad and tried all kinds of things to get it working, so I've finally given up and decided to ask.

I spent ages looking around on [www.linuxtv.org](www.linuxtv.org) and according to that my box is supported and the drivers should already be in my kernel - 2.6.17-11

According to the site the driver needed is a module called ttusb_dec which I have managed to locate using the "lsmod". According to the guide on the site if the module is listed and running then everything should be fine and I should have a folder /dev/dvb/adapter0/ but I don't have a /dvb/ folder in my /dev/ directory.

I tried doing "modprobe ttusb_dec" but it doesn't make any difference, it seems to perform the command fine and there is no error message. Here is the relevant output from my "lsmod" command:

```

Module                  Size  Used by
ttusb_dec              23820  0 
dvb_core               83368  1 ttusb_dec
ttusbdecfe              5504  1 ttusb_dec

```

I know the device is being detected from the following output:

```
dan@frank:~$ lsusb
Bus 002 Device 003: ID 0b48:1006 TechnoTrend AG Technotrend/Hauppauge DEC3000-s
```

I just can't seem to get the device to connect to ttusb_dec, as you can see from the above it says "used by 0" and I assume this should read "used by 1" if it was working. 

What can I do to fix this or at least get some useful diagnostic information? I need help with this I'm a bit out of my depth here. Has anyone used this device with Ubuntu and if so how did you set it up?

Any advice you could give me would be very useful. Thanks in advance :) 

Dan

---

### Post by gh0st on 2007-03-18
Bump!! Anyone got anything at all? :)

---

