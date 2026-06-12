---
title: "Creative WebCam Pro PD1030"
date: 2009-03-31
forum: Multimedia Software
---

### Post by adayforgotten on 2009-03-31
I am running Ubuntu 8.10 x86

Creative WebCam Pro is plugged in but does not work.

I ran lsusb:
danny@dan-s:~/webcam/modules/ov51x-jpeg$ lsusb
Bus 002 Device 004: ID 03f0:2b17 Hewlett-Packard LaserJet 1020
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam
Bus 001 Device 006: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 005: ID 03f0:020c Hewlett-Packard Multimedia Keyboard
Bus 001 Device 003: ID 03f0:010c Hewlett-Packard Multimedia Keyboard Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So it is recognized as OmniVision Technologies, Inc. OV511+ WebCam

All attempts to compile, install or anything to do with OV511 have failed.  I'm a bit new at this so I don't think I could well document what I've tried so far.

This line comes up when I run lsmod:
Module                  Size  Used by
ov511                  83616  0 

Which suggests that the module is working, but it lists nothing under 'used by'

Cheese says no webcam, as does skype (which is what I want to use it for)

Any help would be greatly appreciated.

This webpage claims it is compatible with OV511, but the link to the OV511 info seems broken... [http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html)

---

