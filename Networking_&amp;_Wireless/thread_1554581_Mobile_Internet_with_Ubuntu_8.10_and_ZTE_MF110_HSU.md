---
title: "Mobile Internet with Ubuntu 8.10 and ZTE MF110 HSUPA"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by lebiathan on 2010-08-16
Hello everyone,

I recently purchased a mobile internet connection and I was given a ZTE MF110 HSUPA USB dongle. I'm using Ubuntu 8.10.

I've read several articles giving instructions on how to set up and use (successfully I might add) this particular USB key, however, it seems I can't get past a preliminary stage:

I plug in the USB key but nothing happens, i.e. no new icon is displayed that would show the USB to have been recognized. I've tested it on all 3 USB ports that my laptop has, with no success.

Doing an lsusb after plugging the USB, gives the following result

```

lebiathan@lebi-laptop:~$ sudo lsusb 
[sudo] password for lebiathan: 
Bus 005 Device 007: ID 19d2:2000  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

So, the dongle is not listed. Doing an dmesg, I get the following:

```

[ 4863.272147] usb 5-1: new high speed USB device using ehci_hcd and address 9
[ 4863.407807] usb 5-1: configuration #1 chosen from 1 choice
[ 4863.410667] usb-storage: device ignored

```

Finally, doing an 

```

ls /dev/tty*

```

does not list any USB* ports.

The USB itself works fine under Windows XP, but that is a desktop pc, so I guess it is not a hardware problem. The USB ports of the laptop also work fine, as USB storage sticks are recognized and mounted automatically without a problem.

Has anyone experienced this before? Is it possible to provide some insight as to what to do? Upgrading to a later version to get the USB to work is the last thing I'd like to do.

Thanks,
George

----------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------

Update on Aug. 17:

I just noticed that in the lsusb output I gave in the beginning

```

lebiathan@lebi-laptop:~$ sudo lsusb 
[sudo] password for lebiathan: 
Bus 005 Device 007: ID 19d2:2000  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

the stick seems to be present

```

Bus 005 Device 007: ID 19d2:2000

```

However, that was after installing [modemswitch]("http://www.draisberghof.de/usb_modeswitch/"), but I wasn't paying attention enough to see that it was somewhat recognized. I'm redoing the process now, hope it works.

---

