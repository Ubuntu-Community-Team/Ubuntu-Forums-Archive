---
title: "3d with KM400/VT8378"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Episcopus on 2007-04-24
My xorg.conf file says that my graphics card is using the vesa driver.  With this driver, glxgears gives me about 200fps.  I tried switching to the via driver by altering the xorg.conf file to say > 
Section "Device"
Identifier  "Generic Graphics Card"
Driver        "via"
Option       "DisableIRQ"
Option       "EnableAGPDMA"
BusID         "PCI:1:0:0"
EndSection

I did that because that was the answer I found here in the forums for other people trying to get 3d working right with their Via chipsets.  After doing that, I restarted X and now whenever I run glxgears, the screen opens but stays black and my computer freezes.  I have to do a hard shutdown to make it work again.  It also freezes when I do glxinfo.

Can someone please help me make 3d run correctly?

EDIT:  I read the Xorg.0.log and it said that the chipset does not support XvMC.  The packaged Via driver says that it does, though.  Is there a way to fix this?  I tried attaching the Xorg.0.log, but it is 24kb and we are only allowed 19.5, and I didn't know what to cut and what to leave.

---

### Post by khowe on 2007-09-16
You can try irqpoll boot option.

this can be added to /boot/grub/menu.lst

add it after the quiet splash.


I have had the most sucess with ubuntu 6.10 edgy.

feisty and gutsy have caused lock-up, freeze for me when ever I run a 3d app.

I have an averatec 3715 laptop.

---

### Post by khowe on 2007-09-16
I found this in a bug report @ [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154")

I'm not sure if I got the same problem:
Everything worked fine until Feisty.
My card is a KM400 and since Feisty I get complete freezes (but the mouse cursor is still moveable) when i run ANY 3d related application. Even a simple glxinfo freezes the system.
I don't find any error messages in the logs and i can start the X-Server with via specified in the xorg.conf but as soon as 3D is required the fun is over.

I solved this problem for me by downgrading libgl1-mesa-glx and libgl1-mesa-dri from 6.5.2-3ubuntu7 (Feisty) to 6.5.1~20060817-0ubuntu3 (Edgy).

My card has never worked by default, even if Ubuntu recognizes it in the installation process (which it does since Edgy, I guess).
Additional options which I have always needed to get it working are:
 Option "VBEModes" "true"
 Option "DisableIRQ"
 Option "EnableAGPDMA"

same info also @ [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/118163]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/118163")

---

