---
title: "Intrepid &amp; NVidia 5500 woes (need some instruction)"
date: 2008-11-08
forum: Multimedia Software
---

### Post by oldsoundguy on 2008-11-08
Upgraded to Intrepid on three computers yesterday,  Problems with my main on line computer in the display. (the other two went smooth as glass!)
Have an NVidia 5500 PCI 256 card in the box and am driving a really nice HP 2465 Cinema display. (no AGP or PCIe slot on the motherboard.)

The thing worked great in Gutsy .. not a problem even using the rotation.

I managed to finally get the restricted 173 drivers installed, but they do not work on that screen, so right now it is plugged into my 15" test bench screen .. that works.

really zip in the way of help on the forums except I got this:
[http://packages.ubuntu.com/intrepid/nvidia-glx-173](http://packages.ubuntu.com/intrepid/nvidia-glx-173)
(turs out this is the same driver I have already installed .. so much for that!)

I have NEVER written a kernel and don't have the slightest clue as to where to begin.  Think this may solve the problem as I need more options for resolution and I need the RandRotate to be able to function. (so it appears that I will not have to write anything at present!) 

The darn install of 173 (177 was a total bust!) gave me a really WEIRD xorg file with just a few generic items in it .. so that may have to be worked on also.

Thanks in advance and will be watching (am able to get here on the box, so not an issue there!)

Does anybody on the inside have an idea as to when this issue may be corrected?

---

### Post by oldsoundguy on 2008-11-09
Gonna bump this and re say it.
I need help with an NVida FX5500 driver issue in Intrepid.
I have it working on a standard LCD just fine.
The issue is that the driver is not sufficient to drive a wide aspect ratio monitor (the screen splits, flickers and nothing can be launched).
AND I HAVE to be able to rotate the screen .. the LCD it is on now has that capability, but the driver says NO to rotate.
To point out, I had the card/monitor working in Gutsy and it worked for a short time that I had Hardy on the box when I was upgrading. (has to be a kernel issue here!)

ANY help will be greatly appreciated.

(or am I going to have to wait on NVidia to do something?)

---

### Post by pigboy on 2008-11-09
Hi there. Had a similar issue. Resolved it by simply switching my Monitor cable from DVI to VGA. If you are using a DVI cable currently, I would strongly encourage you to attempt this prior to doing any other posted fix, as it is the easiest possible solution.

I was seconds away from reinstalling 8.04 getting my card to work correctly and then using that config file in a fresh install of 8.10 when I decided to swap cables as a last ditch effort, presto it worked!

Hope this helps.

---

### Post by oldsoundguy on 2008-11-09
pigboy, THANKS for the reply!
First, did you use the vga output or the DVI from the card?

Either way, I have the box hooked into a DVI KVM switch with a separate digital audio switch and sharing the keyboard/video/mouse with a windows box, so will have to get a couple of adapters to make it work (if at all).
Will have to check local outlet in the morning to see if they have something I can use. (if not, will shop eBay).  So it will take some time before I have hardware in hand to try this fix.

This IS a software problem that should be addressed by someone .. but not sure just who should pick this up and I do NOT know how nor have I ever tried to file a formal bug report .. and even then, with WHOM??

---

### Post by oldsoundguy on 2008-11-10
A follow-up
Managed to get the screen up and running by using the 96 Legacy driver, but no ROTATION and the xorg.conf file looks weird:

Section "Device"
        Identifier      "Configured Video Device"
        Option          "RandRotation"        "on"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


And that is it in it's entirety!

---

