---
title: "Very Strange ..."
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by CurlyBlue on 2006-09-01
HI All

Am completely new to Linux but it takes me back to the beginning of my 25 year career in IT.

Anyway - something strange just happened!

I am running an Nvidia Quadro 3450FX Card with a Dell WFP3007 30 inch flat panel attached to the PC.

Obviously needed to load up the latest Nvidia drivers to get Linux running at 2550 x 1600 (Resolution I run at in Windows Vista).

So - came to the forums and tried TWO different methods from TWO different threads both of which installed the driver but trashed X server.

So - Logged in as normal - got the xserver "crashed" message and exited  out to terminal.

Then reconfigured the X Server with 

sudo dpkg-reconfigure xserver-xorg

Gave it all the standard settings (as I did when installing the Nvidia drivers before) and ...

The darn thing worked!

I now have my Quadra 3450 running at full tilt with no issues!

Go figure!

Just thought I  would let you know as it seems a lot of people are having issues with Nivida cards and the "fix" might just be to reconfigure xserver from terminal after the xsever "crashed" message.

CurlyBlue
Converted to Linux August 2006!

---

