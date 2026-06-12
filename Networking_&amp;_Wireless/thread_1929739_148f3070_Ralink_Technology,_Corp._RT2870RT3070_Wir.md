---
title: "148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter: Missing firmware"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by faibistes on 2012-02-22
These are the last lines of [FONT="Courier New"]dmesg[/FONT]:

```
[507733.142313] ieee80211 phy4: Selected rate control algorithm 'minstrel_ht'
[507733.144904] Registered led device: rt2800usb-phy4::radio
[507733.144953] Registered led device: rt2800usb-phy4::assoc
[507733.144999] Registered led device: rt2800usb-phy4::quality
[507733.145289] usbcore: registered new interface driver rt2800usb
[507794.144122] phy4 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
[507794.163066] udevd[14411]: renamed network interface wlan0 to wlan1
[507876.064135] phy4 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
```

The NetworkManager applet menu says about the device, in spanish, something like "missing firmware" (sorry, I don't know what could be the message in english), and it's grayed out.
```
iwlist wlan1 scanning
wlan1     Failed to read scan data : Network is down
```

I installed, with force-overwrite, this package: [FONT="Courier New"]firmware-realtek_0.35_all.deb[/FONT]. Maybe it wasn't a good idea. Sometimes, when I leave it overnight, I find that it magically has loaded the driver and it's connected to the AP. Sometimes it doesn't, and rebooting is a PITA because it's headless, attached to a projector, with difficult physical access and I need to go through some manual steps so it can boot properly.
BTW, 
```
lsmod | grep rt
rt2800usb              22222  0 
rt2800lib              48909  1 rt2800usb
rt2x00usb              20092  1 rt2800usb
rt2x00lib              48114  3 rt2800usb,rt2800lib,rt2x00usb
parport_pc             32114  0 
crc_ccitt              12595  1 rt2800lib
mac80211              393459  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
parport                40930  3 parport_pc,ppdev,lp
```

Any ideas?

---

### Post by chili555 on 2012-02-22
Please check:```
modinfo rt2800usb
```> $ modinfo rt2800usb
filename:       /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
[COLOR="Red"]firmware:       rt2870.bin[/COLOR]
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     D2D2B027FF946B30926F11F
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
<snip>Your driver wants to find rt2870.bin in /lib/firmware. Please check:```
ls -al /lib/firmware | grep 2870
```It ought to report:> -rw-r--r--  1 root root    8192 2011-08-23 09:23 rt2870.bin
lrwxrwxrwx  1 root root      10 2011-10-18 11:21 rt3070.bin -> rt2870.binIs it present in the right palce? Owned by root? Readable?

---

### Post by faibistes on 2012-02-23
Does this look good?
```
modinfo rt2800usb
filename:       /lib/modules/3.0.0-13-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     61CFBA7ACB6A210B48AA6CB
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*

```
```

ls -al /lib/firmware | grep 2870
-rw-r--r--  1 root root    8192 2011-08-23 15:23 rt2870.bin
lrwxrwxrwx  1 root root      10 2011-08-23 15:23 rt3070.bin -> rt2870.bin
```

---

### Post by chili555 on 2012-02-23
> Does this look good?It looks *too* good. It looks entirely normal. Everything is perfect except it simply doesn't work. Let's try a later firmware version. Please download the attached to your desktop. Right-click it and select *Extract Here*. Now let's back up the original:```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.bak
```Now we copy the newer file to /lib/firmware:```
sudo cp Desktop/RT2870_Firmware_V22/rt2870.bin /lib/firmware
```Now reboot and let us see again:```
dmesg | grep rt2
sudo iwlist wlan0 scan
```Fingers crossed...

---

### Post by faibistes on 2012-02-23
This is weird. The mere fact of copying a rt2870.bin to /lib/firmware (the file you are attaching or any other valid firmware) solves the problem. As a workaround, I'm happy with it. If I have to reboot, or rmmod, or detach de USB dongle, it doesn't work anymore... until I copy the file again. Any thoughts?

---

### Post by chili555 on 2012-02-23
> Any thoughts?Yes. That's wierd!!!!

I wonder if it's actually the driver that's not grabbing the firmwrae correctly. Instead of copying the firmware, try this and report back. If it works, we can automate it:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb
```Does it spring to life?

---

### Post by faibistes on 2012-02-23
No, as I said, if I rmmod+modprobe, it doesn't work anymore... until I overwrite the file again. with the module loaded.

---

### Post by chili555 on 2012-02-23
> **faibistes said:**
> No, as I said, if I rmmod+modprobe, it doesn't work anymore... until I overwrite the file again. with the module loaded.Please reboot with the device inserted and see what this tells us:```
dmesg | grep rt2
```We can force it in rc.local if all else fails.

---

### Post by Her Tigger on 2012-03-09
I don't know if it  would help but can we force remove the previously installed driver and  replace it w this new one and somehow force the system 2 not update it  or roll it back to the previous driver and if so how? I started a thread heres the link [http://ubuntuforums.org/showthread.php?p=11752104#post11752104](http://ubuntuforums.org/showthread.php?p=11752104#post11752104)

---

### Post by Her Tigger on 2012-03-09
> **chili555 said:**
> Please reboot with the device inserted and see what this tells us:```
dmesg | grep rt2
```We can force it in rc.local if all else fails.


how do we force it? sorry i'm new 2 ubuntu and i love it already and would love 2 learn more about everything. any pointers would be great, ty sooo much guys and gals yall r doing a great job!

---

### Post by chili555 on 2012-03-09
> **Her Tigger said:**
> how do we force it? sorry i'm new 2 ubuntu and i love it already and would love 2 learn more about everything. any pointers would be great, ty sooo much guys and gals yall r doing a great job!Please see and stay on your other thread.

---

