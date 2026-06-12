---
title: "Ubuntu Koala - no wireless networks showing"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by antiphos on 2010-02-15
I have been working on this problem for a while but might be narrowing the options. This is an HP laptop running Ubuntu Koala. Until last week, the wireless had been working perfectly but suddenly it lost the wireless connection (to a Bell modem/wireless router) and all local wireless networks had disappeared. These two command listings below may hold a key but I know nothing about wireless and not much about Ubuntu. What seems odd is that "lshw" shows the wireless interface as logical name "wmaster0" but the iwconfig shows a "wlan1" as the wireless. The ethernet wired interface shows as "eth1" on both commands. Could this be causing the problem.  Also, I was wondering what the "ACPI handle has no context" means. 

garry@garry-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:27:05:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:f4000000-f4000fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:1b:24:c3:78:94
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:c000(size=256) memory:f8200000-f8200fff memory:80000000-8001ffff(prefetchable)

garry@garry-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-------------------------------------------------------------
dmesg shows wireless sleeping:
[ 1841.389051] ACPI handle has no context!
  [ 1841.390127] ACPI handle has no context!
  [ 1841.390134] sdhci-pci 0000:09:09.1: PME# disabled
  [ 1841.390142] sdhci-pci 0000:09:09.1: PCI INT B disabled
  [ 1841.390150] ACPI handle has no context!
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.428465] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
  [ 1841.664647] iwl3945 0000:02:00.0: Microcode HW error detected.  Restarting.
  [ 1841.884726] ata_piix 0000:00:1f.1: PCI INT A disabled
  [ 1841.988595] HDA Intel 0000:00:1b.0: PCI INT A disabled

---

### Post by antiphos on 2010-02-15
I cannot say the problem is resolved but as mysteriously as it disappeared, the wireless connection has reappeared, so I guess for now no answer is necessary.

---

