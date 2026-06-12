---
title: "Netgear WG511 v2 PCMCIA wireless card trouble"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Jack Bonner on 2009-08-11
I really need a hand on this one,i'm trying to set this damn wireless card up for someone. I've tried various things from other threads and websites, but none of them seem to work. It's the dreaded Chinese version of the card. One site called for me to take the drivers from the Windows install disk, but they don't seem to exist. All I can find are .dlls and setup.exe, autorun.exe and the like. The drivers aren't where the site said they'd be. Next I tried something from these forums, using cabextract to remove the drivers from the installer taken from the Netgear website. That doesn't work either, stating the "No valid cabinets found" error. So what can I do? Can someone give me a step by step guide for this card version and this Distro version. (9.04). I'm quite surprised, even setting up my wireless card on Arch was easier than this.

Cheers in advance for any advice.

---

### Post by tgalati4 on 2009-08-11
First of all, does the card work in Windows?  I've had one fail on me and it was always locking up in linux.  The flexing of the card can sometimes delaminate the chip inside causing strange errors.

What is the output of:

dmesg | tail -50

Immediately after inserting the card?

Here's mine for a WG511U (a and g band) on Jaunty:

[ 3461.768066] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 3461.768132] pci 0000:0c:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[ 3461.815994] cfg80211: Calling CRDA to update world regulatory domain
[ 3461.915585] cfg80211: World regulatory domain updated:
[ 3461.915593] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3461.915600] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3461.915607] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3461.915613] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3461.915619] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3461.915625] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3461.934289] ath5k_pci 0000:0c:00.0: enabling device (0000 -> 0002)
[ 3461.934305] ath5k_pci 0000:0c:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3461.934792] ath5k_pci 0000:0c:00.0: registered as 'phy0'
[ 3461.974262] phy0: Selected rate control algorithm 'pid'
[ 3461.976955] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
[ 3461.976963] ath5k phy0: RF5112B multiband radio found (0x36)
[ 3466.108064] ADDRCONF(NETDEV_UP): wlan0: link is not ready

So, the pcmcia card was detected properly, the wireless chip (atheros 5213A was detected) and wlan0 was not ready because I haven't logged in yet.

If I right-click on the connection icon, it shows up as "Atheros 5001X Network Card".

The drivers load automatically and show up as "ath5k" when doing:

lsmod

---

### Post by Jack Bonner on 2009-08-11
> **tgalati4 said:**
> First of all, does the card work in Windows?  I've had one fail on me and it was always locking up in linux.  The flexing of the card can sometimes delaminate the chip inside causing strange errors.

What is the output of:

dmesg | tail -50

Immediately after inserting the card?

Here's mine for a WG511U (a and g band) on Jaunty:

[ 3461.768066] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 3461.768132] pci 0000:0c:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[ 3461.815994] cfg80211: Calling CRDA to update world regulatory domain
[ 3461.915585] cfg80211: World regulatory domain updated:
[ 3461.915593] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3461.915600] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3461.915607] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3461.915613] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3461.915619] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3461.915625] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3461.934289] ath5k_pci 0000:0c:00.0: enabling device (0000 -> 0002)
[ 3461.934305] ath5k_pci 0000:0c:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3461.934792] ath5k_pci 0000:0c:00.0: registered as 'phy0'
[ 3461.974262] phy0: Selected rate control algorithm 'pid'
[ 3461.976955] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
[ 3461.976963] ath5k phy0: RF5112B multiband radio found (0x36)
[ 3466.108064] ADDRCONF(NETDEV_UP): wlan0: link is not ready

So, the pcmcia card was detected properly, the wireless chip (atheros 5213A was detected) and wlan0 was not ready because I haven't logged in yet.

If I right-click on the connection icon, it shows up as "Atheros 5001X Network Card".

The drivers load automatically and show up as "ath5k" when doing:

lsmod

The card worked fine in Windows, here's the output of dmesg | tail -50

