---
title: "Wireless icon showing red mark and not activated"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by sanoop1 on 2010-05-30
I wanted to get away from windows, because of the helll lot of issues it gave me. I installed ubuntu in my machine, and i am facing lot of issues to activate internet. May be I am fool number one. So need some help from experts.
 
FIrst my hardware details :-
 
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
        Subsystem: Hewlett-Packard Company Device 1508
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb
 
I have gone thru  lot of websites and forums to try to enable the wireless connections. Till now I have installed the ndisgtk_0.8.5-1_i386.deb, ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb & ndiswrapper-common_1.54-2ubuntu1_all.deb. Then I was able to install the windows driver for my wireless card. But still the status is showing as disabled for the wireless adaptor. Please help to make it working.

---

### Post by Iowan on 2010-05-30
*Ordinarily* I'd suspect the interface got defined in */etc/network/interfaces* and NM is ignoring it, but there are a couple of other, similar threads... Still, verify that */etc/network/interfaces* contains only two lines defining "lo".

---

### Post by sanoop1 on 2010-05-30
> **Iowan said:**
> *Ordinarily* I'd suspect the interface got defined in */etc/network/interfaces* and NM is ignoring it, but there are a couple of other, similar threads... Still, verify that */etc/network/interfaces* contains only two lines defining "lo".
 
 
These are the only lines in the interfaces
 
auto lo
iface lo inet loopback

---

### Post by sm4sh1t on 2010-05-30
> **sanoop1 said:**
> I wanted to get away from windows, because of the helll lot of issues it gave me. I installed ubuntu in my machine, and i am facing lot of issues to activate internet. May be I am fool number one. So need some help from experts.
 
FIrst my hardware details :-
 
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
        Subsystem: Hewlett-Packard Company Device 1508
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb
 
I have gone thru  lot of websites and forums to try to enable the wireless connections. Till now I have installed the ndisgtk_0.8.5-1_i386.deb, ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb & ndiswrapper-common_1.54-2ubuntu1_all.deb. Then I was able to install the windows driver for my wireless card. But still the status is showing as disabled for the wireless adaptor. Please help to make it working.

try installing wicd from the synaptic manager, it solved it for me :)

---

