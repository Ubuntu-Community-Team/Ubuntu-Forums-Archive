---
title: "My USB wifi dongle doesn't work on Ubuntu 8.10 and later!"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by calrogman on 2009-03-29
When I first started using Ubuntu (8.04) on my laptop, the first thing I noticed was that the built in WiFi doesn't work.  This was remedied by buying a USB WiFi dongle.

I bought the LM001 dongle from "LM-Technologies", and on kernels 2.6.x and 2.4.x the drivers are supposed to compile cleanly, however upon upgrading to 8.10 (on the day of release, foolishly without first trying the LiveCD) I found the drivers no longer compile.  The same is true of Debian Lenny.

I have tried to track down newer drivers and/or firmware, however Google returns very little useful information (even when using [Google Linux]("http://www.google.com/linux"))

If anyone else has had a similiar problem and has found a solution can you please post it here?

lsusb shows:
```
Bus 007 Device 002: ID 0ace:1215 ZyDAS WLA-54L WiFi

```

The product page (which only provides Windows drivers) is [here]("http://www.lm-technologies.com/ci/index.php?/products/details/2").

The drivers which came with the dongle, and the user guide are below.

---

### Post by chili555 on 2009-03-29
I wonder if this works with the in-built module, *zd1211rw.* Please do:```
sudo modprobe zd1211rw
```Did your dongle spring to life?

---

### Post by calrogman on 2009-03-29
> **chili555 said:**
> I wonder if this works with the in-built module, *zd1211rw.* Please do:```
sudo modprobe zd1211rw
```Did your dongle spring to life?

Running this from inside a Xubuntu 9.04b virtual machine, with USB passthrough enabled doesn't do anything other than cause "iwlist scan" to hang until interrupted.

I'll try again once I burn to a CD and boot from that directly.

---

