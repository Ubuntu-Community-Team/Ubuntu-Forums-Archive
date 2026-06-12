---
title: "MCE Remote worked after I edited hardware.conf"
date: 2007-10-25
forum: Mythbuntu
---

### Post by [Psyduck] on 2007-10-25
Hi!

Thanks for a GREAT product. Installed Mythbuntu yesterday and except for some small glitches everything worked like a dream. :KS

One of the problems I encountered were that my MCE Remote (New model) didn't work. In my case I had to change /etc/lirc/hardware.conf to use /dev/lirc1in order to get the remote to work.
I guess the /dev/lirc0 is used for my Soundblaster X-Fi Remote (which I don't use).


It would be nice if the installer (or the ControlCenter) let the user select which remote to use.

---

### Post by axelsvag on 2007-10-25
I have the same problem  Where in the etc/lirc/hardware.conf did you change?

---

### Post by superm1 on 2007-10-25
I'm interested a little bit about this SB xi-fi remote coming up as lirc0.  Do you by chance know what driver it uses?

You can checkout '**dmesg | grep lirc**' to determine.


As for what lie to modify, modify

[B]DEVICE=""
[/B]

---

### Post by [Psyduck] on 2007-10-26
**superm1:** 
I will check this tonight when I get home.

**axelsvag:**
I edited the line 
*DEVICE=""*
to 
*DEVICE="/dev/lirc1"*
saved
and restarted lirc.

---

### Post by [Psyduck] on 2007-10-27
Here's the dmesg output

```

[   36.304517] lirc_dev: IR Remote Control driver registered, at major 61
[   36.306488] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[   36.306492] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   36.306753] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   36.306758] lirc_dev: lirc_register_plugin: sample_rate: 0
[   36.306884] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0)
[   36.307007] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<1:4> initialized
[   36.307022] usbcore: registered new interface driver lirc_imon
[   36.321673] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   36.321676] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   36.610742] lirc_dev: lirc_register_plugin: sample_rate: 0
[   36.614526] lirc_mceusb2[3]: Philips eHome Infrared Transceiver on usb4:3
[   36.614557] usbcore: registered new interface driver lirc_mceusb2

```

It is either my Soundblaster X-Fi or perhaps the VFD/Volume Knob in my Antec Fusion case?

---

### Post by axelsvag on 2007-10-27
I have the same problem sometimes it works somtimes not . Here is my 

```
[   29.758190] lirc_dev: IR Remote Control driver registered, at major 61 
[   30.069889] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver for Soundgraph iMON MultiMedian IR/VFD, v0.3
[   30.069895] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky Raju <dev@venky.ws>
[   30.070662] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: found IMON device
[   30.070668] lirc_dev: lirc_register_plugin: sample_rate: 0
[   30.070707] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: Registered iMON plugin (minor:0)
[   30.070757] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_probe: iMON device on usb<5:2> initialized
[   30.070772] usbcore: registered new interface driver lirc_imon
[   30.079218] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.33 $
[   30.079222] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   30.460985] lirc_dev: lirc_register_plugin: sample_rate: 0
[   30.464802] lirc_mceusb2[3]: SMK eHome Infrared Transceiver on usb2:3
[   30.464842] usbcore: registered new interface driver lirc_mceusb2
[   73.005567] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened
[   91.124512] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port closed
[  208.923258] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: IR port opened

```

---

### Post by superm1 on 2007-10-28
Ah i see.  Well an alternative solution will be to blacklist lirc_imon if you don't need it.

---

### Post by axelsvag on 2007-10-28
Am I right if I assume that the soundgraph have someting to do with the ANTEC FUSION. If I have understood my hardware  in the case  right it has one vfd/lcd and one ir receiver. Is it these that fool the lirc settings?

---

