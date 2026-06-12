---
title: "Help Connecting to wireless intel centrino wireless-n 6150"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by wolfie3214 on 2012-04-26
Hi guys i just installed ubuntu 11.10 and i love it but i cannot connect to wireless.  More specifically i cannot even bring up my wireless networks.  when i try to enable wireless nothing happens.  i have a sony vaio vpceg.  with a intel centrino wireless-n 6150 wireless card and WIMAX.  Please help im new to ubuntu and dont know anything about codingso i would appreciated step by step instructions.  just downloaded 12.04.

---

### Post by chili555 on 2012-04-27
Please open a terminal and run and post:```
rfkill list all
sudo modprobe iwlagn
dmesg | grep iwl
```Thanks.

---

### Post by zloi on 2012-04-29
Hi Chili, I've heard you're can help me with some wireless problems.
```

rfkill list all 
sudo modprobe iwlagn 
dmesg | grep iwl

```

```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````

[    7.670330] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.670367] iwlwifi 0000:03:00.0: setting latency timer to 64
[    7.670406] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    7.670407] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90000c7c000
[    7.670408] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[    7.670532] iwlwifi 0000:03:00.0: irq 52 for MSI/MSI-X
[    7.670606] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[    7.670704] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    7.686385] iwlwifi 0000:03:00.0: device EEPROM VER=0x71a, CALIB=0x6
[    7.686387] iwlwifi 0000:03:00.0: Device SKU: 0X150
[    7.686388] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    7.686396] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    8.368109] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[    8.516222] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.380027] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   12.386808] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[   12.472990] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   12.479767] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[   47.025440] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:1f:1f:62:43:c8 tid = 0
[   51.627729] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   51.627740] iwlwifi 0000:03:00.0: Loaded firmware version: 18.168.6.1
[   51.627879] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[   51.627881] iwlwifi 0000:03:00.0: Status: 0x000412E4, count: 6
[   51.627882] iwlwifi 0000:03:00.0: 0x00000EDC | ADVANCED_SYSASSERT          
[   51.627884] iwlwifi 0000:03:00.0: 0x000233B0 | uPc
[   51.627885] iwlwifi 0000:03:00.0: 0x00023360 | branchlink1
[   51.627886] iwlwifi 0000:03:00.0: 0x00023360 | branchlink2
[   51.627887] iwlwifi 0000:03:00.0: 0x0000DBEA | interruptlink1
[   51.627888] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[   51.627889] iwlwifi 0000:03:00.0: 0x55F5C95D | data1
[   51.627891] iwlwifi 0000:03:00.0: 0x00EC4A1D | data2
[   51.627892] iwlwifi 0000:03:00.0: 0x00000AF4 | line
[   51.627893] iwlwifi 0000:03:00.0: 0x55000211 | beacon time
[   51.627894] iwlwifi 0000:03:00.0: 0xA85EADEF | tsf low
[   51.627895] iwlwifi 0000:03:00.0: 0x00000039 | tsf hi
[   51.627896] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[   51.627897] iwlwifi 0000:03:00.0: 0x0236D69B | time gp2
[   51.627898] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[   51.627899] iwlwifi 0000:03:00.0: 0x754312A8 | uCode version
[   51.627900] iwlwifi 0000:03:00.0: 0x000000B0 | hw version
[   51.627902] iwlwifi 0000:03:00.0: 0x00880303 | board version
[   51.627903] iwlwifi 0000:03:00.0: 0x00EC4A1D | hcmd
[   51.627904] iwlwifi 0000:03:00.0: CSR values:
[   51.627905] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   51.627940] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00880303
[   51.627968] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   51.627994] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[   51.628019] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   51.628045] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   51.628070] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000003c
[   51.628096] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[   51.628122] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   51.628147] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X000000b0
[   51.628173] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X50460ffd
[   51.628198] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000801
[   51.628224] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[   51.628250] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[   51.628275] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00003903
[   51.628301] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   51.628327] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   51.628352] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   51.628363] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000058
[   51.628388] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X8822c9a6
[   51.628413] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   51.628423] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   51.628433] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   51.628459] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[   51.628460] iwlwifi 0000:03:00.0: FH register values:
[   51.628495] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X22ef4100
[   51.628508] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X022ef2a0
[   51.628521] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000058
[   51.628535] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   51.628548] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   51.628561] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   51.628575] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   51.628588] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   51.628601] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   51.628655] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: nothing in log
[   51.629087] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   51.635874] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[  320.590248] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  340.308983] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  340.309857] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  350.619655] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  350.621478] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  351.491182] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  351.495190] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  351.502021] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[  351.731048] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  351.778592] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[  351.778604] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  351.778613] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5)
[  351.778652] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[  351.778657] iwlwifi 0000:03:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[  351.890477] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  352.093765] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  352.100614] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[  352.276629] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  352.313987] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[  352.314001] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  352.314010] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5)
[  352.314051] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[  352.314057] iwlwifi 0000:03:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[  352.719251] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  352.723415] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  352.730256] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[  353.073593] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  353.156997] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[  353.157002] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  353.157005] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5)
[  353.157047] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[  353.157049] iwlwifi 0000:03:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[  353.507211] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[  353.511195] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  353.518043] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[  613.221211] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:1f:1f:62:43:c8 tid = 0
[ 1015.430217] iwlwifi 0000:03:00.0: PCI INT A disabled
[ 1020.157711] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1020.157768] iwlwifi 0000:03:00.0: setting latency timer to 64
[ 1020.157813] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[ 1020.157814] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90005da4000
[ 1020.157815] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[ 1020.157948] iwlwifi 0000:03:00.0: irq 52 for MSI/MSI-X
[ 1020.158026] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[ 1020.158129] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 1020.173835] iwlwifi 0000:03:00.0: device EEPROM VER=0x71a, CALIB=0x6
[ 1020.173837] iwlwifi 0000:03:00.0: Device SKU: 0X150
[ 1020.173838] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[ 1020.173855] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[ 1020.176865] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[ 1020.177352] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1020.193999] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 1020.200867] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[ 1020.298793] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 1020.305594] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[ 1054.536367] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:1f:1f:62:43:c8 tid = 0
[ 1458.498520] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 1458.498535] iwlwifi 0000:03:00.0: Loaded firmware version: 18.168.6.1
[ 1458.498663] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:
[ 1458.498670] iwlwifi 0000:03:00.0: Status: 0x000412E4, count: 6
[ 1458.498677] iwlwifi 0000:03:00.0: 0x00000EDC | ADVANCED_SYSASSERT          
[ 1458.498682] iwlwifi 0000:03:00.0: 0x000233B0 | uPc
[ 1458.498686] iwlwifi 0000:03:00.0: 0x00023360 | branchlink1
[ 1458.498691] iwlwifi 0000:03:00.0: 0x00023360 | branchlink2
[ 1458.498695] iwlwifi 0000:03:00.0: 0x0000DBEA | interruptlink1
[ 1458.498700] iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
[ 1458.498704] iwlwifi 0000:03:00.0: 0xF0C345B8 | data1
[ 1458.498708] iwlwifi 0000:03:00.0: 0x1277B1AE | data2
[ 1458.498712] iwlwifi 0000:03:00.0: 0x00000AF4 | line
[ 1458.498717] iwlwifi 0000:03:00.0: 0x2901599D | beacon time
[ 1458.498721] iwlwifi 0000:03:00.0: 0xFC518663 | tsf low
[ 1458.498725] iwlwifi 0000:03:00.0: 0x00000039 | tsf hi
[ 1458.498730] iwlwifi 0000:03:00.0: 0x00000000 | time gp1
[ 1458.498734] iwlwifi 0000:03:00.0: 0x1A2323C7 | time gp2
[ 1458.498738] iwlwifi 0000:03:00.0: 0x00000000 | time gp3
[ 1458.498742] iwlwifi 0000:03:00.0: 0x754312A8 | uCode version
[ 1458.498746] iwlwifi 0000:03:00.0: 0x000000B0 | hw version
[ 1458.498751] iwlwifi 0000:03:00.0: 0x00880303 | board version
[ 1458.498755] iwlwifi 0000:03:00.0: 0x1277B1AE | hcmd
[ 1458.498759] iwlwifi 0000:03:00.0: CSR values:
[ 1458.498763] iwlwifi 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 1458.498797] iwlwifi 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00880303
[ 1458.498828] iwlwifi 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[ 1458.498860] iwlwifi 0000:03:00.0:                     CSR_INT: 0X00000000
[ 1458.498892] iwlwifi 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 1458.498921] iwlwifi 0000:03:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 1458.498953] iwlwifi 0000:03:00.0:                 CSR_GPIO_IN: 0X0000003c
[ 1458.498982] iwlwifi 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 1458.499013] iwlwifi 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 1458.499042] iwlwifi 0000:03:00.0:                  CSR_HW_REV: 0X000000b0
[ 1458.499074] iwlwifi 0000:03:00.0:              CSR_EEPROM_REG: 0X50460ffd
[ 1458.499103] iwlwifi 0000:03:00.0:               CSR_EEPROM_GP: 0X90000801
[ 1458.499134] iwlwifi 0000:03:00.0:              CSR_OTP_GP_REG: 0X00030001
[ 1458.499163] iwlwifi 0000:03:00.0:                 CSR_GIO_REG: 0X00080042
[ 1458.499195] iwlwifi 0000:03:00.0:            CSR_GP_UCODE_REG: 0X0000d527
[ 1458.499227] iwlwifi 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 1458.499256] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 1458.499287] iwlwifi 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 1458.499316] iwlwifi 0000:03:00.0:                 CSR_LED_REG: 0X00000058
[ 1458.499348] iwlwifi 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X881f97c2
[ 1458.499377] iwlwifi 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 1458.499408] iwlwifi 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 1458.499441] iwlwifi 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 1458.499470] iwlwifi 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[ 1458.499474] iwlwifi 0000:03:00.0: FH register values:
[ 1458.499515] iwlwifi 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X230fd200
[ 1458.499554] iwlwifi 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02222960
[ 1458.499592] iwlwifi 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000078
[ 1458.499630] iwlwifi 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[ 1458.499669] iwlwifi 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 1458.499715] iwlwifi 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 1458.499752] iwlwifi 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 1458.499765] iwlwifi 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 1458.499778] iwlwifi 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 1458.499832] iwlwifi 0000:03:00.0: Start IWL Event Log Dump: nothing in log
[ 1458.499845] iwlwifi 0000:03:00.0: fw recovery, no hcmd send
[ 1458.499847] iwlwifi 0000:03:00.0: Error sending REPLY_TX_LINK_QUALITY_CMD: enqueue_hcmd failed: -5
[ 1458.500283] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 1458.507128] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1

```sudo modprobe iwlan - shows nothing

---

### Post by chili555 on 2012-04-29
> [   51.627729] iwlwifi 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   51.627740] iwlwifi 0000:03:00.0: Loaded firmware version: 18.168.6.1
[   51.627879] iwlwifi 0000:03:00.0: Start IWL Error Log Dump:Ugly.

Please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi fw_restart=1
dmesg | grep iwl | tail -n20
```Let's see if there is improvement.

---

### Post by reifnotreef on 2012-06-09
I'm trying to get this working as well.

I've been through all the other threads saying to cp/chmod etc the files into my firmware folder. No matter what iwlwifi and iwlagn are NEVER found.
Now I'm trying to install everything I could possibly need then create a bootable cd with UCK. No luck yet though!

---

