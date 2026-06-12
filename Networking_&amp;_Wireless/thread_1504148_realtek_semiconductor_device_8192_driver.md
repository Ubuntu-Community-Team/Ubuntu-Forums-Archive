---
title: "realtek semiconductor device 8192 driver"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by Thomas Humphrey on 2010-06-07
I've just installed Ubuntu 10.04 on my samsung n150. It has the 8192 device in it.

Reading about have seen that it is a nightmare to get going.

Have installed ndiswrapper, however cannot get the drivers for it.

Was wondering if anyone knew how to fix/where to get the driver from so i can get my wireless card working again. 

on lspci:

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller


NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xE
  State:             unavailable
  Default:           no
  HW Address:        B4:82:FE:5D:F3:97

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:24:54:85:45:25

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.85
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

 *-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: b4:82:fe:5d:f3:97
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff


I think the driver may be there, however I just can't 'enable' it. On my laptop there is a blue light saying that wifi is enabled however who knows. any advice would be much appreciated. Oh and i am currently using a wired connection to post this.

---

### Post by chili555 on 2010-06-07
Let's see if the kernel has anything interesting to say about this. Please post:```
dmesg | grep 819
```Thanks.

---

### Post by Thomas Humphrey on 2010-06-08
I've managed to get it working with an old driver (i think v14) however it is very temperamental and never stays connected for long so am back on the wired connection.

This was the output to that code

[  734.804078] =====>rtl8192_set_chan()====ch:4
[  734.820074] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  734.820090] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  734.924076] =====>rtl8192_set_chan()====ch:5
[  734.940092] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  734.940109] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.044090] =====>rtl8192_set_chan()====ch:6
[  735.060070] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.060086] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.164066] =====>rtl8192_set_chan()====ch:7
[  735.180067] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.180084] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.284079] =====>rtl8192_set_chan()====ch:8
[  735.300083] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.300100] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.405059] =====>rtl8192_set_chan()====ch:9
[  735.421066] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.421083] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.524080] =====>rtl8192_set_chan()====ch:10
[  735.540078] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.540095] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.644076] =====>rtl8192_set_chan()====ch:11
[  735.660068] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.660084] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  735.764079] =====>rtl8192_set_chan()====ch:12
[  735.884072] =====>rtl8192_set_chan()====ch:13
[  736.004090] =====>rtl8192_set_chan()====ch:10
[  736.020584] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  736.031882] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  736.031898] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  736.084209] =====>rtl8192_set_chan()====ch:1
[  736.100079] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.100096] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.204113] =====>rtl8192_set_chan()====ch:2
[  736.220121] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.220138] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.324052] =====>rtl8192_set_chan()====ch:3
[  736.340118] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.340137] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.444080] =====>rtl8192_set_chan()====ch:4
[  736.460081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.460109] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.564077] =====>rtl8192_set_chan()====ch:5
[  736.581161] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.581178] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.684082] =====>rtl8192_set_chan()====ch:6
[  736.700082] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.700100] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.804069] =====>rtl8192_set_chan()====ch:7
[  736.820070] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.820081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.925061] =====>rtl8192_set_chan()====ch:8
[  736.940079] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  736.940093] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.048088] =====>rtl8192_set_chan()====ch:9
[  737.061242] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.061256] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.164076] =====>rtl8192_set_chan()====ch:10
[  737.180060] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.180071] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.284121] =====>rtl8192_set_chan()====ch:11
[  737.300060] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.300077] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.404138] =====>rtl8192_set_chan()====ch:12
[  737.524060] =====>rtl8192_set_chan()====ch:13
[  737.644059] =====>rtl8192_set_chan()====ch:10
[  737.660585] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  737.675503] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  737.675527] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  737.729173] =====>rtl8192_set_chan()====ch:1
[  737.745053] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.745071] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.848084] =====>rtl8192_set_chan()====ch:2
[  737.864073] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.864091] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.968100] =====>rtl8192_set_chan()====ch:3
[  737.985059] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  737.985076] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.089042] =====>rtl8192_set_chan()====ch:4
[  738.104738] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.104753] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.209044] =====>rtl8192_set_chan()====ch:5
[  738.224061] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.224080] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.329050] =====>rtl8192_set_chan()====ch:6
[  738.344087] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.344105] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.449053] =====>rtl8192_set_chan()====ch:7
[  738.465050] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.465069] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.568069] =====>rtl8192_set_chan()====ch:8
[  738.584063] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.584080] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.689100] =====>rtl8192_set_chan()====ch:9
[  738.705052] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.705070] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.808147] =====>rtl8192_set_chan()====ch:10
[  738.824151] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.824167] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.929432] =====>rtl8192_set_chan()====ch:11
[  738.944925] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  738.944949] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.049076] =====>rtl8192_set_chan()====ch:12
[  739.168740] =====>rtl8192_set_chan()====ch:13
[  739.289127] =====>rtl8192_set_chan()====ch:10
[  739.305592] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  739.319598] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  739.319612] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  739.372197] =====>rtl8192_set_chan()====ch:1
[  739.389525] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.389549] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.492035] =====>rtl8192_set_chan()====ch:2
[  739.508069] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.508081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.612040] =====>rtl8192_set_chan()====ch:3
[  739.628069] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.628080] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.732051] =====>rtl8192_set_chan()====ch:4
[  739.748066] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.748078] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.855053] =====>rtl8192_set_chan()====ch:5
[  739.869303] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.869318] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.972082] =====>rtl8192_set_chan()====ch:6
[  739.988066] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  739.988085] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.092078] =====>rtl8192_set_chan()====ch:7
[  740.108094] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.108111] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.212047] =====>rtl8192_set_chan()====ch:8
[  740.228054] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.228066] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.332073] =====>rtl8192_set_chan()====ch:9
[  740.348224] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.348240] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.456085] =====>rtl8192_set_chan()====ch:10
[  740.469130] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.469147] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.576062] =====>rtl8192_set_chan()====ch:11
[  740.590472] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.590486] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  740.692110] =====>rtl8192_set_chan()====ch:12
[  740.812111] =====>rtl8192_set_chan()====ch:13
[  740.932116] =====>rtl8192_set_chan()====ch:10
[  740.948584] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  740.975560] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  740.975574] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  741.029169] =====>rtl8192_set_chan()====ch:1
[  741.045071] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.045083] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.148526] =====>rtl8192_set_chan()====ch:2
[  741.164149] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.164166] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.268109] =====>rtl8192_set_chan()====ch:3
[  741.285078] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.285096] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.389074] =====>rtl8192_set_chan()====ch:4
[  741.404910] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.404933] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.509049] =====>rtl8192_set_chan()====ch:5
[  741.524061] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.524079] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.628076] =====>rtl8192_set_chan()====ch:6
[  741.644085] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.644103] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.748079] =====>rtl8192_set_chan()====ch:7
[  741.764087] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.764108] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.869054] =====>rtl8192_set_chan()====ch:8
[  741.885065] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.885083] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  741.988363] =====>rtl8192_set_chan()====ch:9
[  742.005138] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.005163] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.109090] =====>rtl8192_set_chan()====ch:10
[  742.125115] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.125138] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.229076] =====>rtl8192_set_chan()====ch:11
[  742.245071] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.245085] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.348071] =====>rtl8192_set_chan()====ch:12
[  742.468091] =====>rtl8192_set_chan()====ch:13
[  742.589110] =====>rtl8192_set_chan()====ch:10
[  742.605366] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  742.614339] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  742.614353] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  742.669178] =====>rtl8192_set_chan()====ch:1
[  742.685432] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.685451] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.788133] =====>rtl8192_set_chan()====ch:2
[  742.804083] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.804100] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.908084] =====>rtl8192_set_chan()====ch:3
[  742.924073] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  742.924089] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.028083] =====>rtl8192_set_chan()====ch:4
[  743.044095] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.044113] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.149058] =====>rtl8192_set_chan()====ch:5
[  743.164607] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.164632] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.268500] =====>rtl8192_set_chan()====ch:6
[  743.285063] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.285075] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.389081] =====>rtl8192_set_chan()====ch:7
[  743.404134] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.404157] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.508074] =====>rtl8192_set_chan()====ch:8
[  743.524078] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.524095] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.629054] =====>rtl8192_set_chan()====ch:9
[  743.645053] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.645070] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.749079] =====>rtl8192_set_chan()====ch:10
[  743.764589] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.764607] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.868095] =====>rtl8192_set_chan()====ch:11
[  743.885116] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.885134] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  743.989089] =====>rtl8192_set_chan()====ch:12
[  744.109082] =====>rtl8192_set_chan()====ch:13
[  744.229081] =====>rtl8192_set_chan()====ch:10
[  744.245576] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  744.254356] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  744.254371] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  744.309187] =====>rtl8192_set_chan()====ch:1
[  744.325124] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.325145] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.429062] =====>rtl8192_set_chan()====ch:2
[  744.445064] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.445077] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.549065] =====>rtl8192_set_chan()====ch:3
[  744.564095] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.564113] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.669091] =====>rtl8192_set_chan()====ch:4
[  744.685069] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.685081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.789056] =====>rtl8192_set_chan()====ch:5
[  744.805087] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.805101] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.909096] =====>rtl8192_set_chan()====ch:6
[  744.925100] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  744.925116] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.029039] =====>rtl8192_set_chan()====ch:7
[  745.045076] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.045094] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.148128] =====>rtl8192_set_chan()====ch:8
[  745.165088] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.165099] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.269055] =====>rtl8192_set_chan()====ch:9
[  745.285056] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.285067] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.389093] =====>rtl8192_set_chan()====ch:10
[  745.405075] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.405092] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.509067] =====>rtl8192_set_chan()====ch:11
[  745.525105] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.525124] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.629060] =====>rtl8192_set_chan()====ch:12
[  745.748067] =====>rtl8192_set_chan()====ch:13
[  745.868115] =====>rtl8192_set_chan()====ch:10
[  745.885584] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  745.901607] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  745.901621] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  745.956175] =====>rtl8192_set_chan()====ch:1
[  745.972076] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  745.972093] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.076078] =====>rtl8192_set_chan()====ch:2
[  746.092092] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.092110] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.196059] =====>rtl8192_set_chan()====ch:3
[  746.212093] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.212110] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.316072] =====>rtl8192_set_chan()====ch:4
[  746.332093] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.332111] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.436618] =====>rtl8192_set_chan()====ch:5
[  746.452085] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.452102] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.556085] =====>rtl8192_set_chan()====ch:6
[  746.572090] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.572108] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.676156] =====>rtl8192_set_chan()====ch:7
[  746.692057] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.692075] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.796078] =====>rtl8192_set_chan()====ch:8
[  746.812071] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.812088] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.916072] =====>rtl8192_set_chan()====ch:9
[  746.932086] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  746.932104] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.036074] =====>rtl8192_set_chan()====ch:10
[  747.052094] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.052112] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.156058] =====>rtl8192_set_chan()====ch:11
[  747.172079] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.172096] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.276082] =====>rtl8192_set_chan()====ch:12
[  747.396106] =====>rtl8192_set_chan()====ch:13
[  747.516069] =====>rtl8192_set_chan()====ch:10
[  747.532792] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  747.546017] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  747.546030] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  747.600175] =====>rtl8192_set_chan()====ch:1
[  747.616325] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.616350] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.720060] =====>rtl8192_set_chan()====ch:2
[  747.736079] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.736097] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.840063] =====>rtl8192_set_chan()====ch:3
[  747.856294] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.856312] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.960085] =====>rtl8192_set_chan()====ch:4
[  747.976065] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  747.976083] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.080072] =====>rtl8192_set_chan()====ch:5
[  748.096079] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.096096] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.200053] =====>rtl8192_set_chan()====ch:6
[  748.216100] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.216118] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.320045] =====>rtl8192_set_chan()====ch:7
[  748.336081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.336099] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.440073] =====>rtl8192_set_chan()====ch:8
[  748.456086] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.456104] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.560081] =====>rtl8192_set_chan()====ch:9
[  748.576055] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.576071] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.680079] =====>rtl8192_set_chan()====ch:10
[  748.696104] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.696121] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.800102] =====>rtl8192_set_chan()====ch:11
[  748.816076] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.816093] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  748.920068] =====>rtl8192_set_chan()====ch:12
[  749.040061] =====>rtl8192_set_chan()====ch:13
[  749.160083] =====>rtl8192_set_chan()====ch:10
[  749.176607] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  749.188331] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  749.188341] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  749.245185] =====>rtl8192_set_chan()====ch:1
[  749.260077] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.260094] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.364084] =====>rtl8192_set_chan()====ch:2
[  749.380084] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.380101] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.484087] =====>rtl8192_set_chan()====ch:3
[  749.501109] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.501133] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.605054] =====>rtl8192_set_chan()====ch:4
[  749.620085] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.620103] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.725095] =====>rtl8192_set_chan()====ch:5
[  749.741058] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.741076] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.844073] =====>rtl8192_set_chan()====ch:6
[  749.860095] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.860113] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.964080] =====>rtl8192_set_chan()====ch:7
[  749.981059] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  749.981077] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.084065] =====>rtl8192_set_chan()====ch:8
[  750.100120] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.100144] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.205051] =====>rtl8192_set_chan()====ch:9
[  750.220956] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.220980] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.324057] =====>rtl8192_set_chan()====ch:10
[  750.340091] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.340108] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.445075] =====>rtl8192_set_chan()====ch:11
[  750.461088] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.461105] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.565048] =====>rtl8192_set_chan()====ch:12
[  750.684060] =====>rtl8192_set_chan()====ch:13
[  750.805086] =====>rtl8192_set_chan()====ch:10
[  750.821638] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  750.834127] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  750.834141] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  750.889160] =====>rtl8192_set_chan()====ch:1
[  750.904078] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  750.904095] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.009100] =====>rtl8192_set_chan()====ch:2
[  751.024084] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.024101] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.129090] =====>rtl8192_set_chan()====ch:3
[  751.145062] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.145080] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.248075] =====>rtl8192_set_chan()====ch:4
[  751.265054] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.265072] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.368067] =====>rtl8192_set_chan()====ch:5
[  751.384090] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.384108] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.488083] =====>rtl8192_set_chan()====ch:6
[  751.504074] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.504091] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.608070] =====>rtl8192_set_chan()====ch:7
[  751.624078] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.624094] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.728177] =====>rtl8192_set_chan()====ch:8
[  751.744083] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.744100] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.849050] =====>rtl8192_set_chan()====ch:9
[  751.865050] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.865066] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.969075] =====>rtl8192_set_chan()====ch:10
[  751.984086] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  751.984102] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.088095] =====>rtl8192_set_chan()====ch:11
[  752.104092] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.104109] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.208082] =====>rtl8192_set_chan()====ch:12
[  752.328078] =====>rtl8192_set_chan()====ch:13
[  752.448105] =====>rtl8192_set_chan()====ch:10
[  752.464613] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  752.476570] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  752.476587] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  752.529392] =====>rtl8192_set_chan()====ch:1
[  752.545081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.545097] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.649059] =====>rtl8192_set_chan()====ch:2
[  752.665051] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.665062] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.768063] =====>rtl8192_set_chan()====ch:3
[  752.784095] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.784112] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.889046] =====>rtl8192_set_chan()====ch:4
[  752.905074] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  752.905093] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.009047] =====>rtl8192_set_chan()====ch:5
[  753.024102] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.024127] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.128089] =====>rtl8192_set_chan()====ch:6
[  753.144103] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.144121] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.248081] =====>rtl8192_set_chan()====ch:7
[  753.265071] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.265089] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.368085] =====>rtl8192_set_chan()====ch:8
[  753.384075] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.384092] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.489065] =====>rtl8192_set_chan()====ch:9
[  753.505066] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.505082] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.608069] =====>rtl8192_set_chan()====ch:10
[  753.624085] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.624103] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.728063] =====>rtl8192_set_chan()====ch:11
[  753.744105] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.744123] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  753.848075] =====>rtl8192_set_chan()====ch:12
[  753.969044] =====>rtl8192_set_chan()====ch:13
[  754.089060] =====>rtl8192_set_chan()====ch:10
[  754.104597] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  754.117064] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  754.117081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  754.172205] =====>rtl8192_set_chan()====ch:1
[  754.188096] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.188114] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.293063] =====>rtl8192_set_chan()====ch:2
[  754.309084] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.309102] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.412091] =====>rtl8192_set_chan()====ch:3
[  754.428081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.428098] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.532060] =====>rtl8192_set_chan()====ch:4
[  754.548073] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.548091] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.652084] =====>rtl8192_set_chan()====ch:5
[  754.668099] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.668117] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.772091] =====>rtl8192_set_chan()====ch:6
[  754.789081] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.789098] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.892066] =====>rtl8192_set_chan()====ch:7
[  754.909073] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  754.909091] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.012085] =====>rtl8192_set_chan()====ch:8
[  755.028091] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.028108] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.133042] =====>rtl8192_set_chan()====ch:9
[  755.149071] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.149088] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.252088] =====>rtl8192_set_chan()====ch:10
[  755.269126] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.269150] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.372062] =====>rtl8192_set_chan()====ch:11
[  755.388080] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.388097] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.492082] =====>rtl8192_set_chan()====ch:12
[  755.613043] =====>rtl8192_set_chan()====ch:13
[  755.732073] =====>rtl8192_set_chan()====ch:10
[  755.748591] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  755.759768] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  755.759784] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x20 queuelen=0
[  755.812192] =====>rtl8192_set_chan()====ch:1
[  755.828055] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.828072] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.932075] =====>rtl8192_set_chan()====ch:2
[  755.948076] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  755.948093] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  756.052082] =====>rtl8192_set_chan()====ch:3
[  756.068086] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  756.068104] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  756.172094] =====>rtl8192_set_chan()====ch:4
[  756.188080] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  756.188097] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x39 queuelen=0
[  756.292126] =====>rtl8192_set_chan()====ch:5

---

### Post by Thomas Humphrey on 2010-06-09
Everythings seems to have started working. No idea why

Thanks anyway

---

