---
title: "Managing/changing Multiple Wireless adapters"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by KryptoRoxx on 2011-01-02
Alrighty...I'll try to make the most sense of this as I can. I'm in a spot where my wireless access is about 200 ft from my computer so I bought a tl-wn721 adapter. I have already gotten the drivers for it but somehow I am still stuck with my wireless adapter built in to my sony vaio sz220 (yeah I know it's old...that's why I run ubuntu). So how do I change wireless adapters? The system does say that the realtek drivers associated with the 721 adapter are in use and enabled but in Win 7 I have much higher signal than what is currently displayed. Usually it's somewhere in the high 80 or 90s. Now it's hard to even get 70 and that's how I know that I'm on my built in adapter. I ran lspci -nn and this was my output. I know there's something I can do but I am still learning a lot and I just don't know and google isn't helping me a whole lot. I might just not be searching for the right thing. BTW I'm running 10.04 LTS. 


00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72M [GeForce Go 7400] [10de:01d8] (rev a1)
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 15)
09:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
09:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
09:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

And one more question that is kinda tied to this. Like some others I have found people are having problems with network manager from time to time. It seems that wicd is the solution. Will this work with ubuntu 10.04?

---

### Post by PatchesTheCaveman on 2011-01-02
Running this will disable your internal adapter until you reboot:
```
sudo modprobe -r iwl3945
```

Running this will permanently disable your internal adapter after the next reboot:
```
sudo bash -c "echo blacklist iwl3945 >> /etc/modprobe.d/blacklist.conf"
```

If you need to restore your internal wireless adapter after you permanently disabled it with the above command, edit the /etc/modprobe.d/blacklist.conf file and remove the line that says *blacklist iwl3945*.

Good luck!

---

### Post by KryptoRoxx on 2011-01-02
Ok got the disabling part.....it disables but I can't get the other adapter (the one I want) to enable....I tried following the directions on this page but I just can't get it working :confused: ```
http://wireless.kernel.org/en/users/Drivers/ath9k_htc#Get_the_driver
```

For the time being does ubuntu even work with multiple adapters at once? If I could get them working at the same time (not connected...but I could see both of them operational) that would be the best solution as I don't always have this adapter with me. I did Modprobe the new adapter and it does read out as there and everything

---

