---
title: "ENUTV-2 ENCORE TV TUNER Doesn't appear in LSUSB"
date: 2008-12-22
forum: Multimedia Software
---

### Post by miltonlaufer on 2008-12-22
Hello. I just got an ENUTV-2 USB tv tuner and, altough it works perfect in Windows, I can't get even to "see it" in Ubuntu.

First of all, the main chip of this box is an TVMASTER TRIDENT TM5600 Chip (which is said to be compatible with the drivers of TM6000 and TM6010).

When I do 

```
lsusb
```

it looks the same than before plugging the device.

But when doing a dmesg, i get this:
```

[ 1427.116389][ 2149.329060] usb 3-2: new full speed USB device using ohci_hcd and address 2
[ 2149.580140] usb 3-2: no configurations
[ 2149.580160] usb 3-2: can't read configurations, error -22
[ 2149.720077] usb 3-2: new full speed USB device using ohci_hcd and address 3
[ 2149.967167] usb 3-2: no configurations
[ 2149.967188] usb 3-2: can't read configurations, error -22
[ 2150.104055] usb 3-2: new full speed USB device using ohci_hcd and address 4
[ 2150.187139] usb 3-2: device descriptor read/8, error -32
[ 2150.310163] usb 3-2: device descriptor read/8, error -32
[ 2150.549053] usb 3-2: new full speed USB device using ohci_hcd and address 5
[ 2150.620138] usb 3-2: device descriptor read/8, error -32
[ 2150.745145] usb 3-2: device descriptor read/8, error -32
[ 2150.848082] hub 3-0:1.0: unable to enumerate USB device on port 2


```.





I've tried everything. I have installed a lot of drivers for the TM6000. (Apparently, the newer is this, for the DVB project: [http://linuxtv.org/hg/~mchehab/tm6010]("http://linuxtv.org/hg/~mchehab/tm6010") )


The only thing of which I'm not sure is the following: in a lot of places everyone says that you have to get the "tridvid.sys" in order to get some files that you got to put in the "/bin/firmware" folder. But that ".sys" file isn't in my CD of the device, so I copied it from the windows directory in which the device works. MAYBE if I could get the right tridvid.sys, then I will be able to get the device recognized, but I'm not really sure.


Well, thanks to all.

---

### Post by miltonlaufer on 2008-12-23
If I could at least get the device recognized by LSUSB, then maybe I will be able to use the VirtualBox to run it over Windows XP.

---

