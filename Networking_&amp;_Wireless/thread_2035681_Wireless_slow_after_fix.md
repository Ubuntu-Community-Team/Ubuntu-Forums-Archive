---
title: "Wireless slow after fix"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by Matt12334 on 2012-07-31
Earlier today, I was getting incredibly fast internet on my laptop, but it has dropped significantly (from 33.5 Mbps down to ~5 Mbps), but my iPad, as well as the same laptop on Windows 7, gets 30+ Mbps.  I haven't made any system changes that would cause such a sudden decrease in performance, so I'm curious if there's a fix for this.

It seems to be a stability issue more than anything, as it seems to be an intermittent issue.  I've tried rebooting (does that even work for linux?!), but to no avail.

Any suggestions would be fantastic.

---

### Post by madvinegar on 2012-07-31
Hi. We need more info about your wireless card.

please post the results of

```
lspci
sudo lshw -c network
sudo rfkill list all
```

---

### Post by Matt12334 on 2012-07-31
> **madvinegar said:**
> Hi. We need more info about your wireless card.

please post the results of

```
lspci
sudo lshw -c network
sudo rfkill list all
```

```

matt@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

``````

matt@ubuntu:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: b8:70:f4:72:9d:d6
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:b3400000-b340ffff
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:fe:27:6a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-27-generic firmware=N/A ip=192.168.1.112 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b2400000-b240ffff

``````

matt@ubuntu:~$ sudo rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Edit: During the time spent preparing this reply, my connection speed has bounced between 33 Mbps and 6 Mbps, so I really think something's being weird with my system.

---

### Post by madvinegar on 2012-07-31
Do this

Open terminal and write:

```
sudo gedit /etc/modprobe.d/ath9k.conf 
```

A blank document will open. Insert inside the following line:

```
options ath9k nohwcrypt=1
```

Save, reboot, use your internet for some time to check if all is ok, and let me know if it worked.

---

### Post by Matt12334 on 2012-07-31
Thanks, I just applied the setting. Now to see if it works...

---

### Post by Matt12334 on 2012-07-31
It seems to have caused further issues. Upload tests now refuse to start on speediest.net. I'm deleting the line from that file. Is it safe to delete the file itself if it's empty after?

---

### Post by madvinegar on 2012-08-01
Are you sure you have not messed with anything else???

---

### Post by Matt12334 on 2012-08-02
> **madvinegar said:**
> Are you sure you have not messed with anything else???

I've messed with lots of things, but I undid anything that didn't make a significant performance boost. I believe the only change I kept was one that killed my wlan0 power management. I'm not even 100 percent sure that it works. It says that it's off, but that means nothing to me. I've had my gamma at 1.0 even though it said it was .8, so I don't know what to believe. The gamma issue is fixed though.

---

