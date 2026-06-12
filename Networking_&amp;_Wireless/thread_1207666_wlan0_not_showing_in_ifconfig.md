---
title: "wlan0 not showing in ifconfig"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by Yizi on 2009-07-08
Hi,

I was using the macchanger and after a restart i was not able to connect to any wireless network, i tried ```
ifconfig
``` and the wlan0 is not there anymore, tried to do ```
ifconfig wlan0 up
``` it came back with a error saying no such device.

Please can anyone help me here, can't connect to internet...

---

### Post by iponeverything on 2009-07-08
Unless your using /etc/interfaces for wlan0, ifup is not going to work for it.

---

### Post by Yizi on 2009-07-08
I don't know about that but can you guide me to find out if it is? 
Thanks

---

### Post by kerry_s on 2009-07-08
not enough info, you need to tell us what you did with "macchanger".

the commnand to show wireless is-> **sudo iwconfig**

the devices listing is in /etc/udev/rules.d/70-persistent-net.rules
if you changed the mac that won't be correct so it won't be found.

did you check your /var/log/* for any relevant errors ?
have you tried uninstalling macchanger ?

---

### Post by Yizi on 2009-07-08
All i did with the macchanger was i changed the mac address to 00:11:22:33:44:55 and that is it.

---

### Post by Yizi on 2009-07-08
I did sudo iwconfig and it returned with 

lo     no wireless extensions
eth0   no wireless extensions
pan0   no wireless extensions

---

### Post by Yizi on 2009-07-08
I think its something to do with the driver, can anyone tell me how to reinstall the driver for wireless? i didn't load any driver for the wireless it was done automatically at the installation...

---

### Post by calsaverini on 2009-07-08
I'm having the exact same problem, I thing. I don't understand this very much, but I think my card wasn't even detected by the system. 

I'm using Ubuntu 9.04 64 bits. I just finish a fresh install 30 minutes ago, and did nothing except for an update and tried to install madwifi when I saw my wireless wasn't working. I know my card is an Atheros 5007, which gave me some trouble to install in previous versions but was working ok on Debian Lenny.

When I try to check on my pci devices I can't find any wireless cards:
```

calsaverini@mnemosyne:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
07:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
07:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
07:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
07:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

When I try iwconfig:
```

calsaverini@mnemosyne:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

No ath0 or wifi0 interfaces appear. On Debian Lenny I had a ath0 interface that was automatically detected on install. 

Anyone knows what happened?

When I was installing Ubuntu I connected the ethernet cable on my wired ethernet card. Will this preclude him from searching for a wifi interface? I hope not.:icon_frown:

---

### Post by kerry_s on 2009-07-08
> **Yizi said:**
> All i did with the macchanger was i changed the mac address to 00:11:22:33:44:55 and that is it.

udev use the mac address to identify the connection, what you've actually done is like hiding it. go to /etc/udev/rules.d/70-persistent-net.rules and change it to match your new mac or just remove the line so it can be rediscovered.

---

### Post by kerry_s on 2009-07-08
> **calsaverini said:**
> I'm having the exact same problem, I thing. I don't understand this very much, but I think my card wasn't even detected by the system. 

I'm using Ubuntu 9.04 64 bits. I just finish a fresh install 30 minutes ago, and did nothing except for an update and tried to install madwifi when I saw my wireless wasn't working. I know my card is an Atheros 5007, which gave me some trouble to install in previous versions but was working ok on Debian Lenny.

When I try to check on my pci devices I can't find any wireless cards:
```

calsaverini@mnemosyne:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
07:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
07:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
07:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
07:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

When I try iwconfig:
```

calsaverini@mnemosyne:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

No ath0 or wifi0 interfaces appear. On Debian Lenny I had a ath0 interface that was automatically detected on install. 

Anyone knows what happened?

When I was installing Ubuntu I connected the ethernet cable on my wired ethernet card. Will this preclude him from searching for a wifi interface? I hope not.:icon_frown:

yours is a different problem, you should start your own thread.
try> **modprobe ath5k**
then check> **sudo iwconfig**

---

### Post by Yizi on 2009-07-08
> **kerry_s said:**
> udev use the mac address to identify the connection, what you've actually done is like hiding it. go to /etc/udev/rules.d/70-persistent-net.rules and change it to match your new mac or just remove the line so it can be rediscovered.

Worked like a charm! that was the problem, deleted the line, logged off and everythings back to normall.... Thanks

---

### Post by kerry_s on 2009-07-08
> **Yizi said:**
> Worked like a charm! that was the problem, deleted the line, logged off and everythings back to normall.... Thanks

your welcome. i hope u don't do that again. ;)

---

### Post by j_niquito30 on 2009-08-25
> **kerry_s said:**
> udev use the mac address to identify the connection, what you've actually done is like hiding it. go to /etc/udev/rules.d/70-persistent-net.rules and change it to match your new mac or just remove the line so it can be rediscovered.


I'm into kinda the same problem but tried this and didnt work .... I think it might be related to the PCI bridge but i see that mine it's ok .... besides, i was not using macchanger ...


BTW .... i have my own thread [http://ubuntuforums.org/showthread.php?t=1231062&highlight=pci+problem+update](http://ubuntuforums.org/showthread.php?t=1231062&highlight=pci+problem+update)
but no luck what so ever

---

