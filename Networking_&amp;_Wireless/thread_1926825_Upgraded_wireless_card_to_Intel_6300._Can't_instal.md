---
title: "Upgraded wireless card to Intel 6300. Can't install drivers."
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by sreezon on 2012-02-17
Hello,

I used to use a broadcom wireless card that worked. Then I upgraded the card to the Intel 6300 wireless card. I can't seem to get it to work. I copied iwlwifi-6000-ucode-9.221.4.1 into lib/firmware but nothing happens. 

```

@M11x-R2:~$ uname -mr
3.0.0-16-generic x86_64

```

```

@M11x-R2:~$ dmesg | egrep 'iwl|switch|radio|kill|wmi'
[    3.449102] wmi: Mapper loaded
[    4.761114] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    4.761121] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    4.761612] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.761626] iwlagn 0000:03:00.0: setting latency timer to 64
[    4.761686] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[    4.789929] iwlagn 0000:03:00.0: Unsupported (too old) EEPROM VER=0x422 < 0x423 CALIB=0x5 < 0x4
[    4.790768] iwlagn 0000:03:00.0: PCI INT A disabled
[    4.790791] iwlagn: probe of 0000:03:00.0 failed with error -22
[    5.054961] init: failsafe main process (786) killed by TERM signal
[    5.169752] Console: switching to colour frame buffer device 170x48
[ 1356.399651] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 1356.399656] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 1356.399756] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1356.399770] iwlagn 0000:03:00.0: setting latency timer to 64
[ 1356.399828] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[ 1356.426876] iwlagn 0000:03:00.0: Unsupported (too old) EEPROM VER=0x422 < 0x423 CALIB=0x5 < 0x4
[ 1356.426907] iwlagn 0000:03:00.0: PCI INT A disabled
[ 1356.426918] iwlagn: probe of 0000:03:00.0 failed with error -22
[ 1456.009864] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 1456.009868] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[ 1456.009958] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1456.009973] iwlagn 0000:03:00.0: setting latency timer to 64
[ 1456.010020] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[ 1456.037059] iwlagn 0000:03:00.0: Unsupported (too old) EEPROM VER=0x422 < 0x423 CALIB=0x5 < 0x4
[ 1456.037093] iwlagn 0000:03:00.0: PCI INT A disabled
[ 1456.037106] iwlagn: probe of 0000:03:00.0 failed with error -22

```

```

@M11x-R2:~$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:26:b9:e4:0d:0a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=169.229.92.11 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:b6800000-b683ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b5800000-b5801fff

```

---

