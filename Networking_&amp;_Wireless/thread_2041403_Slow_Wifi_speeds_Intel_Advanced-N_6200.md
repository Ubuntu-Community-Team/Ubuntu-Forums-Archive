---
title: "Slow Wifi speeds Intel Advanced-N 6200"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by danbrownlow on 2012-08-12
Hey, a few days ago we had some problems with my friends hard drive. We eventually got the data back and got a new drive, installed it and then installed Ubuntu 12.04 :)

Well, now we have the problem that the Wifi is running unbelievable slow, like and hour to apt-get upgrade. The funny thing is, we've never had this problem before.

Results from various commands I saw people asking to show:

dmesg | grep iwl - 
```

[    8.994156] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.994187] iwlwifi 0000:02:00.0: setting latency timer to 64
[    8.994216] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[    8.994218] iwlwifi 0000:02:00.0: pci_resource_base = f847c000
[    8.994220] iwlwifi 0000:02:00.0: HW Revision ID = 0x35
[    8.994474] iwlwifi 0000:02:00.0: irq 43 for MSI/MSI-X
[    8.994570] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[    8.994678] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    9.011399] iwlwifi 0000:02:00.0: device EEPROM VER=0x436, CALIB=0x6
[    9.011401] iwlwifi 0000:02:00.0: Device SKU: 0X1f0
[    9.012158] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.394355] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[    9.693859] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.943458] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   18.949695] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[   19.184020] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   19.190233] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[  110.498789] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  176.125431] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  238.556629] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  288.627876] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  300.858585] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  317.728978] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  375.947857] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  446.192854] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  565.818230] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  609.339087] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  817.479246] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  847.692848] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  916.873898] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  933.363104] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[  979.269815] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1011.078644] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1084.841624] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1120.343565] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1194.545288] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1229.058194] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1244.559469] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1286.412804] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1324.063480] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1364.155790] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1409.698338] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1426.802954] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1474.550462] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1491.407027] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1532.368640] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1555.962485] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 6
[ 1613.749835] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1643.348877] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 1755.983294] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f4:ca:e5:b4:ca:bd tid = 0
[ 5017.646586] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 62:a1:d7:44:af:b5 tid = 0
[ 5219.583987] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 62:a1:d7:44:af:b5 tid = 0


```

rfkill list all - 

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

lspci - 
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```

lspci -nn | grep 0280 - 
```

02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)


```

The odd thing is, Ubuntu worked straight out of the box (so to speak) before, so I'm a bit confused as to why it's not working now.

Thanks.

---

### Post by praseodym on 2012-08-12
Hi,

deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

