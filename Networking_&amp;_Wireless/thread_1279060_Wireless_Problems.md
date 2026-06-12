---
title: "Wireless Problems"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by lewisforlife on 2009-09-30
I have a Compaq Presario CQ060 laptop with Ubuntu 9.04 on it.  I was able to connect to wireless networks with my laptop after first installing Ubuntu, but the internet connection was really slow.  I did a hardware scan, and a different driver came up for my wireless card, I decided to install it, wireless quit working all-together after that.  I cannot seem to figure out what the issues is.  I have searched the forum but cannot find a solution.

```

michael@michael-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:7b:45:97
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:f0:96:b3:0e:18
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```

michael@michael-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

Thanks for your help.

David

---

### Post by semitone36 on 2009-09-30
Strange... neither of those outputs even list a wireless card.  Where did you get your new driver? Can you uninstall it?

---

### Post by lewisforlife on 2009-09-30
I got the driver from going to [System->Administration->Hardware Drivers], it did a scan of hardware, and popped up and said another driver was available for my wireless card, so I figured I would try it since my internet connection was going really slow.  This is when it quit working, and would not even detect the card.

Thanks,

David

---

### Post by semitone36 on 2009-09-30
Ah.  Try going back to Hardware Drivers.  Im not running Ubuntu anymore so I cant check but from what I remember that program should still have your old driver listed.  You should be able to just switch back to your old driver.

---

### Post by lewisforlife on 2009-09-30
I have tried that, the old driver is not listed.  Is there any other way that I can roll back to an old driver, or anyway to get my laptop to detect my wireless card now?

Thanks,

---

### Post by semitone36 on 2009-09-30
Sorry mate, this is beyond what i know.  Perhaps somebody else might know what to do?

---

### Post by Ayuthia on 2009-09-30
Do you have another OS installed on this computer?  If so, does the wireless card work?  The lspci information not showing up for your wireless card sometimes points to a hardware issue.

---

### Post by lewisforlife on 2009-09-30
I was thinking the same thing at first, but I have dual boot with Vista (don't ask me why), but it does work in vista.

Thanks,

David

---

### Post by lewisforlife on 2009-09-30
I just realised something, my laptop has a button on it that turns wireless on and off on the laptop.  When it is blue it means wireless is on, red means it is off.  When I just booted into vista, it was red by default, I pushed it and it turned blue and wireless was activated.  When I rebooted into ubuntu, the button was red, pushing it has not effect, it won't turn on which means I can't get wireless to work.  Does anyone have any suggestions?

Thanks,

David

---

### Post by nevarDeath on 2009-09-30
Yeah hardware was my first thought too. See if you can determine the chipset in your wireless card, maybe by taking whatever is listed in device manager for your wireless card
Click on start
right-click on "Computer"
left click on "Properties"
left click on "Device Manager" in the upper left hand corner
click on the "Continue" button if you have UAC on.
then click on the + box to the left of "Network Adapters"

take that and google "Chipset [whatever device is listed]"
Then once you seen figure out the chipset google "[chipset] linux driver"
This is what I would do in your situation. You may want to see if your card is listed on the Backtrack Hardware compatibility list also, because it should tell you a driver that will work with it [http://backtrack.offensive-security.com/index.php/HCL:Wireless](http://backtrack.offensive-security.com/index.php/HCL:Wireless)
This may not be a simple or elegant solution, but since ubuntu doesn't appear to recognize it anymore I don't know what else you could do.

---

### Post by lewisforlife on 2009-09-30
From Vista, I found out that it is an Atheros AR5007 802.11b/g WiFi Adapter.  I will see what I can do about getting a driver and will keep all updated.

---

### Post by lewisforlife on 2009-09-30
I installed the MadWifi driver that someone suggested.  I believe my wireless card is detected now.  Here are the deatils:
```

michael@michael-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:7b:45:97
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.103 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:24:2c:3a:c0:36
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:08:b8:94:ab:f1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
```

michael@michael-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

Now my only problem is connecting to a network I guess.  My laptop is not automatically detecting wireless networks, so I tried: sudo wlanconfig wifi0 list scan in a terminal with no luck either.  Where can I go from here.  Thanks for all of the help and getting me this far, I feel I am getting a lot closer.

Thanks,

David

---

### Post by t0mppa on 2009-09-30
Ah, looks like you have the same card as me then. Should have AR242x as your chip then. The wireless led doesn't work by default on Linux, but the switch still works, so you probably just accidentally pressed it and disabled the wireless.

You probably enabled the "Madwifi" driver, which is an older version that still uses the ieee80211 stack instead of the newer mac80211. Ath5k was changed to be the default driver on Jaunty though, since it's using the newer stack that is slowly replacing the older one. Both drivers should work though, so it's really up to you which one you want to use.

So, bottom line is that you should see your interface, when you enable it through the hardware switch. If the driver you're using isn't working, you'll just have to revert back to the old one, which should be as simple as deactivating the one you picked from Hardware Drivers, but if that doesn't do it, will have to do it manually.

EDIT: Ahh, a little late with the reply. Should've checked the thread for further input. Anyhow, if your wireless worked just fine earlier before you changed the drivers, I suggest you just go back to ath5k.

---

### Post by lewisforlife on 2009-10-01
The MadWifi driver seems to be working now, thanks for all of the help.

David

---

