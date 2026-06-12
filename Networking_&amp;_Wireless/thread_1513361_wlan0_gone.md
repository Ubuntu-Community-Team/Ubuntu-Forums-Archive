---
title: "wlan0 gone"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by The Low End Theory on 2010-06-19
for whatever reason i can no longer connect to wireless networks,and when i do ifconfig wlan0 doesnt show up, this just started this morning, and my wireless has been working fine up until this point.

sudo lshw -C network returns
```
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:c3:91:58
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff

```

lspci -nn returns

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
03:03.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)

```

sudo iwlist scan returns
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

lsusb returns
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive / Patriot Xporter 32GB (PEF32GUSB) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by The Low End Theory on 2010-06-19
> **pytheas22 said:**
> This seems to be a recurring issue (see [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/30666") from a long time ago).

If you remove the e100 module by typing:
```

sudo rmmod e100
```

then reinsert with special options appended:
```

sudo modprobe e100 eeprom_bad_csum_allow=1
```

does it work?  Or do you get the same error message in dmesg?

could something similar to this work with wlan0? it dissapeared on my laptop, and i was wondering if this would fix it.

---

### Post by pytheas22 on 2010-06-19
> **Mr. Popo said:**
> could something similar to this work with wlan0? it dissapeared on my laptop, and i was wondering if this would fix it.

Probably not, unfortunately.  The solution in this thread solves a specific problem with a particular ethernet driver; wireless issues are usually a very different story.

I'd be happy to help you, however, if you start a new thread.  In your thread, please include the output of these commands:
```

lshw -C Network
dmesg | grep -e wlan -ie radio
lspci -nn
sudo iwlist scan
lsusb
```

---

### Post by Iowan on 2010-06-19
> **pytheas22 said:**
> I'd be happy to help you, however, if you start a new thread. 
I can help with that - moved to new thread.

---

### Post by The Low End Theory on 2010-06-20
ok thanks
[http://ubuntuforums.org/showthread.php?p=9483445#post9483445]("http://ubuntuforums.org/showthread.php?p=9483445#post9483445")

---

### Post by pytheas22 on 2010-06-20
Thanks for the information.  It looks like the driver (b43) is claiming your card, but no interface is being brought up for some reason.  If you could please post the output of this command, it should help zero-in no what's going wrong:
```

dmesg | grep -e wlan -e b43
```

---

### Post by The Low End Theory on 2010-06-20
```
[    1.274546] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4565.307616] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[ 4566.120873] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 4566.120893] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfcfe000)
[ 4566.120899] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[ 4566.120906] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x1 (was 0x0, writing 0x106)
[ 4567.684178] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4835.015601] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[ 4835.840466] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 4835.840486] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfcfe000)
[ 4835.840492] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[ 4835.840499] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x1 (was 0x0, writing 0x106)
[ 4837.400177] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5642.227754] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[ 5643.045004] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 5643.045023] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfcfe000)
[ 5643.045029] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[ 5643.045036] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x1 (was 0x0, writing 0x106)
[ 5644.604178] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

