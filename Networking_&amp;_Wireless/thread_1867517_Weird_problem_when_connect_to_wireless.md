---
title: "Weird problem when connect to wireless"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by SagoO on 2011-10-23
Everytime i want to connect to my wireless, I have to restart my router then connect again. I I dint restart my wireless, it will keep asking me password and cannot connect after I reboot my PC. What is the root cause actually?
I try a lot of method already. I am not sure what is the root cause. I try to uninstall and install again. But It still the same. After that, I give up network manager. I uninstall it and try WICD. But it also have this kind of problem. So, I dont think is the network manager problem. Is it caused by driver o something else? But if caused by driver, I dont think I can connect to Internet right now. Any help please?

For your reference:
```

sagoo@sagoo-Satellite-M200:~$ uname -a
Linux sagoo-Satellite-M200 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

```

```

sagoo@sagoo-Satellite-M200:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
[COLOR=Red]03:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)[/COLOR]
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


```

---

### Post by praseodym on 2011-10-23
Which module is that? ath5k or ath9k? Try to shut off the hardware encryption:

```
echo "options [COLOR="Red"]modulename[/COLOR] nohwcrypt=1" | sudo tee /etc/modprobe.d/atheros.conf
```

---

### Post by SagoO on 2011-10-23
> **praseodym said:**
> Which module is that? ath5k or ath9k? Try to shut off the hardware encryption:

```
echo "options [COLOR=Red]modulename[/COLOR] nohwcrypt=1" | sudo tee /etc/modprobe.d/atheros.conf
```

is ath5k. I try it already. but it is still the same. What is hardware encryption? Will it cause anything after i shut it off? Do it need to turn it on b since it doesnt help in this issue.

---

