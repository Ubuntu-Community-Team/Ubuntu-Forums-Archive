---
title: "DVD playback jumpy, can't figure it out."
date: 2011-04-27
forum: Multimedia Software
---

### Post by 84_K10Guy on 2011-04-27
I recently tried playing a DVD on my computer because I wanted to test how it worked before going on a trip in a few weeks. First Movie Player told me that it didn't have the proper plugins to play a DVD, so I got that figured out. But now when I try to watch any DVD the screen is jumpy during playback. I've never had a problem with this, not even during editing. I don't know what the problem is. Any help fixing this issue would be appreciated.

---

### Post by K_45 on 2011-04-27
```
sudo apt-get install vlc
```

and try your DVD in there.

---

### Post by 84_K10Guy on 2011-04-27
Still is a problem. It's not that big of a deal, but it would be nice to get it fixed. If this helps, it also does it on Youtube.

---

### Post by inobe on 2011-04-27
any tearing when scrolling in firefox, problems with desktop affects?

it use to work well, now it doesn't?

what do you think changed that'll cause this, updates, removing, installing apps?

run 

```
lspci
```

in terminal, paste output on next post.

---

### Post by lidex on 2011-04-27
Could be your graphics driver. What do you get for this, in a terminal:
```
sudo lshw -C display
```

---

### Post by K_45 on 2011-04-27
Make sure drop frames is enabled in VLC too. What drivers are you using?

---

### Post by 84_K10Guy on 2011-04-28
> **inobe said:**
> any tearing when scrolling in firefox, problems with desktop affects?

it use to work well, now it doesn't?

what do you think changed that'll cause this, updates, removing, installing apps?

run 

```
lspci
```in terminal, paste output on next post.

Here's what I got
```
zhoeffner@Zach-Laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
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
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

> **lidex said:**
> Could be your graphics driver. What do you get for this, in a terminal:
```
sudo lshw -C display
```

```
zhoeffner@Zach-Laptop:~$ sudo lshw -C display
[sudo] password for zhoeffner: 
  *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:19 memory:e0000000-efffffff(prefetchable)  memory:fe9f0000-fe9fffff ioport:ee00(size=256) memory:fea00000-feafffff

```

The only driver outside of what I get from the original installation is my wireless.

---

### Post by rigol2000 on 2012-03-15
Has a solution been found yet?  I see the replies just dropped off.

---

