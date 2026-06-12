---
title: "Wifi seems to be spotty and slow"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by cwblanch on 2013-08-02
Hi,[INDENT]I wasn't sure how else to title this post, but exactly as it says the internet seems to be spotty and slow.  I have a windows 7 partition and it works just fine. No slowdowns or drops. I'm not sure how to troubleshoot wifi internet issues in Ubuntu 12.04

For example, sometimes I'll watch an HD video on Youtube or otherwise in windows, and it works fine, no stops or anything. But in Ubuntu it has to always stop to load and buffer. Sometimes I can't even stream music!
Any help would be appreciated.

Thanks!
[/INDENT]

---

### Post by kurt18947 on 2013-08-02
What adapter/chipset?  If internal, please post the output of "lspci", if USB "lsusb".  There's more but that's a start, some chipsets/adapters have known issues.

---

### Post by cwblanch on 2013-08-03
> **kurt18947 said:**
> What adapter/chipset?  If internal, please post the output of "lspci", if USB "lsusb".  There's more but that's a start, some chipsets/adapters have known issues.

Internal. I wasn't sure what to post so I put everything.

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

---

### Post by Bucky Ball on 2013-08-03
*Thread moved to **Networking & Wireless**.*

Unsure why this was in ***General Help.***

Please provide the output of:

```
sudo lshw -C network
```

That will reveal more. So far, your output shows you have an AR928X Wireless Network Adapter, an Atheros device.

PS: I believe this card has wireless N. That can sometimes cause problems if switched on and the access point does not have wireless N. Have a check on the router/modem that it is either capable of wireless N or that it is off or on. As the card is working, just getting sporadic, I am presuming you have the correct drivers installed (think those are in the kernel already) and that this problem lies elsewhere and is not a driver issue.

I could, of course, be wrong. ;)

---

### Post by wildmanne39 on 2013-08-03
Hi, try this please copy and paste one line at a time:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

### Post by cwblanch on 2013-08-05
> **Bucky Ball said:**
> *Thread moved to **Networking & Wireless**.*

Unsure why this was in ***General Help.***

Please provide the output of:

```
sudo lshw -C network
```

That will reveal more. So far, your output shows you have an AR928X Wireless Network Adapter, an Atheros device.

PS: I believe this card has wireless N. That can sometimes cause problems if switched on and the access point does not have wireless N. Have a check on the router/modem that it is either capable of wireless N or that it is off or on. As the card is working, just getting sporadic, I am presuming you have the correct drivers installed (think those are in the kernel already) and that this problem lies elsewhere and is not a driver issue.

I could, of course, be wrong. ;)

It seems to work just fine for my windows partition, phone and other (older) laptop that I tested it on, and the router doesn't seem to have any issues.
I'm actually downloading a game in Steam right now and I took some time to watch it and it has lost connection and gone down into the bytes speed several times.

```
 *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:ca:47:14
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f8500000-f8503fff ioport:2000(size=256) memory:c0000000-c001ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4d:b7:b2:38
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-37-generic firmware=N/A ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f8600000-f860ffff

```

---

### Post by Bucky Ball on 2013-08-06
Now perhaps

```
iwconfig
```

All seems to be fine, driver installed, etc., from your last output, so wondering if it's external to the card or computer. As you were downloading a game it appears the connection does work fine, when it wants to, then drops or slows the connection unexpectedly. Are you sure this is not the server at the other end being bashed? 

I would perhaps try downloading the same in Windows and see if it starts okay then slows to a crawl. Just a thought because I don't really have any others at this point. ;)

---

### Post by wildmanne39 on 2013-08-06
Possibly try what is in post 5 most of the time it will fix that issue with the ath9k driver.
Thanks

---

