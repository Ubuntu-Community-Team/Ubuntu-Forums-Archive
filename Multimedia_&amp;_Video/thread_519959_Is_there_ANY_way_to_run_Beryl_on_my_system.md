---
title: "Is there ANY way to run Beryl on my system?"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by shadow1515 on 2007-08-07
I'm trying to get beryl running on Feisty and am beginning to despair.  I have a Radeon x1600 Pro PCIe card, which seems to be my problem. As I've seen people say all over, the flgrx (or some transposition of those letters...) driver is utter crap.  When I install it, I can never even get Ubuntu to boot again without getting rid of the driver first.  Even if I try going with no driver and editing my xserver to enable a higher resolution, it causes a system crash on reboot.  Am I just destined to not ever run 3D acceleration until I buy a different video card (no time soon - it runs all my games just fine in Windows) or are there some drivers out there that will actually work?

---

### Post by shadow1515 on 2007-08-07
I just thought of something that might work, but I don't know how to go about it so I still need help.  My mobo has an integrated GeForce 6150 LE Nvidia graphics processor.  If I just plugged a VGA cable into that could I get Ubuntu to use that card and Windows to use my other one?  Would the regular Nvidia drivers work and support 3D acceleration for that?  My biggest concern is how to get two different OSes to use two different video cards on the same computer.  How do I go about that?

---

### Post by backflop on 2007-08-07
If you are using a desktop based on aiglx (which is the standard rendering platform for feisty fawn) then the fglrx driver will not work. To get around this you can install the xgl platform by using[ this guide.]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#Install_Beryl_using_proprietary_FGLRX_drivers_from_ATI") It was what worked for me when i was using an ATI card.

---

### Post by dougfractal on 2007-08-07
It can be done

this may help, but if it don't read the whole thread.
from 
[http://rage3d.com/board/showthread.php?p=1334381957](http://rage3d.com/board/showthread.php?p=1334381957)
> aticonfig --initial -f
aticonfig --resolution=0,1280x1024

---

