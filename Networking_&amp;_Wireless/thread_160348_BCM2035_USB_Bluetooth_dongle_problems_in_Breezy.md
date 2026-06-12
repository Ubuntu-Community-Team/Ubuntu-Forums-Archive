---
title: "BCM2035 USB Bluetooth dongle problems in Breezy"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by goldfish654 on 2006-04-14
I have an identical problem to this poster:
[http://ubuntuforums.org/showthread.php?t=24876](http://ubuntuforums.org/showthread.php?t=24876)

However neither solution is useful, as I'm running Breezy with 2.6 kernel.  

Irritatingly I have another problem which causes my syslog to be completely full of these:
Apr 14 23:44:49 (none) kernel: [4298622.818000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

So I can't post much from there right now.  However the output is pretty much identical to the post linked above.  

Cheers!

EDIT: More links:
[https://lists.ubuntu.com/archives/ubuntu-users/2004-October/005671.html](https://lists.ubuntu.com/archives/ubuntu-users/2004-October/005671.html)
My problem is the same.
Here is some dmesg from when I connect the device:
```

[4294853.478000] RPC: failed to contact portmap (errno -5).
[4294855.792000] usb 2-1: new full speed USB device using uhci_hcd and address 3[4294855.907000] bcm203x_probe: Mini driver request failed
[4294855.907000] bcm203x: probe of 2-1:1.0 failed with error -5

```

---

### Post by goldfish654 on 2006-04-14
Finally! I solved it!

It appears that Broadcom devices require the firmware from bluez-firmware in order to work correctly.  This page: [https://lists.ubuntu.com/archives/ubuntu-users/2005-August/045914.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-August/045914.html) 
triggered me to go to the bluez page : [http://www.bluez.org/download.html](http://www.bluez.org/download.html)
Download bluez-firmware (there is a Debian package, but I wanted to be safe and ensure that the firmware was downloaded and installed to the right place).

I then unpacked bluez-firmware, ./configured it (as per the README), make install'd it and then copied the files from /lib/firmware/ to /usr/lib/hotplug/firmware.

Unplugged the device, plugged it in again and it works perfectly :)

There is a good reason why this wasn't included in Breezy by default, and that's the legal implications.  But it mightn't be a bad idea to make note of this reason somewhere so that someone else with a USB dongle like this doesn't need to spend 4 hours researching this!

---

### Post by davidmaxwaterman on 2006-07-26
I can't get my bluetooth dongle to work.

I've tried the firmware thing - it installed loads of files in /usr/lib/hotplug/firmware, but I still get :

```
Jul 26 12:44:24 localhost kernel: [11719.060213] usb 1-1: new full speed USB device using ohci_hcd and address 9
Jul 26 12:44:24 localhost kernel: [11719.310270] bcm203x: probe of 1-1:1.0 failed with error -5
```

lsusb shows :

```
Bus 001 Device 009: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth
```

and lsmod shows :

```

Module                  Size  Used by
bcm203x                 7012  0
hci_usb                18452  0
ppp_deflate             7744  0
zlib_deflate           25736  1 ppp_deflate
bsd_comp                7072  0
ppp_async              14624  1
crc_ccitt               2176  1 ppp_async
ppp_generic            37876  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7808  1 ppp_generic
rfcomm                 48216  0
l2cap                  28484  5 rfcomm
bluetooth              62180  5 hci_usb,rfcomm,l2cap
ipv6                  323492  10
radeon                136968  1
drm                    90744  2 radeon
ppdev                  11748  0
lp                     13804  0
parport                45936  2 ppdev,lp
cpufreq_userspace       5640  1
cpufreq_stats           6276  0
cpufreq_powersave       1920  0
cpufreq_ondemand        8284  0
cpufreq_conservative     9764  0
dm_mod                 69808  1
md_mod                 89336  0
sr_mod                 20100  0
af_packet              27080  2
snd_powermac           57920  3
snd_pcm_oss            68480  0
snd_mixer_oss          23072  1 snd_pcm_oss
snd_pcm               109892  3 snd_powermac,snd_pcm_oss
snd_timer              29188  2 snd_pcm
snd                    72532  9 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11716  1 snd
snd_page_alloc         12424  1 snd_pcm
sbp2                   28068  0
scsi_mod              179588  2 sr_mod,sbp2
apm_emu                 8364  0
option                  9536  1
usbserial              36880  4 option
airport                 7808  0
orinoco                47348  1 airport
hermes                  9024  2 airport,orinoco
ehci_hcd               39272  0
pcmcia                 49456  0
sungem                 38948  0
sungem_phy             10432  1 sungem
yenta_socket           33228  2
rsrc_nonstatic         14368  1 yenta_socket
pcmcia_core            51384  3 pcmcia,yenta_socket,rsrc_nonstatic
uninorth_agp           11432  1
agpgart                39900  2 drm,uninorth_agp
evdev                  12608  7
tsdev                   9440  0
ext3                  166824  1
jbd                    72436  1 ext3
ohci1394               42868  0
ieee1394              436560  2 sbp2,ohci1394
ohci_hcd               25732  0
usbcore               156576  7 bcm203x,hci_usb,option,usbserial,ehci_hcd,ohci_hcd
ide_cd                 38372  0
cdrom                  49500  2 sr_mod,ide_cd
ide_disk               20800  3
i2c_keywest            11936  0
capability              5352  0
commoncap               8256  1 capability
```

I'm running : Ubuntu 6.06 LTS

Any ideas?

Max.

---

### Post by Bil-E-daKid on 2007-05-20
Hey there Max - did you ever find a fix for this?  I'm getting the same error in Feisty.

---

### Post by davidmaxwaterman on 2007-05-20
> **Bil-E-daKid said:**
> Hey there Max - did you ever find a fix for this?  I'm getting the same error in Feisty.

No, sorry.

I think it's because mine is one of the very first dongles and the driver architecture is different - more is done in s/w than with other dongles. So the usual drivers don't work since they assume that more is done in h/w....or something. ...but that is just some vague memory of what the problem was (I haven't looked at it for a long time).

Max.

---

### Post by Bil-E-daKid on 2007-05-20
Hey - thanks for the quick response Max - much appreciated.

:-)

---

### Post by renaud00 on 2007-07-04
Hi

I fallowed what goldfish654 post as a solution and now I can pair my phone with the computer but when I try to connect to it I have connection failed on my phone, so I can't transfer anything or control anything

I use 7.04

any idea ??

Jeff

---

