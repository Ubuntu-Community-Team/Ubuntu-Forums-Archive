---
title: "How can I do for ZTE AC8710 modem"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by ncnc on 2012-07-08
I have a ZTE AC8710 3G modem. it works fine on my netbook.(Ubuntu 10.04)

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 002 Device 004: ID 19d2:fff1 ONDA Communication S.p.A. [/COLOR]
Bus 002 Device 002: ID 15d9:0a33 Dexon Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub.

Now I use it to my Dell laptop (Intel i 2450 , Ubuntu12.04LTS),it can't work!
i found :
gu@gu-Inspiron-N311z:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 006: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 004: ID 1bcf:2880 Sunplus Innovation Technology Inc. 
Bus 003 Device 006: ID 19d2:[COLOR=Red]fff5[/COLOR] ZTE WCDMA Technologies MSM 

Q1.why it changs to "fff5"?

I found the [posted]("http://ubuntuforums.org/showthread.php?t=1185452"): "http://ubuntuforums.org/showthread.php?t=1185452"
I don‘t know where "** 5553424312345678c00000008000069f030000000000000000  000000000000**"  come from.

I try : sudo usb_modeswitch -v 0x19d2 -p 0xfff5 -V 0x19d2 -P 0xfff1 -M 5553424312345678c00000008000069f030000000000000000 000000000000

display:
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 006 on bus 003 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x0a (out) and 0x89 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

Q2: Help me! How can I do?
Sorry for my poor English.

THX

---

### Post by sanderj on 2012-07-08
Answer #1: it has two different lsusb-IDs because such an USB WAN stick can be a WAN device, and a memory flash. But not at the same time. So it switches. With usb_modeswitch you can order the switching. 

FYI: I bought a ZTE USB WAN Stick a few weeks ago, and it was plug-and-play. See [http://ubuntuforums.org/showthread.php?t=2003480](http://ubuntuforums.org/showthread.php?t=2003480)
So: when you plugin in the stick, and click on the Network icon in the upper right corner, is there a new option "Mobile Broadband" (or something like that)?

If not, then [http://ubuntuforums.org/showthread.php?t=1901702](http://ubuntuforums.org/showthread.php?t=1901702) is useful for you:

First post #6 ([http://ubuntuforums.org/showpost.php?p=11576942&postcount=6):](http://ubuntuforums.org/showpost.php?p=11576942&postcount=6):) "I noticed that if i plugged in the modem and then powered on the system, then it would get detected and it would work. ". So: turn off your Ubuntu system, put in the USB WAN stick, and boot your Ubuntu system. Does it work then?

If not, as described in the post, post the output of 

```
dmseg | tail -n30
```

 
HTH

---

### Post by ncnc on 2012-07-08
```

gu@gu-Inspiron-N311z:~$ dmesg | tail -n30
[   86.078558] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   86.078572] cfg80211: World regulatory domain updated:
[   86.078579] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   86.078589] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   86.078599] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   86.078608] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   86.078616] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   86.078624] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  232.243488] usb 3-2: USB disconnect, device number 3
[  232.243674] option: option_instat_callback: error -108
[  232.243965] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  232.244006] option 3-2:1.0: device disconnected
[  232.244522] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  232.244552] option 3-2:1.1: device disconnected
[  232.245025] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  232.245077] option 3-2:1.2: device disconnected
[  232.248240] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  232.248275] option 3-2:1.3: device disconnected
[  246.071219] wlan0: authenticate with 00:27:19:4e:d1:42 (try 1)
[  246.073354] wlan0: authenticated
[  246.073840] wlan0: associate with 00:27:19:4e:d1:42 (try 1)
[  246.076512] wlan0: RX ReassocResp from 00:27:19:4e:d1:42 (capab=0x431 status=0 aid=1)
[  246.076517] wlan0: associated
[  256.210520] wlan0: no IPv6 routers present
[  398.258162] usb 3-2: new full-speed USB device number 4 using xhci_hcd
[  398.299100] scsi8 : usb-storage 3-2:1.0
[  399.300889] scsi 8:0:0:0: CD-ROM            ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[  399.308538] sr0: scsi-1 drive
[  399.309026] sr 8:0:0:0: Attached scsi CD-ROM sr0
[  399.309362] sr 8:0:0:0: Attached scsi generic sg1 type 5
gu@gu-Inspiron-N311z:~$ 


```

---

### Post by sanderj on 2012-07-08
Hi, I gave you three hints:

1) Check for network icon 
2) Plug in before booting
3) dmesg 

You only posted the dmesg output. Was that with the ZTE plugged in before booting, or with the ZTE plugging some time after the boot?

What the about the network icon?

---

### Post by cway00 on 2012-09-30
Good Day 

I am using the same ZTE AC8710 3G modem on windows I just recently installed Ubuntu 12.04 ( Fresh Installation) and I have tried alot of help like wvdial, sakis3g ...nd wha i observed is that my Modem is not detected at all..but was not successful making it work. Will be glad if someone could help me in solving this issue.

here is my more information 
lsusb 
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1fea:0047  
Bus 003 Device 003: ID 19d2:ffff ZTE WCDMA Technologies MSM 

```
and also 
dmseg | tail -n30

```

[   51.504351] type=1400 audit(1349001595.639:38): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=2479 comm="apparmor_parser"
[   55.966120] init: plymouth-stop pre-start process (2724) terminated with status 1
[  148.696122] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[  148.887570] Initializing USB Mass Storage driver...
[  148.889418] scsi5 : usb-storage 3-1:1.0
[  148.889730] usbcore: registered new interface driver usb-storage
[  148.889739] USB Mass Storage support registered.
[  148.904722] usbcore: registered new interface driver uas
[  149.893083] scsi 5:0:0:0: CD-ROM            ZTE      USB Storage FFFF 2.31 PQ: 0 ANSI: 2
[  149.912072] sr0: scsi-1 drive
[  149.912088] cdrom: Uniform CD-ROM driver Revision: 3.20
[  149.912841] sr 5:0:0:0: Attached scsi CD-ROM sr0
[  149.918815] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  398.952160] usb 3-1: USB disconnect, device number 2
[  795.000112] usb 3-1: new full-speed USB device number 3 using uhci_hcd
[  795.171227] scsi6 : usb-storage 3-1:1.0
[  796.173251] scsi 6:0:0:0: CD-ROM            ZTE      USB Storage FFFF 2.31 PQ: 0 ANSI: 2
[  796.194189] sr0: scsi-1 drive
[  796.194870] sr 6:0:0:0: Attached scsi CD-ROM sr0
[  796.195432] sr 6:0:0:0: Attached scsi generic sg2 type 5

```
Like I said help will be appreciated.

---

