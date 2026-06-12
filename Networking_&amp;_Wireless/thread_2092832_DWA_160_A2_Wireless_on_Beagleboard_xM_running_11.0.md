---
title: "DWA 160 A2 Wireless on Beagleboard xM running 11.04"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by NZNobody on 2012-12-09
Hey,
I am trying to get a D-Link DWA 160 Dual Band USB adapter to function on Ubuntu 11.04. I have spent the most part of a day trying many things and am stuck. The module is labeled as H/W Ver.:A2 and F/W Ver.: 1.80 for those interested. When I plug it into the beagleboard and use dmesg i get this (truncated):
```
[  827.154541] usb 1-2.2: new high-speed USB device number 5 using ehci-omap
[  827.325225] usb 1-2.2: New USB device found, idVendor=07d1, idProduct=3a09
[  827.325256] usb 1-2.2: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[  827.325286] usb 1-2.2: Product: 11n adapter
[  827.325469] usb 1-2.2: Manufacturer: ATHER
[  827.325500] usb 1-2.2: SerialNumber: 12345
[  827.427856] usb 1-2.2: reset high-speed USB device number 5 using ehci-omap
[  827.658660] usb 1-2.2: driver   API: 1.9.4 2011-08-15 [1-1]
[  827.658721] usb 1-2.2: firmware API: 1.9.2 2010-12-25
[  827.658752] usb 1-2.2: failed to find compatible firmware descriptor.
[  827.674896] usb 1-2.2: failed to parse firmware (-61).

```
Sometimes this also shows up from dmesg:
```
[ 4522.469451] usbcore: registered new interface driver carl9170

```
And lsmod gives:
```
root@omap:~# lsmod
Module                  Size  Used by
carl9170               69205  0
mac80211              272196  1 carl9170
ath                    15784  1 carl9170
cfg80211              169679  3 carl9170,mac80211,ath

```
I have done sudo apt-get install linux-firmware, i have downloaded and copied to lib/firmware the firmware file found here: [Carl 9170Driver Homepage]("http://linuxwireless.org/en/users/Drivers/carl9170")
I have then rebooted and still get not solution. I am not able to install the compat-wireless drivers (version 3.6.8-1) because when I run the make file i get the following error: ```
root@omap:/usr/src/compat# sudo make
/bin/sh: ./compat/scripts/gen-compat-config.sh: Permission denied
make: *** [/usr/src/compat/.compat_autoconf_compat-wireless-v3.6.8-1] Error 126

```
The file in question is not there and I cannot find what to do about it. Desperately need help as I am completely at a loss now.
Thanks in advance

---

### Post by NZNobody on 2012-12-09
Possibly fixed thanks to support from IRC channel #linux-wireless. Appears I had a few things not configured correctly and somehow the older firmware even though at some point I thought i updated it to 1.9.6.

---

### Post by chili555 on 2012-12-09
> I have done sudo apt-get install linux-firmware, i have downloaded and copied to lib/firmware the firmware file found here: Carl 9170Driver Homepage
I have then rebooted and still get not solution.Meaning that you still get a firmware error? Which firmware version did you download? What does this tell us?```
ls -al /lib/firmware/carl*
```> I am not able to install the compat-wireless drivers (version 3.6.8-1) I doubt that the 3.6.8 version will ever compile on your 3.0-xx kernel. Did you do the driver-select step outlined in the README? Do you have linux-headers and build-essential installed? Moreover, I don't believe the compat-wireless package includes firmware for good old Carl, probably for proprietary reasons.

Finally, there is no reason to use sudo if you are already running as root:> [COLOR="Red"]root[/COLOR]@omap:/usr/src/compat# sudo make

---

### Post by NZNobody on 2012-12-11
Thankyou chili555,
Yes after talking to the helpful people in the IRC channel I have now managed to resolve the issue. I had the wrong firmware version in my lib/firmware for my kernel, which is strange because I could have sworn I downloaded it and changed it but I must not have. As for using sudo as root, I know, habit. Normally I am not logged in as root :)

---

