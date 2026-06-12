---
title: "SIOCSIFFLAGS: Resource temporarily unavailable"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by Red Kelly on 2011-12-03
hi, after many hours searching I have fixed it!
I was making this post as I was going. I'll post it anyway so if anyone is in the same position it might help

In short I had to place the drivers off the cd supplied in the correct folder but I'll list all that I found to get to that conclusion.

So here is what I've done.

lsub
```

Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp.RTL8191S WLAN Adapter

```

```

xbmc@xbmc:~$ sudo ifconfig eth0 up
SIOCSIFFLAGS: Resource temporarily unavailable

```
Searched "SIOCSIFFLAGS: Resource temporarily unavailable" found:
[http://www.vidarholen.net/contents/linuxtips/](http://www.vidarholen.net/contents/linuxtips/)

dmesg```


[LIST=1]
[*][   22.870770] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[*][   22.870777] 
[*][   22.871001] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[*][   22.871007] 
[*][   22.887704] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[*][   22.887710] 
[*][   22.889190] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[*][   22.889197] 
[*][   22.889206] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[*][   22.889210] 
[*][   22.964110] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 20
[*][   22.964128]   alloc irq_desc for 20 on node -1
[*][   22.964135]   alloc kstat_irqs on node -1
[/LIST]

```
lines 641->

```

[   19.137558] 
[   19.137560] Linux kernel driver for RTL8192 based WLAN cards
[   19.137565] Copyright (c) 2007-2008, Realsil Wlan
[   19.145916] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[   19.145936] ACPI: resource nForce2_smbus [io  0x4e00-0x4e3f] conflicts with ACPI region SM00 [dma 19968-20031 pref]
[   19.145946] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.167724] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.170920] lp: driver loaded but no devices found
[   19.230020] type=1400 audit(1322909770.665:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=505 comm="apparmor_parser"
[   19.230880] type=1400 audit(1322909770.665:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=505 comm="apparmor_parser"
[   19.231379] type=1400 audit(1322909770.675:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=505 comm="apparmor_parser"
[   19.246230] ==>ep_num:4, in_ep_num:1, out_ep_num:3
[   19.246240] ==>RtInPipes:3  
[   19.246248] ==>RtOutPipes:4  6  13  
[   19.246258] ==>txqueue_to_outpipemap for BK, BE, VI, VO, HCCA, TXCMD, MGNT, HIGH, BEACON:
[   19.246265] 1  1  0  0  2  2  2  2  2  
[   19.682021] Dot11d_Init()
[   19.684130] usbcore: registered new interface driver rtl819xU
[   19.821814] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   19.822343] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   19.823384] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   19.823398]   alloc irq_desc for 21 on node -1
[   19.823404]   alloc kstat_irqs on node -1

```
lines 605-627
Full log:
[http://pastebin.com/G1wT0qw2](http://pastebin.com/G1wT0qw2)

Terminal log:
[http://pastebin.com/BHkNWhGy](http://pastebin.com/BHkNWhGy)

Searched  "SIOCSIFFLAGS: Resource temporarily unavailable" again found

[http://alexsleat.co.uk/2011/02/15/realtek-rtl8191s-in-ubuntu-10-10/](http://alexsleat.co.uk/2011/02/15/realtek-rtl8191s-in-ubuntu-10-10/)

But driver didn't work. Remembered the cd that came with the dongle, (had discarded as most cds don't have Linux drivers) this one had drivers and copied it into the /lib/firmware dir and shut-down the computer completely removed lan cable, and power cable; reconnected power and started. 
IT LIVED!!

I'm off to bed the suns coming up.

---

