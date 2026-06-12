---
title: "Loud Beep on speakers when rebooting/shutdown"
date: 2012-10-26
forum: Multimedia Software
---

### Post by jaweinre on 2012-10-26
After upgrading to 12.10, i'm getting a loud beep when shutting  down or restarting my HP 2560p laptop. Sound comes through speakers and/or headphones. This happens on unity and gnome DE.

hwinfo --sound shows the following:

```
12: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  Unique ID: u1Nb.kZ5ZvXzaJL4
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel Audio device"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1c20 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x162b 
  Revision: 0x04
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xd4700000-0xd4703fff (rw,non-prefetchable)
  IRQ: 47 (918 events)
  Module Alias: "pci:v00008086d00001C20sv0000103Csd0000162Bbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

Already tried every solution found here to no avail:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331589](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331589)

Which include disabling sound notification on "sound" config, blacklisting pcspkr, going to alsamixer and lowering "Beep" to 0, etc etc..

Audio is working 100% btw, although this Model: "Intel Audio device" is suspiciuous.. maybe my system is not fully recognizing my onboard audio?

Also, i can't set any notification sound on the "sound" configuration panel, they're all greyed out, even when i enable it.

---

### Post by jaweinre on 2012-10-26
Problem solved. After trying the above, and also reinstalling the whole audio framework, and using alsamixer on console, i came across the **gnome-alsamixer** package.  Using this software i was able to find a "Beep" entry which i disabled, muted, and lowered volume to 0, three times just to make sure. Problem got solved.

So, for anyone having similar issues, use **GNOME-ALSAMIXER**.

---