```
[   20.883653] Bridge firewalling registered
[   22.187023] pci 0000:01:05.0: power state changed by ACPI to D0
[   22.187040] pci 0000:01:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.478089] [drm] Initialized drm 1.1.0 20060810
[   22.580250] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   22.796050] ppdev: user-space parallel port driver
[   23.099425] agpgart-ati 0000:00:00.0: AGP 3.0 bridge
[   23.099449] agpgart-ati 0000:00:00.0: putting AGP V3 device into 8x mode
[   23.099474] pci 0000:01:05.0: putting AGP V3 device into 8x mode
[   23.339096] [drm] Setting GART location based on new memory map
[   23.339107] [drm] Loading R200 Microcode
[   23.339155] [drm] writeback test succeeded in 1 usecs
[   25.874555] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   36.648031] eth0: no IPv6 routers present
[  339.978251] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  339.982503] usbcore: registered new interface driver ndiswrapper
[ 2382.003216] exaile[5972]: segfault at 33 ip b7674660 sp bf879240 error 4 in libgtk-x11-2.0.so.0.1600.1[b743f000+3a9000]
[ 2640.558313] type=1505 audit(1249991571.682:10): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=6670
[ 2640.647744] type=1505 audit(1249991571.770:11): operation="profile_replace" name="/sbin/dhclient-script" name2="default" pid=6674
[ 2640.648841] type=1505 audit(1249991571.774:12): operation="profile_replace" name="/sbin/dhclient3" name2="default" pid=6674
[ 2640.649000] type=1505 audit(1249991571.774:13): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=6674
[ 2640.649128] type=1505 audit(1249991571.774:14): operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=6674
[ 2640.717433] type=1505 audit(1249991571.842:15): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=6679
[ 2640.943053] type=1505 audit(1249991572.066:16): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=6683
[ 2640.943653] type=1505 audit(1249991572.066:17): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=6683
[ 2641.007853] type=1505 audit(1249991572.130:18): operation="profile_replace" name="/usr/sbin/tcpdump" name2="default" pid=6687
[ 2897.694583] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 2897.737249] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[ 2897.737589] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[ 2897.737595] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[ 2897.737597] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[ 3363.742005] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 3384.992050] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 3384.992102] pci 0000:03:00.0: reg 10 32bit mmio: [0xd0000000-0xd000ffff]
[ 3384.992112] pci 0000:03:00.0: reg 14 32bit mmio: [0xc0000000-0xc000ffff]
[ 3384.992191] yenta_cardbus 0000:02:04.0: EnE: chaning testregister 0xC9, 04 -> 04
[ 6181.883168] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[ 6416.273462] UDF-fs: No VRS found
[ 6416.315975] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 6416.402157] ISO 9660 Extensions: RRIP_1991A
[ 9952.944053] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 9952.944105] pci 0000:03:00.0: reg 10 32bit mmio: [0xd0000000-0xd000ffff]
[ 9952.944115] pci 0000:03:00.0: reg 14 32bit mmio: [0xc0000000-0xc000ffff]
[ 9952.944195] yenta_cardbus 0000:02:04.0: EnE: chaning testregister 0xC9, 04 -> 04
[15187.387119] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[15199.180048] pcmcia_socket pcmcia_socket0: cs: unable to apply power.
[15199.956058] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[15199.956110] pci 0000:03:00.0: reg 10 32bit mmio: [0xd0000000-0xd000ffff]
[15199.956120] pci 0000:03:00.0: reg 14 32bit mmio: [0xc0000000-0xc000ffff]
[15199.956199] yenta_cardbus 0000:02:04.0: EnE: chaning testregister 0xC9, 04 -> 04

```

---

### Post by tgalati4 on 2009-08-11
The yenta pcmcia cardbus recognizes that a card is inserted, but that's it.

How old is the laptop that this is going into?  Perhaps there is a pcmcia driver problem (16-bit vs 32-bit?).  I know that older laptops can only support 16-bit cards and all newer pcmcia cards are 32-bit.

Windows drivers may handle this better.


My WG511U card is a few years old.  It's also made in China, but shows up in dmesg as the correct card and the ath5k driver loads automatically.

What happens when you do the following:

sudo modprobe ath5k

---

### Post by Jack Bonner on 2009-08-11
> **tgalati4 said:**
> The yenta pcmcia cardbus recognizes that a card is inserted, but that's it.

How old is the laptop that this is going into?  Perhaps there is a pcmcia driver problem (16-bit vs 32-bit?).  I know that older laptops can only support 16-bit cards and all newer pcmcia cards are 32-bit.

Windows drivers may handle this better.


My WG511U card is a few years old.  It's also made in China, but shows up in dmesg as the correct card and the ath5k driver loads automatically.

What happens when you do the following:

sudo modprobe ath5k

The card is fine. I had it working this morning under windows, the laptop isn't that old. It's an Acer TravelMate 2200. So I know that the card will work in the PCMCIA slot. 'sudo modprobe ath5k' doesn't give an output as it's not an atheros chip in the card. I know people have had these cards working, I just can't extract the drivers from either the install disk or from the downloaded driver installer exe from Netgear. That's what I want to know how to do. The methods I have tried do not work.

---

### Post by Jack Bonner on 2009-08-12
Okay, I got the thing working after finding a post about it on Slackware and adapting it to Ubuntu, now my only problem is that it won't connect to any wireless networks, even though the Password is correct and it finds the networks fine.

Any ideas?

---

