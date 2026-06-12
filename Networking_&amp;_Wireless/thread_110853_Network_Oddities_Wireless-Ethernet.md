---
title: "Network Oddities Wireless-Ethernet"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by mrhaffer on 2005-12-31
I have an odd problem.  I did a default install and have both a wireless and ethernet ISA card.  Neither card worked although both work in Windows 98.  If I do a recovery boot, log in as root and do modprobe ne, my isa card is found.  I use System>admin>networking to configure and activate.  But this is not a  permanent fix.  I have to do the same thing every time I boot.  The wireless card shows up in lshw with a prism2 driver but prism2 doesn't show in lsmod | grep prism2 so it must not be loaded.  the Networking table shows a wifi0 ? which doesn't appear in the hardware and also wlan0 which shows in lshw -C Network as *Network -DISABLED Wireless network interface.  I tried to do a modprobe prism2 but it says FAULT: Not found.  I would like to not have to reboot the ethernet card every time.  Attached is the dmesg output. I tried to edit but didn't want to miss something.
[  126.443519] hostap_pci: Registered netdevice wifi0
[  126.443629] wifi0: Original COR value: 0x1f
[  126.948184] hostap_pci: assuming no Primary image in flash - card initializat ion not completed
[  126.948217] wifi0: test Genesis mode with HCR 0x1f
[  126.948236] wifi0: Original COR value: 0x0
[  126.981892] Readback test failed, HCR 0x1f write 00 e1 a1 ff read 00 ce a1 ce
[  126.981913] wifi0: test Genesis mode with HCR 0x0f
[  126.981929] wifi0: Original COR value: 0xa1
[  127.015521] Readback test succeeded, HCR 0x0f
[  127.045142] wifi0: Intersil Prism2.5 PCI: mem=0xfedff000, irq=11
[  127.077126] wifi0: registered netdevice wlan0
[  132.509168] Real Time Clock Driver v1.12
[  133.267033] input: PC Speaker
[  134.797811] Floppy drive(s): fd0 is 1.44M
[  134.812344] FDC 0 is a National Semiconductor PC87306
[  136.852355] ts: Compaq touchscreen protocol output
[  140.797954] NET: Registered protocol family 17
[  141.933024] prism2: wlan0: operating mode changed 3 -> 2
[  141.933053] wlan0: cannot set RID fc00 (len=2) - no PRI f/w
[  141.947110] wlan0: cannot set RID fc02 (len=34) - no PRI f/w
[  142.051735] wlan0: could not set interface UP - no PRI f/w
[  142.051774] wlan0: could not set interface UP - no PRI f/w
[  165.739230] pnp: Device 01:01.00 activated.
[  165.739299] ne.c: ISAPnP reports Generic PNP at i/o 0x240, irq 5.
[  165.739368] ne.c:v1.10 9/23/94 Donald Becker (becker@scyld.com)
[  165.739380] Last modified Nov 1, 2000 by Paul Gortmaker
[  165.739466] NE*000 ethercard probe at 0x240: 00 40 05 5f 0d 44
[  165.739634] eth%d: NE2000 found at 0x240, using IRQ 5.
[  203.467149] capifs: Rev 1.1.2.3
[  231.354423] NET: Registered protocol family 10
[  231.355019] Disabled Privacy Extensions on device c02eb280(lo)
[  231.355457] IPv6 over IPv4 tunneling driver
[  324.004312] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.005449] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[  324.006243] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[  324.007055] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.007957] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[  324.008712] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[  324.009515] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[  324.010297] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[  324.011240] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[  324.012021] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[  324.012771] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[  324.013560] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[  324.014492] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.015285] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[  324.016070] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[  324.016837] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.017621] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[  324.018394] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[  324.019171] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[  324.019947] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[  324.020696] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[  324.021474] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[  324.022435] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[  324.023216] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[  324.072758] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.073827] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[  324.074625] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[  324.075435] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.076314] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[  324.077099] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[  324.077853] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[  324.078665] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[  324.079441] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[  324.080219] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[  324.080969] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[  324.081751] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[  324.082672] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.083470] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[  324.084255] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[  324.085176] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.086055] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[  324.086805] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[  324.087584] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[  324.088507] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[  324.089276] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[  324.090048] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[  324.090796] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[  324.091577] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[  324.139213] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.140461] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[  324.141391] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[  324.142203] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[  324.143059] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[  324.143837] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[  324.144617] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[  324.145396] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[  324.146168] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[  324.146919] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[  324.147696] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[  324.148483] wifi0: cannot get RID fd48 (len=2) - no PRI f/w

---

