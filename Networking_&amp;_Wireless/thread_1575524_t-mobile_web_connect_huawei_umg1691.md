---
title: "t-mobile web connect huawei umg1691"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by DantePasquale on 2010-09-15
Hi All,

I'm pulling my hair out as it seems many folks have this modem working properly, but I've tried every suggestion with no success.

Here's what I have:

```
2.6.31-22-generic #64-Ubuntu SMP Tue Aug 24 09:33:27 UTC 2010 x86_64 GNU/Linux
```

HUAWEI UMG 1691 usb dongle ( shows as vender 12d1 product 1446 )

```
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 014: ID 12d1:1446 Huawei Technologies Co., Ltd.** 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

And, it looks like it switched from ttyUSB0 to ttyUSB1 via modem-modeswitch udev rules:

```
61-option-modem-modeswitch.rules:ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"
```

```
ls -l /dev/ttyUS*
crw-rw---- 1 root dialout 188, 1 2010-09-15 21:16 /dev/ttyUSB1
```


But, modem-manager never finishes checking it -- constantly defers checking so it never shows up in network manager.

```
Sep 15 21:11:19 dexter kernel: [ 4592.892712] usb 2-6: new high speed USB device using ehci_hcd and address 13
Sep 15 21:11:19 dexter kernel: [ 4593.045920] usb 2-6: configuration #1 chosen from 1 choice
Sep 15 21:11:19 dexter kernel: [ 4593.047710] usbserial_generic 2-6:1.0: generic converter detected
Sep 15 21:11:19 dexter kernel: [ 4593.047844] usb 2-6: generic converter now attached to ttyUSB0
Sep 15 21:11:19 dexter kernel: [ 4593.047966] usbserial_generic 2-6:1.1: generic converter detected
Sep 15 21:11:19 dexter kernel: [ 4593.048064] usb 2-6: generic converter now attached to ttyUSB1
Sep 15 21:11:19 dexter kernel: [ 4593.390524] generic ttyUSB0: generic converter now disconnected from ttyUSB0
Sep 15 21:11:19 dexter kernel: [ 4593.390559] usbserial_generic 2-6:1.0: device disconnected
Sep 15 21:11:20 dexter modem-manager: (Huawei): (ttyUSB1) deferring support check
Sep 15 21:11:21 dexter usb_id[3808]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/ttyUSB0/tty/ttyUSB0'
Sep 15 21:11:21 dexter usb_id[3809]: unable to access '/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/ttyUSB0/tty/ttyUSB0'
Sep 15 21:11:23 dexter modem-manager: (ttyUSB1): re-checking support...
Sep 15 21:11:23 dexter modem-manager: (Huawei): (ttyUSB1) deferring support check
Sep 15 21:11:26 dexter modem-manager: (ttyUSB1): re-checking support...
Sep 15 21:11:26 dexter modem-manager: (Huawei): (ttyUSB1) deferring support check
```

I've tried using usb-modeswitch, but there aren't any rules, so I tried some in another post in this section that worked for that particular dongle, but usb_modeswitch isn't even getting the device -- strace shows that it can't get it, probably because modem-manger has it or maybe something else since modem-manager is constantly deferring.

Help!! I need to do a bunch of patching this weekend for a customer and I can't get connected from the hotel I'm at!!!

---

### Post by maxoud on 2010-09-17
Consider to try free _[Sakis3G]("http://www.sakis3g.org/")_. It requires Usb-ModeSwitch but everything goes automatically, except you have to provide PIN (and, may be, your operator).

---

### Post by DantePasquale on 2010-09-19
Thanks for the input. I fixed the issue by following:

[http://ubuntuforums.org/showpost.php?p=7533144&postcount=24]("http://ubuntuforums.org/showpost.php?p=7533144&postcount=24")

Download and install latest usb_modeswitch and things started working! I'll check out your recommendation too!

---

