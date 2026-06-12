---
title: "Problem with wifi USB adapter"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by kcode on 2010-01-13
hi,

I'm unable to use Cisco Linksys Wireless-G USB adapter - Model No. WUSB54GC ver 3. 

Ubuntu distribution : Hardy Heron (updated)

Desktop Environment : wmii

lsusb : 
```

Bus 007 Device 006: ID 1737:0077  
Bus 007 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002  
Bus 006 Device 001: ID 1d6b:0002  
Bus 004 Device 001: ID 1d6b:0001  
Bus 005 Device 001: ID 1d6b:0001  
Bus 003 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 003 Device 001: ID 1d6b:0001  
Bus 002 Device 001: ID 1d6b:0001  
Bus 001 Device 001: ID 1d6b:0001  

```First line corresponds to this device.

dmesg : 
```

[   36.481392] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   36.481454] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   38.100175] evdev.c(EVIOCGBIT): Suspicious buffer size 511, limiting output to 64 bytes. See http://userweb.kernel.org/~dtor/eviocgbit-bug.html
[   68.136046] PPP BSD Compression module registered
[   68.232257] PPP Deflate Compression module registered
[  483.002311] CE: hpet increasing min_delta_ns to 15000 nsec
[  525.672170] prism2_usb: no symbol version for module_layout
[ 2113.933998] usb 7-5: USB disconnect, address 4
[ 2124.576215] usb 7-5: new high speed USB device using ehci_hcd and address 5
[ 2124.726579] usb 7-5: configuration #1 chosen from 1 choice

```
Kernel : 2.6.31.5

ifconfig : Has no mention of wlan

lshw : Has no mention this device.

Tried startup with device connected, no success.

Read some threads which generally correspond to version 2 of the device.

It probably uses Ralink chipset(cmiiw). I neither have Rt73 nor prism2_usb installed, confirmed by lsmod.

Thanks

---

### Post by clearwood on 2010-01-23
Fellow ubuntu user

I had a similar problem tjeck this:
[http://www.glenscott.net/2009/12/01/how-to-fix-huawei-e620-usb-3g-modem-in-ubuntu-9-10-karmic-koala/](http://www.glenscott.net/2009/12/01/how-to-fix-huawei-e620-usb-3g-modem-in-ubuntu-9-10-karmic-koala/)

best regards

---

### Post by pdc on 2010-01-23
I think kcode is trying to get this configured

> 1737:0077

rather than the 

> ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

but it is certainly tricky to have both plugged in at the same time;

kcode:

have a read at this post

[http://ubuntuforums.org/showthread.php?t=1273401](http://ubuntuforums.org/showthread.php?t=1273401)

see if it helps

I suspect you need the rt3070 and you may need to blacklist one or two rt modules that may also be present

---