### Post by calrogman on 2009-03-29
Ubuntu 9.04 from CD non-virtualised doesn't work either.
Might need to track down some newer firmware.:(

---

### Post by chili555 on 2009-03-29
I believe a newer *zd1211rw* may be in *linux-backports-modules-intrepid-generic*. Can you please install that?

---

### Post by calrogman on 2009-03-30
> **chili555 said:**
> I believe a newer *zd1211rw* may be in *linux-backports-modules-intrepid-generic*. Can you please install that?

That would make more sense if I was running Intrepid instead of 9.04b.
After installing *linux-backports-modules-jaunty-generic* and running ```
modprobe zd1211rw
```
```
ifconfig wlan0 up
``` complains of a timeout error.

Really hope I can get this working, I love 9.04 but if I can't get the wifi working it won't be touching my HDD.

:(

---

### Post by chili555 on 2009-03-30
> complains of a timeout error.Times out trying to get an IP address or what? At least we have signs of life, pulse, breath, etc.

It would help to know more. Are you using Network Manager or manual configuration? Are you certain the interface is *wlan0*? Did you tell it what ESSID you wish to connect to?

---

### Post by calrogman on 2009-04-02
> **chili555 said:**
> Times out trying to get an IP address or what? At least we have signs of life, pulse, breath, etc.

It would help to know more. Are you using Network Manager or manual configuration? Are you certain the interface is *wlan0*? Did you tell it what ESSID you wish to connect to?

When I run
```
ifconfig wlan0 up
```

I get a message stating "SIOCSIFFLAGS: Timeout Error" or something along those lines, and the firmware doesn't load.

I'll check that I've got that error message right as soon as I have a chance.

I am certain the interface is wlan0 and I use manual configuration as I find the network manager to be very buggy.

I didn't get a chance to give it an essid to connect to as the interface won't "go up".

---

### Post by chili555 on 2009-04-02
> I am certain the interface is wlan0One way to be sure is to run:```
iwconfig
```See which interface has all the details.

---

### Post by calrogman on 2009-04-05
> **chili555 said:**
> One way to be sure is to run:```
iwconfig
```See which interface has all the details.

> **calrogman said:**
> the interface is wlan0

*facepalm*

---

### Post by calrogman on 2009-04-11
Desperately
Bumping
My
Thread

---

### Post by kerry_s on 2009-04-11
weird i use a zydas, all i do is install the firmware(zd1211-firmware) then plug in the usb wifi and it just works.
in debian the the firmware is in the non-free repo.
in arch it's just pacman -S zd1211-firmware

so it should be in the repos, make sure there all on and type zd1211 in synaptic.

make sure you don't have it plugged in till after you install the firmware.

---

### Post by calrogman on 2009-04-11
> **kerry_s said:**
> weird i use a zydas, all i do is install the firmware(zd1211-firmware) then plug in the usb wifi and it just works.
in debian the the firmware is in the non-free repo.
in arch it's just pacman -S zd1211-firmware

so it should be in the repos, make sure there all on and type zd1211 in synaptic.

make sure you don't have it plugged in till after you install the firmware.

Presuming you are using 8.10 or 9.04b, I'll have a look for zd1211-firmware in Aptitude(FAR superior to Synaptic).

Edit: It appears that zd1211-firmware is not available in 9.04b yet.

---

### Post by kerry_s on 2009-04-11
if you want you can try the deb.
[http://195.221.21.36/mirrors/ftp.debian.org/pool/non-free/z/zd1211-firmware/?C=S;O=D](http://195.221.21.36/mirrors/ftp.debian.org/pool/non-free/z/zd1211-firmware/?C=S;O=D)

---

### Post by calrogman on 2009-04-12
> **kerry_s said:**
> if you want you can try the deb.
[http://195.221.21.36/mirrors/ftp.debian.org/pool/non-free/z/zd1211-firmware/?C=S;O=D](http://195.221.21.36/mirrors/ftp.debian.org/pool/non-free/z/zd1211-firmware/?C=S;O=D)

```
Reading database ... 103662 files and directoires currently installed.)
Unpacking zd1211-firmware (from .../zd1211-firmware_2.21.0.0-0.1_all.deb) ..
dpkg: error processing /home/callum/Desktop/zd1211-firmware_2.21.0.0-0.1_all.deb (--install):
 trying to overwrite `/lib/firmware/zd1211/zd1211b_uphr', which is also in package linux-firmware
Errors were encountered while processing:
 /home/callum/Desktop/zd1211-firmware_2.21.0.0-0.1_all.deb
```

'linux-firmware' is stopping me from installing correct firmware for my USB dongle?  *facepalm*

Once `'linux-firmware' is purged, it is optional, and zd1211-firmware is installed, running 'ifconfig wlan0 up' produces this output.
```
SIOCSIFFLAGS: Connection timed out
```
I get the same errors with 2.16.0.0-0.1.

---

### Post by kerry_s on 2009-04-13
bummer, maybe you should try debian or arch?
i just got mine back, using it now, see pic.
added wicd to my install.

---

### Post by calrogman on 2009-04-13
Heres what I get from lsusb
```
ID 0ace:1215 ZyDAS WLA-54L WiFi
```

and lsmod shows the following related modules
```

zd1211rw               56964  0
ieee80211softmac       30976  1 zd1211rw
ieee80211              35528  2 zd1211rw,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
cfg80211               15112  1 iwlwifi_mac80211
usbcore               146412  4 zd1211rw,ehci_hcd,uhci_hcd
```

and the kernel suppresses (default Ubuntu style) the following information (dug up using dmesg) when the dongle is plugged in

```
[   59.067039] usb 7-5: reset high speed USB device using ehci_hcd and address 2
[   59.111542] zd1211rw 7-5:1.0: eth1
[   59.111579] usbcore: registered new interface driver zd1211rw
[   59.234251] zd1211rw 7-5:1.0: firmware version 4725
[   59.274206] zd1211rw 7-5:1.0: zd1211b chip 0ace:1215 v4810 high 00-02-72 AL2230_RF pa0 g--NS
[   59.293841] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   59.838500] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   62.527771] NET: Registered protocol family 17
[   63.189580] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   63.352512] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   65.104070] eth1: no IPv6 routers present
[   67.440806] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   69.054028] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   73.643946] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   75.826399] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   81.600556] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   82.035473] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   87.092528] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   90.286831] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26
[   90.413103] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   92.698637] eth1: no IPv6 routers present
[  103.592842] SoftMAC: Open Authentication completed with 00:11:95:96:3d:26

```


Notice the line ```
[   59.274206] zd1211rw 7-5:1.0: zd1211b chip 0ace:1215 v4810 high 00-02-72 AL2230_RF pa0 g--NS
```which shows that my dongle uses the zd1211b firmware.

---

### Post by kerry_s on 2009-04-13
is "LM001" the brand? i don't see that on the supported page:
[http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices)

---

### Post by calrogman on 2009-04-13
> **kerry_s said:**
> is "LM001" the brand? i don't see that on the supported page:
[http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices)


LM-Technologies is the brand.

I bought it because the site I bought it from (Amazon) said that it was compatible, which it is, but apparently only on aging versions of distros. =/.

EDIT: According to lsusb I am using the 0ace:1215 ZyDAS WLA-54L WiFi, which is on the supported device list, it is a repackaged LUTEC.

If you go here and do a Ctrl F for WLA-54L you can find my dongle, only mine has the logo changed.
[http://www.metanewmedia.com/index.php?/produkte-data.htm](http://www.metanewmedia.com/index.php?/produkte-data.htm)

Even the plastic casing is the same shape.

The drivers found there won't compile.

---

### Post by calrogman on 2009-04-13
With the help of the guys at #linux-wireless on irc.frenode.net I have got the wifi working.  I needed to copy /lib/firmware/zd1211 to /lib/firmware/`uname -r`/zd1211 and run "modprobe zd1211rw" before using iwconfig and dhclient to get connected.  Thanks for the help guys!

---

### Post by wodzu12 on 2009-06-25
calrogman, i have the problem you solved (on 9.04), could you please explain what should i do? step by step? im a newb with ubuntu.

---

### Post by calrogman on 2009-07-20
Sorry for not replying sooner, I thought this thread was dead.

I did the following:
```
cp /lib/firmware/zd1211 /lib/firmware/`uname -r`/zd1211
modprobe zd1211rw
```

If your dongle starts working then add zd1211rw to /etc/modules using:
```
echo zd1211rw >> /etc/modules
```

---

