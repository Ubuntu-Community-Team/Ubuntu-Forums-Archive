---
title: "Intel PC Camera Pro (webcam) worked on 8.04 but NOT on 9.04 - Please Help"
date: 2009-05-29
forum: Multimedia Software
---

### Post by LucaBri on 2009-05-29
Hello,
   I have an old Intel PC Camera pro (Create and Share) Webcam that used to work flawlessly with 8.04 (Hardy Heron) but is **not** working with 9.04 (Jaunty Jackalope).
I recently updated to 9.04 (vis 8.10 but I did not test the camera under Intrepid) and now the system (Skype, Cheese, Xsane for instance) recognize it but I only get colorful statics.

I tried to install EasyCam2 but the system (both via the terminal and synaptic) is telling me that python2.4-gtk2 and python2.4-something-or-other are needed but they WON'T be installed (just like this....).

This is my lsusb:

Bus 001 Device 006: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 074d:3556 Micronas GmbH Composite USB-Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:2d11 Hewlett-Packard OfficeJet 6110
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 0733:0430 ViewQuest Technologies, Inc. Intel Pro Share WebCam**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Skype and Cheese call it:

USB Camera (0733:0430) (/dev/video0)


I think that if I could roll back the driver to 8.04 I should be set, but I have no idea on how to do it.

Please keep in mind that I am a total Linux newbie, coming from W....XP


Thank you in advance

Luca

---

### Post by LucaBri on 2009-05-29
Hello Again,
     Some more pieces to the puzzle.

I borrowed a newer logitech USB webcam from my wife's computer (she does not know it yet...)

The camera gives me a great picture with Cheese but still a bunch of statics in Skype, which baffles me a little. Could it be that I have **two** problems? One with my old webcam (Intel PC Camera Pro) and one with Skype itself?
I don't mind buying another webcam, if it comes to that, as they are relatively inexpensive but I want to be able to use it with Skype.

Here is lsusb (with both devices plugged in):

Bus 001 Device 006: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 005 Device 002: ID 046d:089d Logitech, Inc. **
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:2d11 Hewlett-Packard OfficeJet 6110
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 0733:0430 ViewQuest Technologies, Inc. Intel Pro Share WebCam**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Interestingly, the Logitech webcam has an LED that turns on in Windows (when used with Skype) but not in Ubuntu.

As I mentioned in my previous post, the old Intel Webcam worked fine under 8.04.

Again, any help is greatly appreciated.
I have dual boot but it would be a drag if I had to boot in Windows only to be able to use Skype.


Thanks


Luca

---

### Post by LucaBri on 2009-06-01
Ok,
   I "solved" my problem by giving up on my Intell PC Webcam and buying a Dynex 1.3 Mpixel webcam.
It was the cheapest at Best Buy (relatively speaking) and had a green checkmark in the list from here: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

It works well with Skype.

So, I did not really solve my problem (just bypassed it) and I am still curious on why the Intel PC Camera works with 8.04 but not with 9.04....

Luca

---

### Post by factorgaming on 2009-06-12
hai! this is realy good i have similar problem this website really help me sort off my problem thanking you.

---

