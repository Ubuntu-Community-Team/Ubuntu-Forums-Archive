---
title: "intel wifi 5100 on vostro 1320 - can see it but wireless not working, iwlagn issue?"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by ibbers on 2011-04-03
After brand new install, I was unable to enable wireless from the toolbar - there was an option, but it was greyed out.  I've already tried a fresh reinstall of Ubuntu to no avail, and this second time tried digging a bit deeper.

I've since tried uninstalling the broadcom driver, and then reinstalling it, but to no avail (the uninstall just caused the greyed out wireless option to disappear, and reinstalling has not restored it).  I keep reading that the iwlagn is the appropriate driver, and it is even mentioned in some of my command line commands, but it doesn't come up at all in synaptics.

The 'wireless' (search in synaptics) components installed are:  bcmwl-kernel-source, bcmwl-modaliases, libiw30, libopenobex1, network-manager-pptp, network-manager-pptp-gnome, pcmciautils, wireless-crda, wireless-tools, wpasupplicant.

the one thing i haven't tried is installing with an internet connection up - would that make a difference (in terms of finding the right drivers at the beginning)?

or is there something i need to do to get iwlagn working?

many thanks - i've fixed my own issues in ubuntu many times before, but i'm stumped on this one.  i've been using my work mobile broadband stick, but can't keep using it due to data limitations!

Jon




commands (from forum sticky on new wireless issue posts):

1.  Brand/Model

Dell Vostro 1320

2.  lspci:  

0e:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]

lsusb:

Bus 008 Device 006: ID 0a5c:4503 Broadcom Corp. 
Bus 008 Device 005: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 008 Device 004: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 008 Device 003: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 008 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 1199:68a3 Sierra Wireless, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

3. 

ifconfig:  only gives result for eth0, lo and PPP0 (3g card).  No wlan.

iwconfig:  lo, eth0, wwan0, ppp0 - no wireless extensions.

4.

jon@jon-Vostro-1320:~$ lsmod | grep Intel - nothing.

5.

jon@jon-Vostro-1320:~$ dmesg | grep Intel
[    0.000000] ACPI: DSDT bfde9000 06318 (v02 Intel  CANTIGA  06040000 INTL 20060608)
[    0.004265] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.062010] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
[   12.476594] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.476655] HDA Intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   12.476683] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.569564] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.569766] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9


6.sudo lshw -C network

  *-network UNCLAIMED
       description: Network controller
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6001fff

7.  iwlist scan - lo, eth0, wwan0, ppp0 - doesn't supporting scanning.

8.  lsb_release -d
Description:	Ubuntu 10.10

9.  uname -mr
2.6.35-28-generic i686

10.  sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                      Ignoring unknown interface ppp0=ppp0.

---

### Post by wildmanne39 on 2012-07-07
Old thread closed.

---