### Post by chili555 on 2012-02-17
> Unsupported (too old) EEPROM VER=0x422 < 0x423 CALIB=0x5 < 0x4Please see this: [http://forums.fedoraforum.org/showthread.php?t=254293](http://forums.fedoraforum.org/showthread.php?t=254293) and this: [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997) Especially see comment #8.

Now you could return the card and get another, or if you are especially adventerous, you could download compat-wireless here: [http://linuxwireless.org/en/users/Download/stable#compat-wireless_3.0_stable_releases](http://linuxwireless.org/en/users/Download/stable#compat-wireless_3.0_stable_releases)

I suggest you download compat-wireless-3.0.9-1 to your desktop. Right-click it and select *Extract Here*. Open the file drivers/net/wireless/iwlwifi/iwl-agn-eeprom.c with any text editor; gedit or nano, for eample. Comment out the check for EEPROM version and the error handling as I've shown here. I've highlighted the changed parts. All other parts of the file remain unchanged:```
/******************************************************************************
 *
 * EEPROM related functions
 *
******************************************************************************/

int iwl_eeprom_check_version(struct iwl_priv *priv)
{
	u16 eeprom_ver;
	u16 calib_ver;

	eeprom_ver = iwl_eeprom_query16(priv, EEPROM_VERSION);
	calib_ver = iwlagn_eeprom_calib_version(priv);

[COLOR="Red"]/*****************************************************************************
*	if (eeprom_ver < priv->cfg->eeprom_ver ||
*	    calib_ver < priv->cfg->eeprom_calib_ver)
*		goto err;
******************************************************************************/[/COLOR]
	IWL_INFO(priv, "device EEPROM VER=0x%x, CALIB=0x%x\n",
		 eeprom_ver, calib_ver);

	return 0;
[COLOR="Red"]/********************************************************************************
*err:
*	IWL_ERR(priv, "Unsupported (too old) EEPROM VER=0x%x < 0x%x "
*		  "CALIB=0x%x < 0x%x\n",
*		  eeprom_ver, priv->cfg->eeprom_ver,
*		  calib_ver,  priv->cfg->eeprom_calib_ver);
*	return -EINVAL;
*********************************************************************************/[/COLOR]
}
```Proofread carefully, twice. Save and close the text editor.

Now open a terminal and do:```
cd Desktop/compat-wireless-3.0.9-1
sudo su
./scripts/driver-select iwlagn
make
make install
modprobe -r iwlagn
modprobe iwlagn
iwconfig
exit
```Any improvement?

---

### Post by sreezon on 2012-02-17
The device is no longer unclaimed. It is now disabled. It also won't show on startup. I'd always have to do sudo modprobe iwlagn for it to show up.


```

@M11x-R2:~$ dmesg | egrep 'iwl|switch|radio|kill|wmi'
[    3.454056] wmi: Mapper loaded
[    3.571906] Modules linked in: video wmi ndiswrapper(+) lp parport sdhci_pci sdhci ahci libahci firewire_ohci firewire_core crc_itu_t atl1c
[    3.872233] init: failsafe main process (724) killed by TERM signal
[    5.076564] Console: switching to colour frame buffer device 128x48
[  264.289884] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  264.289889] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[  264.289970] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  264.289980] iwlagn 0000:03:00.0: setting latency timer to 64
[  264.290024] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[  264.317111] iwlagn 0000:03:00.0: device EEPROM VER=0x422, CALIB=0x5
[  264.317113] iwlagn 0000:03:00.0: Device SKU: 0Xb
[  264.317115] iwlagn 0000:03:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[  264.317127] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  264.317210] iwlagn 0000:03:00.0: irq 45 for MSI/MSI-X
[  264.326107] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[  264.336606] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  264.419636] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  264.419644] iwlagn 0000:03:00.0: Loaded firmware version: 9.221.4.1 build 25532
[  264.419649] iwlagn 0000:03:00.0: Not valid error log pointer 0x00000000 for Init uCode
[  264.419653] iwlagn 0000:03:00.0: CSR values:
[  264.419655] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  264.419663] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  264.419669] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  264.419676] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[  264.419682] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  264.419689] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[  264.419695] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[  264.419702] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[  264.419708] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  264.419715] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[  264.419721] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[  264.419728] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000004
[  264.419734] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00020000
[  264.419741] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[  264.419747] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  264.419754] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  264.419760] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  264.419766] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  264.419773] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[  264.419779] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[  264.419785] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  264.419792] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  264.419798] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  264.419805] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  264.419808] iwlagn 0000:03:00.0: FH register values:
[  264.419825] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X135ad700
[  264.419841] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0135ad60
[  264.419858] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[  264.419874] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[  264.419891] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  264.419907] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  264.419923] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  264.419940] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  264.419956] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  264.419961] iwlagn 0000:03:00.0: Invalid event log pointer 0x00000000 for Init uCode
[  264.420316] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[  264.420357] iwlagn 0000:03:00.0: Unable to initialize device.
[  264.491578] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  264.491586] iwlagn 0000:03:00.0: Loaded firmware version: 9.221.4.1 build 25532
[  264.491675] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[  264.491679] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[  264.491683] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[  264.491687] iwlagn 0000:03:00.0: 0x00020118 | uPc
[  264.491689] iwlagn 0000:03:00.0: 0x00020070 | branchlink1
[  264.491692] iwlagn 0000:03:00.0: 0x00020070 | branchlink2
[  264.491695] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[  264.491698] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[  264.491701] iwlagn 0000:03:00.0: 0x00000000 | data1
[  264.491704] iwlagn 0000:03:00.0: 0x00000000 | data2
[  264.491706] iwlagn 0000:03:00.0: 0x0000010B | line
[  264.491709] iwlagn 0000:03:00.0: 0x00012FB5 | beacon time
[  264.491712] iwlagn 0000:03:00.0: 0x0000604B | tsf low
[  264.491715] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[  264.491717] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[  264.491720] iwlagn 0000:03:00.0: 0x0000604F | time gp2
[  264.491723] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[  264.491726] iwlagn 0000:03:00.0: 0x000109DD | uCode version
[  264.491729] iwlagn 0000:03:00.0: 0x00000074 | hw version
[  264.491732] iwlagn 0000:03:00.0: 0x00480303 | board version
[  264.491735] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[  264.491737] iwlagn 0000:03:00.0: CSR values:
[  264.491740] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  264.491747] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  264.491754] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  264.491760] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[  264.491767] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  264.491773] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[  264.491779] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[  264.491786] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[  264.491792] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  264.491799] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[  264.491805] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[  264.491811] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000004
[  264.491818] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00020000
[  264.491824] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[  264.491831] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  264.491837] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  264.491844] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  264.491850] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  264.491856] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[  264.491863] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[  264.491869] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  264.491876] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  264.491882] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  264.491889] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  264.491892] iwlagn 0000:03:00.0: FH register values:
[  264.491908] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X135ad700
[  264.491924] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0135ad60
[  264.491940] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[  264.491957] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[  264.491973] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  264.491990] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  264.492006] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  264.492022] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  264.492039] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  264.492111] iwlagn 0000:03:00.0: Log capacity 1024 is bogus, limit to 512 entries
[  264.492116] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[  264.492140] iwlagn 0000:03:00.0: EVT_LOGT:0000016253:0x00000000:0064
[  264.492155] iwlagn 0000:03:00.0: EVT_LOGT:0000016257:0x00000000:0064
[  264.492168] iwlagn 0000:03:00.0: EVT_LOGT:0000016260:0x00000000:0064
[  264.492181] iwlagn 0000:03:00.0: EVT_LOGT:0000016274:0x00000000:0064
[  264.492194] iwlagn 0000:03:00.0: EVT_LOGT:0000016277:0x00000000:0064
[  264.492207] iwlagn 0000:03:00.0: EVT_LOGT:0000016280:0x00000000:0064
[  264.492220] iwlagn 0000:03:00.0: EVT_LOGT:0000016283:0x00000000:0064
[  264.492233] iwlagn 0000:03:00.0: EVT_LOGT:0000016297:0x00000000:0064
[  264.492246] iwlagn 0000:03:00.0: EVT_LOGT:0000016300:0x00000000:0064
[  264.492259] iwlagn 0000:03:00.0: EVT_LOGT:0000016304:0x00000000:0064
[  264.492272] iwlagn 0000:03:00.0: EVT_LOGT:0000016307:0x00000000:0064
[  264.492285] iwlagn 0000:03:00.0: EVT_LOGT:0000016321:0x00000000:0064
[  264.492298] iwlagn 0000:03:00.0: EVT_LOGT:0000016324:0x00000000:0064
[  264.492311] iwlagn 0000:03:00.0: EVT_LOGT:0000016327:0x00000000:0064
[  264.492323] iwlagn 0000:03:00.0: EVT_LOGT:0000016330:0x00000000:0064
[  264.492336] iwlagn 0000:03:00.0: EVT_LOGT:0000016344:0x00000000:0064
[  264.492349] iwlagn 0000:03:00.0: EVT_LOGT:0000016347:0x00000000:0064
[  264.492374] iwlagn 0000:03:00.0: EVT_LOGT:0000019365:0x00000000:0064
[  264.492387] iwlagn 0000:03:00.0: EVT_LOGT:0000019368:0x00000000:0064
[  264.492400] iwlagn 0000:03:00.0: EVT_LOGT:0000024661:0x00000000:0125
[  264.492772] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[  264.492812] iwlagn 0000:03:00.0: Unable to initialize device.
[  264.532883] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  264.532888] iwlagn 0000:03:00.0: Loaded firmware version: 9.221.4.1 build 25532
[  264.532977] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[  264.532981] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[  264.532984] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[  264.532988] iwlagn 0000:03:00.0: 0x00020118 | uPc
[  264.532991] iwlagn 0000:03:00.0: 0x00020070 | branchlink1
[  264.532993] iwlagn 0000:03:00.0: 0x00020070 | branchlink2
[  264.532996] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[  264.532999] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[  264.533002] iwlagn 0000:03:00.0: 0x00000000 | data1
[  264.533005] iwlagn 0000:03:00.0: 0x00000000 | data2
[  264.533008] iwlagn 0000:03:00.0: 0x0000010B | line
[  264.533010] iwlagn 0000:03:00.0: 0x00012FB5 | beacon time
[  264.533013] iwlagn 0000:03:00.0: 0x0000604B | tsf low
[  264.533016] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[  264.533019] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[  264.533021] iwlagn 0000:03:00.0: 0x00006050 | time gp2
[  264.533024] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[  264.533027] iwlagn 0000:03:00.0: 0x000109DD | uCode version
[  264.533030] iwlagn 0000:03:00.0: 0x00000074 | hw version
[  264.533033] iwlagn 0000:03:00.0: 0x00480303 | board version
[  264.533036] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[  264.533038] iwlagn 0000:03:00.0: CSR values:
[  264.533041] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  264.533048] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  264.533054] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  264.533061] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[  264.533067] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  264.533074] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[  264.533080] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[  264.533086] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[  264.533093] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  264.533099] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[  264.533105] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[  264.533112] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000004
[  264.533118] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00020000
[  264.533125] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[  264.533131] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  264.533137] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  264.533144] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  264.533150] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  264.533156] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[  264.533163] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[  264.533169] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  264.533175] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  264.533182] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  264.533188] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  264.533191] iwlagn 0000:03:00.0: FH register values:
[  264.533207] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X135ad700
[  264.533223] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0135ad60
[  264.533240] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[  264.533256] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[  264.533273] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  264.533289] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  264.533305] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  264.533322] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  264.533338] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  264.533399] iwlagn 0000:03:00.0: Log capacity 1024 is bogus, limit to 512 entries
[  264.533402] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[  264.533424] iwlagn 0000:03:00.0: EVT_LOGT:0000016254:0x00000000:0064
[  264.533437] iwlagn 0000:03:00.0: EVT_LOGT:0000016258:0x00000000:0064
[  264.533450] iwlagn 0000:03:00.0: EVT_LOGT:0000016261:0x00000000:0064
[  264.533463] iwlagn 0000:03:00.0: EVT_LOGT:0000016275:0x00000000:0064
[  264.533476] iwlagn 0000:03:00.0: EVT_LOGT:0000016278:0x00000000:0064
[  264.533489] iwlagn 0000:03:00.0: EVT_LOGT:0000016281:0x00000000:0064
[  264.533502] iwlagn 0000:03:00.0: EVT_LOGT:0000016284:0x00000000:0064
[  264.533515] iwlagn 0000:03:00.0: EVT_LOGT:0000016298:0x00000000:0064
[  264.533529] iwlagn 0000:03:00.0: EVT_LOGT:0000016301:0x00000000:0064
[  264.533542] iwlagn 0000:03:00.0: EVT_LOGT:0000016305:0x00000000:0064
[  264.533555] iwlagn 0000:03:00.0: EVT_LOGT:0000016308:0x00000000:0064
[  264.533568] iwlagn 0000:03:00.0: EVT_LOGT:0000016322:0x00000000:0064
[  264.533581] iwlagn 0000:03:00.0: EVT_LOGT:0000016325:0x00000000:0064
[  264.533594] iwlagn 0000:03:00.0: EVT_LOGT:0000016328:0x00000000:0064
[  264.533607] iwlagn 0000:03:00.0: EVT_LOGT:0000016331:0x00000000:0064
[  264.533620] iwlagn 0000:03:00.0: EVT_LOGT:0000016345:0x00000000:0064
[  264.533633] iwlagn 0000:03:00.0: EVT_LOGT:0000016348:0x00000000:0064
[  264.533657] iwlagn 0000:03:00.0: EVT_LOGT:0000019366:0x00000000:0064
[  264.533670] iwlagn 0000:03:00.0: EVT_LOGT:0000019369:0x00000000:0064
[  264.533684] iwlagn 0000:03:00.0: EVT_LOGT:0000024662:0x00000000:0125
[  264.534020] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[  264.534056] iwlagn 0000:03:00.0: Unable to initialize device.
[  624.243188] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  624.243197] iwlagn 0000:03:00.0: Loaded firmware version: 9.221.4.1 build 25532
[  624.243287] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[  624.243291] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[  624.243297] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[  624.243299] iwlagn 0000:03:00.0: 0x00020118 | uPc
[  624.243300] iwlagn 0000:03:00.0: 0x00020070 | branchlink1
[  624.243302] iwlagn 0000:03:00.0: 0x00020070 | branchlink2
[  624.243303] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[  624.243305] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[  624.243306] iwlagn 0000:03:00.0: 0x00000000 | data1
[  624.243308] iwlagn 0000:03:00.0: 0x00000000 | data2
[  624.243309] iwlagn 0000:03:00.0: 0x0000010B | line
[  624.243311] iwlagn 0000:03:00.0: 0x00012FB5 | beacon time
[  624.243312] iwlagn 0000:03:00.0: 0x0000604B | tsf low
[  624.243314] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[  624.243315] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[  624.243317] iwlagn 0000:03:00.0: 0x0000604F | time gp2
[  624.243318] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[  624.243319] iwlagn 0000:03:00.0: 0x000109DD | uCode version
[  624.243321] iwlagn 0000:03:00.0: 0x00000074 | hw version
[  624.243323] iwlagn 0000:03:00.0: 0x00480303 | board version
[  624.243324] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[  624.243326] iwlagn 0000:03:00.0: CSR values:
[  624.243327] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  624.243333] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  624.243338] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  624.243342] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[  624.243347] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  624.243352] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[  624.243357] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[  624.243362] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[  624.243366] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  624.243371] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[  624.243376] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[  624.243381] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000004
[  624.243386] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00020000
[  624.243391] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[  624.243396] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  624.243401] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  624.243405] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  624.243410] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  624.243415] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[  624.243420] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[  624.243425] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  624.243430] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  624.243434] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  624.243439] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  624.243441] iwlagn 0000:03:00.0: FH register values:
[  624.243456] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X135ad700
[  624.243471] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0135ad60
[  624.243485] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[  624.243500] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[  624.243515] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  624.243530] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  624.243544] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  624.243559] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  624.243574] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  624.243633] iwlagn 0000:03:00.0: Log capacity 1024 is bogus, limit to 512 entries
[  624.243635] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[  624.243655] iwlagn 0000:03:00.0: EVT_LOGT:0000016253:0x00000000:0064
[  624.243666] iwlagn 0000:03:00.0: EVT_LOGT:0000016257:0x00000000:0064
[  624.243678] iwlagn 0000:03:00.0: EVT_LOGT:0000016260:0x00000000:0064
[  624.243689] iwlagn 0000:03:00.0: EVT_LOGT:0000016274:0x00000000:0064
[  624.243701] iwlagn 0000:03:00.0: EVT_LOGT:0000016277:0x00000000:0064
[  624.243712] iwlagn 0000:03:00.0: EVT_LOGT:0000016280:0x00000000:0064
[  624.243724] iwlagn 0000:03:00.0: EVT_LOGT:0000016283:0x00000000:0064
[  624.243735] iwlagn 0000:03:00.0: EVT_LOGT:0000016297:0x00000000:0064
[  624.243747] iwlagn 0000:03:00.0: EVT_LOGT:0000016300:0x00000000:0064
[  624.243758] iwlagn 0000:03:00.0: EVT_LOGT:0000016304:0x00000000:0064
[  624.243769] iwlagn 0000:03:00.0: EVT_LOGT:0000016307:0x00000000:0064
[  624.243781] iwlagn 0000:03:00.0: EVT_LOGT:0000016321:0x00000000:0064
[  624.243792] iwlagn 0000:03:00.0: EVT_LOGT:0000016324:0x00000000:0064
[  624.243804] iwlagn 0000:03:00.0: EVT_LOGT:0000016327:0x00000000:0064
[  624.243815] iwlagn 0000:03:00.0: EVT_LOGT:0000016330:0x00000000:0064
[  624.243826] iwlagn 0000:03:00.0: EVT_LOGT:0000016344:0x00000000:0064
[  624.243838] iwlagn 0000:03:00.0: EVT_LOGT:0000016347:0x00000000:0064
[  624.243860] iwlagn 0000:03:00.0: EVT_LOGT:0000019365:0x00000000:0064
[  624.243872] iwlagn 0000:03:00.0: EVT_LOGT:0000019368:0x00000000:0064
[  624.243884] iwlagn 0000:03:00.0: EVT_LOGT:0000024661:0x00000000:0125
[  624.244215] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[  624.244252] iwlagn 0000:03:00.0: Unable to initialize device.
[  799.413644] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  799.413655] iwlagn 0000:03:00.0: Loaded firmware version: 9.221.4.1 build 25532
[  799.413744] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[  799.413748] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[  799.413752] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[  799.413755] iwlagn 0000:03:00.0: 0x00020118 | uPc
[  799.413758] iwlagn 0000:03:00.0: 0x00020070 | branchlink1
[  799.413761] iwlagn 0000:03:00.0: 0x00020070 | branchlink2
[  799.413764] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[  799.413767] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[  799.413769] iwlagn 0000:03:00.0: 0x00000000 | data1
[  799.413772] iwlagn 0000:03:00.0: 0x00000000 | data2
[  799.413775] iwlagn 0000:03:00.0: 0x0000010B | line
[  799.413778] iwlagn 0000:03:00.0: 0x00012FB5 | beacon time
[  799.413781] iwlagn 0000:03:00.0: 0x0000604B | tsf low
[  799.413783] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[  799.413786] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[  799.413789] iwlagn 0000:03:00.0: 0x0000604F | time gp2
[  799.413792] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[  799.413794] iwlagn 0000:03:00.0: 0x000109DD | uCode version
[  799.413797] iwlagn 0000:03:00.0: 0x00000074 | hw version
[  799.413800] iwlagn 0000:03:00.0: 0x00480303 | board version
[  799.413803] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[  799.413806] iwlagn 0000:03:00.0: CSR values:
[  799.413809] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  799.413816] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  799.413822] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[  799.413829] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[  799.413835] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[  799.413842] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[  799.413848] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X0000000f
[  799.413854] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[  799.413861] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[  799.413867] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X00000074
[  799.413874] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0X00000000
[  799.413880] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000004
[  799.413886] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00020000
[  799.413893] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080044
[  799.413899] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[  799.413905] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  799.413912] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  799.413918] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  799.413925] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[  799.413931] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[  799.413937] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  799.413944] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  799.413950] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  799.413956] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  799.413960] iwlagn 0000:03:00.0: FH register values:
[  799.413976] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X135ad700
[  799.413992] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0135ad60
[  799.414009] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[  799.414025] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[  799.414041] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  799.414058] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  799.414074] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  799.414090] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  799.414107] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  799.414168] iwlagn 0000:03:00.0: Log capacity 1024 is bogus, limit to 512 entries
[  799.414171] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 20 entries
[  799.414193] iwlagn 0000:03:00.0: EVT_LOGT:0000016253:0x00000000:0064
[  799.414207] iwlagn 0000:03:00.0: EVT_LOGT:0000016257:0x00000000:0064
[  799.414220] iwlagn 0000:03:00.0: EVT_LOGT:0000016260:0x00000000:0064
[  799.414233] iwlagn 0000:03:00.0: EVT_LOGT:0000016274:0x00000000:0064
[  799.414246] iwlagn 0000:03:00.0: EVT_LOGT:0000016277:0x00000000:0064
[  799.414259] iwlagn 0000:03:00.0: EVT_LOGT:0000016280:0x00000000:0064
[  799.414272] iwlagn 0000:03:00.0: EVT_LOGT:0000016283:0x00000000:0064
[  799.414285] iwlagn 0000:03:00.0: EVT_LOGT:0000016297:0x00000000:0064
[  799.414298] iwlagn 0000:03:00.0: EVT_LOGT:0000016300:0x00000000:0064
[  799.414311] iwlagn 0000:03:00.0: EVT_LOGT:0000016304:0x00000000:0064
[  799.414324] iwlagn 0000:03:00.0: EVT_LOGT:0000016307:0x00000000:0064
[  799.414337] iwlagn 0000:03:00.0: EVT_LOGT:0000016321:0x00000000:0064
[  799.414350] iwlagn 0000:03:00.0: EVT_LOGT:0000016324:0x00000000:0064
[  799.414363] iwlagn 0000:03:00.0: EVT_LOGT:0000016327:0x00000000:0064
[  799.414376] iwlagn 0000:03:00.0: EVT_LOGT:0000016330:0x00000000:0064
[  799.414389] iwlagn 0000:03:00.0: EVT_LOGT:0000016344:0x00000000:0064
[  799.414402] iwlagn 0000:03:00.0: EVT_LOGT:0000016347:0x00000000:0064
[  799.414426] iwlagn 0000:03:00.0: EVT_LOGT:0000019365:0x00000000:0064
[  799.414439] iwlagn 0000:03:00.0: EVT_LOGT:0000019368:0x00000000:0064
[  799.414452] iwlagn 0000:03:00.0: EVT_LOGT:0000024661:0x00000000:0125
[  799.414754] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[  799.414792] iwlagn 0000:03:00.0: Unable to initialize device.

```

```

@M11x-R2:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:26:b9:e4:0d:0a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=169.229.92.11 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:b6800000-b683ffff ioport:3000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 01
       serial: 00:00:00:54:fb:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-16-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:b5800000-b5801fff

```

---

### Post by chili555 on 2012-02-17
I'm sorry; I'm out of ideas. Googling suggests it's an engineering prototype card. I don't know how to proceed. You might remove compat-wireless:```
cd Desktop/compat-wireless-3.0.9-1
sudo su
make uninstall
modprobe -r iwlagn
modprobe iwlagn
exit
```I wish I could be of more assistance.

---

### Post by sreezon on 2012-02-18
Thank you for your help. Also, could you post the link that suggests that this chip is an engineering prototype? I'd need evidence if I'm going to return this chip.

---

### Post by chili555 on 2012-02-18
> **sreezon said:**
> Thank you for your help. Also, could you post the link that suggests that this chip is an engineering prototype? I'd need evidence if I'm going to return this chip.See my post #2 above, especially: [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997)> Your card surely does not have correct eeprom and that is not something you can
fix outside of a lab. Please try to get a replacement.> The problem is on Windows side which do not check EEPROM version. the engineer
sample having earlier EEPROM which can have expected behavior, plus did not go
through regulator scan. On Linux, we follow the right process to make sure all
the devices will have the expectation.Please note this bug reort is at **intel**linuxwireless.

---

