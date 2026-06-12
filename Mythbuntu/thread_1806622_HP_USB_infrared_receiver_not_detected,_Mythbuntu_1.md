---
title: "HP USB infrared receiver not detected, Mythbuntu 10.04"
date: 2011-07-17
forum: Mythbuntu
---

### Post by stlouisubntu on 2011-07-17
Purchased an HP USB infrared receiver to go with the mceusb2 remote transmitter that came with my HVR-2250 kit but it is not showing up in lsusb.

I am running a FE/BE dedicated machine with a dual core AMD Athlon II 2.5 Ghz CPU, Nvidia 6200 chipset, dedicated Nvidia GT220 HDMI 1 GB graphics card, 2GB RAM, Dual SATA HD, 1 160 GB, 1 TB drive, smaller drive for OS, database, and video storage partition and the larger drive solely for video storage.  The tuner card is a Hauppage HVR-2250 (dual HD/ATSC tuner.)  This box runs Mythbuntu 10.04 (32-bit) with 0.24-fixes all updated.

This usb receiver is supposed to work OOTB evidenced by others experiences as reported in various mythtv forum posts.

After plugging in this device, sudo tail -f /var/log/messages indicates

```
Jul 17 20:49:42 mythtvbox kernel: [14941.236047] usb 2-2: new full speed USB device using ohci_hcd and address 4
Jul 17 20:49:42 mythtvbox kernel: [14941.460629] usb 2-2: configuration #1 chosen from 1 choice
```

but again lsusb indicates nothing and the device does not work (irw shows nothing when pressing buttons but red light does flash.)

When plugging it into my main Ubuntu 10.04 box upstairs box lsusb shows 

```
Bus 002 Device 002: ID 0cf2:6230 ENE Technology, Inc. 
```

So, it seems to me that this must be some kind of usb and/or udev problem but I really need some assistance here.  Other usb devices work correctly on this box (wireless usb keyboard/mouse combo works fine, usb webcam works fine.)  Also, I did remove all other usb devices and boot with only this usb infrared to see if that would make a difference and it did not.)

I also tried sudo dpkg-reconfigure udev, but that did not help either. 

Any assistance and/or advice would be much appreciated.

<UPDATE>

Actually, lsusb does show

```
Bus 002 Device 004: ID 1934:5168
```

but does not show make/model info and the device id is different so I am unable to determine if this is referring to the HP infrared receiver (as seems quite clear on the upstairs main ubuntu box.)

---

### Post by stlouisubntu on 2011-07-18
Okay, friends.

The answer is found here:

[http://forum.xbmc.org/archive/index.php/t-66527.html](http://forum.xbmc.org/archive/index.php/t-66527.html)

I used their step by step to add this device to the infrared receivers.

The correct device was as detected by lsusb in the mythtvbox (I still have no idea why it was detected so different in my other ubuntu box.)

Bus 002 Device 004: ID 1934:5168

I hope that this helps someone else someday.  (However, at this point I think I could hear a pin drop.)

Kind Regards,

stlouisubntu

---

### Post by stlouisubntu on 2011-07-19
Issue hereby solved and attempted to forward upstream so that this device will work OOTB for others.


Bug Report:

[https://bugs.launchpad.net/lirc/+bug/813273](https://bugs.launchpad.net/lirc/+bug/813273)

---