```

---

### Post by pytheas22 on 2010-06-20
Thanks for the information.  Did this problem start occurring after you woke you computer back up from a suspended state (i.e., when it was "sleeping"), or did it appear after a fresh reboot?

A possible solution to try is to power the computer down completely, unplug the power cord (and remove the battery if this is a laptop, which I think it is), then hold the power button in for thirty seconds.  This will force all of your hardware to reset.  I think this may solve the problem, because from your dmesg output, the issue appears to have to do with the driver being unable to "wake up" the wireless card.

---

### Post by The Low End Theory on 2010-06-20
it happened after i booted it, i tried what you said but no luck :(

---

### Post by pytheas22 on 2010-06-20
Sorry that didn't help.  What output do you get if you type (in this order):

```
sudo rmmod ssb
sudo rmmod b43
sudo modprobe b43
sudo ifconfig wlan0 up
dmesg | grep -e wlan -e ssb -e b43
grep -iR b43 /etc/modprobe.d
```

---

### Post by The Low End Theory on 2010-06-20
well that made wireles work, however if im  not mistaken its not using the ndiswrapper driver, rather the "native" broadcom driver. either way thank you, and if it matters heres the output

```
nick@nick-laptop:~$ sudo rmmod ssb
[sudo] password for nick: 
nick@nick-laptop:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
nick@nick-laptop:~$ sudo modprobe b43
nick@nick-laptop:~$ sudo ifconfig wlan0 up
nick@nick-laptop:~$ dmesg | grep -e wlan -e ssb -e b43
[    1.287603] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.344071] ssb: Sonics Silicon Backplane found on PCI device 0000:03:03.0
[   66.151716] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[   66.986769] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[   66.986789] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfcfe000)
[   66.986795] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[   66.986802] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x1 (was 0x0, writing 0x106)
[   68.556198] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  100.467732] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[  101.236678] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  101.236697] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfcfe000)
[  101.236703] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[  101.236710] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x1 (was 0x0, writing 0x106)
[  102.800178] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  134.810970] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[  169.962089] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  170.020244] ssb: Sonics Silicon Backplane found on PCI device 0000:03:03.0
[  170.091649] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[  170.216697] Registered led device: b43-phy0::tx
[  170.217283] Registered led device: b43-phy0::rx
[  170.217842] Registered led device: b43-phy0::radio
[  170.268220] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  170.337361] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  170.354114] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  170.367494] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[  170.488198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  170.531267] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  178.128432] wlan0: deauthenticating from 00:21:91:04:02:e7 by local choice (reason=3)
[  178.128820] wlan0: direct probe to AP 00:21:91:04:02:e7 (try 1)
[  178.133582] wlan0: direct probe responded
[  178.133591] wlan0: authenticate with AP 00:21:91:04:02:e7 (try 1)
[  178.135059] wlan0: authenticated
[  178.135090] wlan0: associate with AP 00:21:91:04:02:e7 (try 1)
[  178.137831] wlan0: RX AssocResp from 00:21:91:04:02:e7 (capab=0x431 status=0 aid=5)
[  178.137839] wlan0: associated
[  178.139255] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  188.476030] wlan0: no IPv6 routers present
nick@nick-laptop:~$ grep -iR b43 /etc/modprobe.d
/etc/modprobe.d/broadcom.conf:blacklist b43
/etc/modprobe.d/broadcom.conf:blacklist b43legacy
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.

```

---

### Post by pytheas22 on 2010-06-20
Right, you're using the native driver, which is called b43, not ndiswrapper.  I'm not positive why those commands solved the problem, but it looks from your dmesg output like removing and then reinserting the ssb and b43 modules made the card start working properly.  If it breaks again, please try running:
```

sudo rmmod ssb
sudo rmmod b43
sudo modprobe b43
```

and see if that fixes it.  If it does, and this problem recurs often, we could write a script to run those commands automatically when the system boots.

---

### Post by The Low End Theory on 2010-06-21
ok thanks for the help,
do you know of a way to put it in monitor mode?

---

### Post by pytheas22 on 2010-06-21
```
sudo iwconfig wlan0 mode monitor
```

should work.  If it complains, try putting the interface down with ifconfig first, and also killing NetworkManager.

If you're using aircrack you can use the airmon-ng script to put interfaces in monitor mode.

---

### Post by Iowan on 2010-06-21
Merged threads - something didn't work properly when I split previous posts to new (this) thread.

---

### Post by spider_0k on 2012-07-23
> **pytheas22 said:**
> Thanks for the information.  Did this problem start occurring after you woke you computer back up from a suspended state (i.e., when it was "sleeping"), or did it appear after a fresh reboot?

A possible solution to try is to power the computer down completely, unplug the power cord (and remove the battery if this is a laptop, which I think it is), then hold the power button in for thirty seconds.  This will force all of your hardware to reset.  I think this may solve the problem, because from your dmesg output, the issue appears to have to do with the driver being unable to "wake up" the wireless card.

Worked for me I'm happy to say. Thank you to everyone for their suggestions.

---

### Post by wildmanne39 on 2012-07-23
Thanks for sharing. Thread Closed.

---

