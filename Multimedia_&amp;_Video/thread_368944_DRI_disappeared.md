---
title: "DRI disappeared"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by akshaysrinivasan on 2007-02-23
I am having a Integrated Unichrome Graphics on the VIA KM 400 
Northbridge chipset.It is having DRI support from Edgy onwards.
I was meddling around with the drivers ,on my Motherboard CD ROM ,and now i can't get DRI back?Can someone please help?I don't fancy installing it again.I have attached my xorg.conf.
Also ,glxinfo says ...

neptune@neptune:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

And xdri info...

neptune@neptune:~$ xdriinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Screen 0: not direct rendering capable.


Thanking you in advance....

---

