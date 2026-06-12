---
title: "No wireless after 9.10 upgrade"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by marcusesses on 2009-10-30
I think I'll join the chorus of those whose wireless isn't working in 9.10.

I upgraded from 9.04 to 9.10 last night and after the update,network manager was unable to detect any networks. I thought the problem was in network manager, so I instead installed wicd (which I have been using since 8.04) and no such luck there.

I should point out that wireless worked in 9.04, and stopped in 9.10.

Output of lshw -C network

```

*-network               
       description: Ethernet interface
     *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:10:7a:34
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5787m-v3.23 ip=192.168.2.14 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f6000000-f600ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
  product: NetLink BCM5787M Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:10:7a:34
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5787m-v3.23 ip=192.168.2.14 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f6000000-f600ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
  physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:00:97:e4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:f8000000-f8000fff

```

Output of lsmod | grep iwl3945

```

iwl3945                77212  0 
iwlcore               112508  1 iwl3945
mac80211              181236  2 iwl3945,iwlcore
cfg80211               93052  3 iwl3945,iwlcore,mac80211
led_class               4096  3 iwl3945,iwlcore,acer_wmi

```

Output of /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

```

After the install, only the first two lines were in the interface file. I added the last two lines later, but this didn't seem to change much.

I've seen some other people who have had issues with a Broadcom driver, but I'm not sure if this applies here, as I'm not using any proprietary drivers.

Thanks.

---

### Post by vegas588 on 2009-10-30
I have the same problem as well. No wireless after installing 9.10. Worked in previous versions.

HP Pavilion dv6000 laptop.

---

### Post by NightHawk877 on 2009-10-30
Try recompiling your driver. I have to do that whenever there is a kernel upgrade and I had to do it again when I upgraded. See if that works.

---

### Post by marcusesses on 2009-10-30
> **NightHawk877 said:**
> Try recompiling your driver. I have to do that whenever there is a kernel upgrade and I had to do it again when I upgraded. See if that works.

How does one do that?

Actually, I may have run into a DIFFERENT problem now. 

I rebooted, and when I checked WICD, it detected the wireless networks, but I was unable to click on any of the networks (instead of black fonts, they were all in gray fonts, and I wasn't able to clock anything). 

So I may have fixed my original problem about detecting networks, but now I can't access WICD. 

Also, when upgrading (and installing wicd), there was an error in downloading "python-wxversion", which is used for GUIs, I believe. I think this may be where my wicd problem is originating.

---

### Post by DJChung on 2009-10-30
New U 9.10 install / new user problem.

When I installed U 9.04, the install process detected wireless network, asked for the WEP password, and connected to my home WiFi.  However, after install, U 9.04 would not boot from the HD.  So, I abandoned the effort and installed U 9.10.

The 9.10 install went smoothly and, after the install, the system came up; but no network is detected.  When I click on the wireless icon at top right, it displays the drop down menu; however, in the drop down menu, there are no wireless networks that I can select from.

In a WinXP machine (located in the same room as the Ubuntu machine and having the same model Linksys PCI wireless card as the Ubuntu machine), shows at least three networks - my home wireless network and a couple from neighbors' networks.

In the Unbuntu machine, do I need to install drivers?  Can I make it "scan" and look for networks?  What do I do?

Are there documentation or FAQ where I can search for answers to these stupid newbie questions without having to bother the forum members?

Machine spec.:
Asus MB CUV4X
Pentium III 800 MHz
512 MB RAM
WD Caviar 120 GB HD (no dual boot; just clean HD with only U 9.10)
AGP Voodoo 3dfx video card connected to a Samsung 21.4 inch LCD (1600x1200)
Linksys wireless card in a PCI bus
MS mouse and keyboard

Thanks for your help.

---

### Post by marcusesses on 2009-10-30
Problem was (somewhat) solved. 

After rebooting, I was able to detect wireless networks in wicd. However, I was unable to access them using the wicd GUI because of an issue installing python-wxversion.

I resolved this using the command 

```
wicd-curses
```

which is a terminal-based version of wicd. I was able to connect to my wireless from here.

However, I was still unable to install python-wxversion, which may effect some other applications I'm running.

---

### Post by DJChung on 2009-10-30
Problem solved by a clean re-install of 9.10.  Now, the wireless icon, when clicked, shows my WiFi.  Don't know what happened, but the re-install fixed it.

---

