---
title: "Atheros Card: Blacklisting?"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by Nohtanhoj on 2009-11-28
I've been following the tutorial on [this]("http://ubuntuforums.org/showthread.php?t=1309072") thread to try to configure my Samsung NC20's wireless card.... The part that confuses me is the various blacklisting of the ath5k and ath9k drivers. I have no problem with messing with this stuff (I actually quite like it, I learn a lot about how systems work), but I'm not sure what effect this has. 

I ran an lspci -v and the output for my ethernet section looks like this.

mark@mark-nc20:/etc/modprobe.d$ sudo lspci -v

01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7130
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f5000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Kernel driver in use: ath_pci
    Kernel modules: ath_pci, ath5k

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
    Subsystem: Samsung Electronics Co Ltd Device c04e
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f5100000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 5000 [size=256]
    Capabilities: [48] Power Management version 3
    Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [c0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [130] Device Serial Number 00-13-77-ff-ff-e6-30-7c
    Kernel driver in use: sky2
    Kernel modules: sky2

From what I can see, my wireless card is still using the ath5k driver (from looking at the Kernel Modules output). I have blacklisted that driver inside the /etc/modprobe.d directory in various files, and have deleted all references to blacklisting ath_pci (it seems that tutorial wants you to use that driver). How can I get this driver truly blacklisted?

Wicd still shows zero wireless connections. Any ideas??

---

### Post by drpjkurian on 2009-11-28
Hi
Your wireless card appears to be an Atheros. Well i would like to suggest you to install madwifi drivers for your card which is robust. I was using it since Hardy heron. You can visit my thread to make your wireless alive

The thread is [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

### Post by Nohtanhoj on 2009-12-01
Fixed it. All I needed to do was blacklist the driver in the blacklist.conf file. Apparently I forgot to do so.

=D =D

---

### Post by drpjkurian on 2009-12-03
> **Nohtanhoj said:**
> Fixed it. All I needed to do was blacklist the driver in the blacklist.conf file. Apparently I forgot to do so.

=D =D
HI

Is your card back to life again, Is it working alright?
Well  the blacklisting commands are included in my Howto.

With regards
Dr Kurian

---

