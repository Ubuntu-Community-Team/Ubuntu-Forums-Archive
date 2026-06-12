---
title: "Intel (iwlagn) gnome problems"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by happyface_0 on 2010-02-14
Hi,
my wireless has been working fine in Ubuntu (9.10) x64 until recently.
nm-applet says "wireless is disabled" and right-clicking on it doesn't allow me to check "enable wireless".

```
dave@dave-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"****"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

dave@dave-ubuntu:~$ lspci |grep -i net
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
dave@dave-ubuntu:~$ dmesg | grep iwlagn
[   24.030352] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   24.030361] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   24.031436] iwlagn 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.031464] iwlagn 0000:0b:00.0: setting latency timer to 64
[   24.031597] iwlagn 0000:0b:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   24.080774] iwlagn 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   24.080870] iwlagn 0000:0b:00.0: irq 30 for MSI/MSI-X
[  289.439688] iwlagn 0000:0b:00.0: RF_KILL bit toggled to disable radio.
[  296.368194] iwlagn 0000:0b:00.0: RF_KILL bit toggled to enable radio.
[  296.369747] iwlagn 0000:0b:00.0: firmware: requesting lbm-iwlwifi-4965-2.ucode
[  296.395002] iwlagn 0000:0b:00.0: loaded firmware version 228.61.2.24
[  546.632957] iwlagn 0000:0b:00.0: RF_KILL bit toggled to disable radio.
[  549.473981] iwlagn 0000:0b:00.0: RF_KILL bit toggled to enable radio.
dave@dave-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:44:b1:1c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.123 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f1ffc000-f1ffffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:31:09:e1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f1efe000-f1efffff
```

Thanks for any help on getting wifi working again!

---

### Post by Abhijit Navale on 2010-02-14
I have EXACTLY the same problem. But when I press wifi button then nothing happens. It remain off (red) only. 

and my iwconfig output wireless is DISABLED.
anyone have solution?

---

### Post by happyface_0 on 2010-02-14
It works again, wow this is a sporadic problem.

---

