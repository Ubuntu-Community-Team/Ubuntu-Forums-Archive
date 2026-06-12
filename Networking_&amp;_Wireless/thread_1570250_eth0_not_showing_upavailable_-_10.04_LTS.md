---
title: "eth0 not showing up/available - 10.04 LTS"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by ajturner on 2010-09-07
I got a new hard drive for my computer a little while ago and upgraded to ubuntu 10.04 LTS from 9.10.  Now eth0 doesn't show up.

My original /etc/network/interfaces:

```

auto lo
iface lo inet loopback

```I've since modified it to this:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```lshw -C network:

```

  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:7e:29:79
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=172.21.210.172 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d1000000-d100ffff

```/etc/NetworkManager/nm-system-settings.conf:

```

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```lspci | grep Ethernet:

```

08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```ifconfig -a:

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79888 (79.8 KB)  TX bytes:79888 (79.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:7e:29:79  
          inet addr:172.21.210.172  Bcast:172.21.211.255  Mask:255.255.252.0
          inet6 addr: fe80::21f:e1ff:fe7e:2979/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14998637 (14.9 MB)  TX bytes:1214617 (1.2 MB)

```And then doing *ifconfig eth0 up* gives me the following error:

eth0: ERROR while getting interface flags: No such device


Any help on this issue would be greatly appreciated.

Thanks!

---

### Post by MaindotC on 2010-09-07
Eth0 is usually for wired connections.  All I see from your lspci is a wireless adapter.

---

### Post by Iowan on 2010-09-07
What kind of card/chipset is eth0 *supposed* to be?
(**lshw -C network** doesn't show it)

---

### Post by ajturner on 2010-09-07
I did some searching and it appears the Intel flavor of my computer (HP Pavillion dv5 with AMD Turion X2) has this network card and I can't seem to find anywhere else saying the AMD version has different:

**Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)**

[http://h20386.www2.hp.com/CanadaStore/images/dv5-1130ca.pdf](http://h20386.www2.hp.com/CanadaStore/images/dv5-1130ca.pdf)

---

### Post by MaindotC on 2010-09-07
Well, do you have a wired interface on your laptop?

---

### Post by ajturner on 2010-09-08
> **strAlan said:**
> Well, do you have a wired interface on your laptop?

My wired ethernet connection worked fine with ubuntu 9.10 so I think so.

I'm sorry I haven't ever had any major problems with my network connections before so most of this is pretty unfamiliar to me.

---

### Post by MaindotC on 2010-09-08
Well you do have a wired interface on the right side there.  I'm looking at the HP site.  I don't know if this network card is a combo wired/wireless.  Look at the full lscpi and see if there are two network adapters listed.  Post them here unless you only see the AR5001.

---

### Post by ajturner on 2010-09-08
> **strAlan said:**
> Well you do have a wired interface on the right side there.  I'm looking at the HP site.  I don't know if this network card is a combo wired/wireless.  Look at the full lscpi and see if there are two network adapters listed.  Post them here unless you only see the AR5001.

I have an ethernet interface on the left side and another wire interface on the right (not ethernet though, not sure what it is and isn't labeled with any sort of name or diagram).  The only network adapter listed is the one i posted previously.

lspci:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

---

### Post by MaindotC on 2010-09-08
Yeah looks like that's the only network card on your lapper.  I have tried to pull up a visual of this network adapter but I can't get a picture that shows if it has Ethernet jacks on it, so I'm just going to assume this is a combo wireless/wired card.

Alright so assuming it's all 1 card, when you plug it into the access point, there should be green and amber lights illuminated around the interface.  This indicates that it is functioning, electrically.  I doubt your laptop has those lights but check the interface.  If your laptop doesn't have them, check the interface on the access point.  There should be 1 green (signifying power) and 1 amber that blinks (signifying data transfer).

If you don't see these lights, check the BIOS to see if the network card is enabled.  I know you probably didn't change any of these settings but just make sure it's enabled.  Also, shut off the wireless card if you have a killswitch somewhere on the chassis of the lapper.  If this is a combo wired/wireless card then this may shut off the wired connection as well, so you'll have to experiment to see if this helps narrow down the problem.

If it is enabled and/or you see lights around either your network card's or the AP's wired interface, you should have wired communication.  If you don't, log into your AP and there should be a menu item that shows a list of machines that are connected and see if your laptop is listed in there.

Let me know how far this brings you.

---

