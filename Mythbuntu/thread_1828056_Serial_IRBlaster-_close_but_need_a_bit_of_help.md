---
title: "Serial IRBlaster- close but need a bit of help"
date: 2011-08-18
forum: Mythbuntu
---

### Post by pilesofspam on 2011-08-18
After a few years of successful mything, I had a slow HD crash, meaning bits of data started going missing.  I managed to back up the important stuff, got a new HD, and fresh installed 11.04.  Everything went very smoothly with the exception of the serial port homebrew IR blaster.  It's giving me the dreaded 'Hardware Does Not support sending' error.

I have an HD-PVR, a streamzap Remote, and a PC 5500 OTA card, and a homebrew IR blaster on a serial port.

My /etc/lirc/hardware.conf is correctly calling out the streamzap (as /dev/lirc0).  It is calling the serial blaster /dev/lirc1 (which would make it addressable by lircd1) but I THINK the PC5500 card (which has an ir receiver I don't use) is registered as lirc1.

If I run dmesg | grep lirc I get this:
```
[   12.616397] lirc_dev: IR Remote Control driver registered, major 249 
[   12.706543] rc rc0: lirc_dev: driver ir-lirc-codec (streamzap) registered at minor = 0
[   13.558003] rc rc1: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 1
[   15.068038] lirc_serial: auto-detected active high receiver
[   15.068165] lirc_serial lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 2
```

but if I look at ls /dev/lirc* I only see:
```
/dev/lirc0  /dev/lirc1  /dev/lirc2  /dev/lircd  /dev/lircd1
```

Anybody have any help to offer on this one?  Actually, a way to disable the ir receiver on the pc5500 would be good enough.  I tried to assign the serial blaster in hardware.conf to use /dev/lirc2 but it didn't work- there's no lircd2 created.  I don't know what creates /dev/lircd2.

---

### Post by pilesofspam on 2011-08-18
Looks like this (as root) will create the device I need.  It also needs to be referenced correctly (as lirc2) in your hardware.conf:

```
/usr/sbin/lircd --driver=default --device=/dev/lirc2 --output=/dev/lircd2 --pidfile=/var/run/lircd2.pid --listen=8766 /etc/lirc/lircd.conf
```
Now the streamzap works fine, the serial blaster works fine, and the PC5500's ir receiver sits idly in between.  I might drop it at the end of /etc/init.d/lirc or maybe /etc/init.d/rc.local

---

