---
title: "Problems with Wifi on my Dell D610 after uprgrade to 12.01"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by sjoseph on 2012-08-03
I had been using 10.? LTS for sometime, than my wireless stopped working so I tried a number of things and then upgraded to 12.01.. It continued to not find my local router.. after trying a number of attempts (downloading and installing bcmwl-kernel-source) and still nothing. I attached a USB linkeys and it worked right away. So i thought the wife card was fried. Bought a new one and just installed it w no change. Here's what Ubuntu finds on my system.. I'd rather not run on the USB if I don't have to.. 

lspci -vvnn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)

Is it possible that this card isn't supported?..is this a driver issue?

Any help would be appreciated. I'm tired of trying to find the answers on my own...

---

### Post by chili555 on 2012-08-03
> lspci -vvnn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
This is an ethernet card, not wireless. Please check a little deeper:```
lspci -nn | grep 0280
```

---

### Post by sjoseph on 2012-08-03
> **chili555 said:**
> This is an ethernet card, not wireless. Please check a little deeper:```
lspci -nn | grep 0280
```

Hmmm, I get nothing with this command. Does this mean that my card isn't being recognized?

---

### Post by chili555 on 2012-08-03
> **sjoseph said:**
> Hmmm, I get nothing with this command. Does this mean that my card isn't being recognized?Not sure yet. Let's see:```
lspci -nn
lsusb
```> So i thought the wife card was fried. Bought a new one and just installed it w no change. Are you quite certain everything is connected properly?

---

### Post by sjoseph on 2012-08-03
> **chili555 said:**
> Not sure yet. Let's see:```
lspci -nn
lsusb
```Are you quite certain everything is connected properly?

results for lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV370 [Mobility Radeon X300] [1002:5460]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)

and

results for lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]

I am confident that the new card I installed is connected correctly..

Thanks in advance for your help.

---

### Post by chili555 on 2012-08-03
Sorry. Nothing here, aside from your USB Linksys, is a wireless device. I'm not sure how we can help you further.

---

