---
title: "Intel Centrino Wireless -N 1000/Ubuntu 11.10 /Lenovo IdeapadY460"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by amaz1ng on 2012-03-15
I was running Ubuntu 11.04 and update to 11.10. After the update my wireless networking didn't work. The Networking button on the upper right (default GNOME) says "device not ready" about my wireless card.

lspic -v gives me:
```

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
	Subsystem: Lenovo Device 3975
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f8400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3 
```

ifconfig gives me:
```
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:07:76:3d  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea9a:8fff:fe07:763d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151117959 (151.1 MB)  TX bytes:16735919 (16.7 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1678784 (1.6 MB)  TX bytes:1678784 (1.6 MB)



```

iwconfig gives me:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

lsmod wlan0 gives me:
```

usage: lsmod

```

dmesg | grep "iwlagn" returns

```

[   17.278869] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.278872] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   17.278930] iwlagn 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.278941] iwlagn 0000:03:00.0: setting latency timer to 64
[   17.278975] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   17.300599] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   17.300602] iwlagn 0000:03:00.0: Device SKU: 0X9
[   17.300604] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   17.306245] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   17.306574] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[   17.506793] iwlagn 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   19.202385] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   19.202389] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   19.202511] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[   19.202513] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[   19.202515] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   19.202516] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[   19.202517] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[   19.202519] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[   19.202520] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[   19.202521] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[   19.202522] iwlagn 0000:03:00.0: 0x00000000 | data1
[   19.202524] iwlagn 0000:03:00.0: 0x00000000 | data2
[   19.202525] iwlagn 0000:03:00.0: 0x00000616 | line
[   19.202526] iwlagn 0000:03:00.0: 0x00018BCB | beacon time
[   19.202527] iwlagn 0000:03:00.0: 0x00000435 | tsf low
[   19.202529] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[   19.202530] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[   19.202531] iwlagn 0000:03:00.0: 0x0000043A | time gp2
[   19.202532] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[   19.202534] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[   19.202535] iwlagn 0000:03:00.0: 0x0000006C | hw version
[   19.202536] iwlagn 0000:03:00.0: 0x00C80300 | board version
[   19.202537] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[   19.202539] iwlagn 0000:03:00.0: CSR values:
[   19.202540] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   19.202545] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   19.202550] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   19.202555] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[   19.202559] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   19.202564] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   19.202569] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[   19.202573] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[   19.202578] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   19.202583] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[   19.202587] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   19.202592] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   19.202596] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[   19.202601] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[   19.202607] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   19.202611] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   19.202616] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   19.202620] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   19.202625] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   19.202630] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   19.202634] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   19.202639] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[   19.202644] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   19.202648] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   19.202650] iwlagn 0000:03:00.0: FH register values:
[   19.202667] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[   19.202685] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[   19.202703] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   19.202721] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   19.202739] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   19.202756] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   19.202773] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   19.202790] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   19.202807] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   19.202876] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[   19.202898] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   19.202913] iwlagn 0000:03:00.0: EVT_LOGT:0000000022:0x00000000:1208
[   19.202927] iwlagn 0000:03:00.0: EVT_LOGT:0000001003:0x00000001:0071
[   19.202940] iwlagn 0000:03:00.0: EVT_LOGT:0000001079:0x00000002:0071
[   19.202954] iwlagn 0000:03:00.0: EVT_LOGT:0000001085:0x00000000:0125
[   19.203326] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[   19.203432] iwlagn 0000:03:00.0: Unable to initialize device.
[   19.264892] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   19.264897] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   19.264977] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[   19.264981] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[   19.264983] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   19.264986] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[   19.264988] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[   19.264991] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[   19.264993] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[   19.264995] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[   19.264997] iwlagn 0000:03:00.0: 0x00000000 | data1
[   19.264999] iwlagn 0000:03:00.0: 0x00000000 | data2
[   19.265001] iwlagn 0000:03:00.0: 0x00000616 | line
[   19.265003] iwlagn 0000:03:00.0: 0x00018BCC | beacon time
[   19.265005] iwlagn 0000:03:00.0: 0x00000434 | tsf low
[   19.265007] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[   19.265009] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[   19.265011] iwlagn 0000:03:00.0: 0x00000438 | time gp2
[   19.265013] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[   19.265015] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[   19.265016] iwlagn 0000:03:00.0: 0x0000006C | hw version
[   19.265019] iwlagn 0000:03:00.0: 0x00C80300 | board version
[   19.265021] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[   19.265023] iwlagn 0000:03:00.0: CSR values:
[   19.265024] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   19.265030] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   19.265035] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   19.265041] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[   19.265046] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   19.265051] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   19.265057] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[   19.265062] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[   19.265068] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   19.265074] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[   19.265079] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   19.265085] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   19.265090] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[   19.265095] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[   19.265100] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   19.265105] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   19.265111] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   19.265116] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   19.265122] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   19.265126] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   19.265132] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   19.265137] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   19.265143] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   19.265148] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   19.265150] iwlagn 0000:03:00.0: FH register values:
[   19.265164] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[   19.265178] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[   19.265192] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   19.265207] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   19.265221] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   19.265235] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   19.265249] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   19.265264] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   19.265278] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   19.265334] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[   19.265354] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   19.265365] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[   19.265377] iwlagn 0000:03:00.0: EVT_LOGT:0000001001:0x00000001:0071
[   19.265388] iwlagn 0000:03:00.0: EVT_LOGT:0000001077:0x00000002:0071
[   19.265399] iwlagn 0000:03:00.0: EVT_LOGT:0000001083:0x00000000:0125
[   19.265737] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[   19.265842] iwlagn 0000:03:00.0: Unable to initialize device.
[   19.283682] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   19.283686] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   19.283764] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[   19.283766] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[   19.283767] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[   19.283769] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[   19.283770] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[   19.283771] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[   19.283773] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[   19.283774] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[   19.283775] iwlagn 0000:03:00.0: 0x00000000 | data1
[   19.283777] iwlagn 0000:03:00.0: 0x00000000 | data2
[   19.283778] iwlagn 0000:03:00.0: 0x00000616 | line
[   19.283779] iwlagn 0000:03:00.0: 0x00018BCD | beacon time
[   19.283780] iwlagn 0000:03:00.0: 0x00000433 | tsf low
[   19.283782] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[   19.283783] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[   19.283784] iwlagn 0000:03:00.0: 0x00000437 | time gp2
[   19.283785] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[   19.283786] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[   19.283788] iwlagn 0000:03:00.0: 0x0000006C | hw version
[   19.283789] iwlagn 0000:03:00.0: 0x00C80300 | board version
[   19.283790] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[   19.283792] iwlagn 0000:03:00.0: CSR values:
[   19.283793] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   19.283798] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   19.283802] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[   19.283807] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[   19.283811] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[   19.283815] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   19.283820] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[   19.283824] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[   19.283829] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[   19.283834] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[   19.283839] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   19.283843] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[   19.283847] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[   19.283851] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[   19.283855] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   19.283860] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   19.283864] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   19.283868] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   19.283872] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[   19.283876] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   19.283881] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   19.283885] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   19.283889] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   19.283893] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   19.283895] iwlagn 0000:03:00.0: FH register values:
[   19.283908] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[   19.283921] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[   19.283934] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   19.283948] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   19.283961] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   19.283974] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   19.283988] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   19.284001] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   19.284014] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   19.284068] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[   19.284086] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   19.284097] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[   19.284107] iwlagn 0000:03:00.0: EVT_LOGT:0000001000:0x00000001:0071
[   19.284118] iwlagn 0000:03:00.0: EVT_LOGT:0000001076:0x00000002:0071
[   19.284129] iwlagn 0000:03:00.0: EVT_LOGT:0000001082:0x00000000:0125
[   19.284540] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[   19.284657] iwlagn 0000:03:00.0: Unable to initialize device.
[ 5054.591482] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 5054.591520] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8000004)
[ 5054.591529] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 5054.591540] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 5058.489359] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 5058.489363] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 5058.489441] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[ 5058.489443] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[ 5058.489444] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[ 5058.489446] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[ 5058.489447] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[ 5058.489448] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[ 5058.489449] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[ 5058.489451] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[ 5058.489452] iwlagn 0000:03:00.0: 0x00000000 | data1
[ 5058.489453] iwlagn 0000:03:00.0: 0x00000000 | data2
[ 5058.489454] iwlagn 0000:03:00.0: 0x00000616 | line
[ 5058.489455] iwlagn 0000:03:00.0: 0x00018BC7 | beacon time
[ 5058.489457] iwlagn 0000:03:00.0: 0x00000439 | tsf low
[ 5058.489458] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[ 5058.489459] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[ 5058.489460] iwlagn 0000:03:00.0: 0x0000043E | time gp2
[ 5058.489461] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[ 5058.489462] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[ 5058.489464] iwlagn 0000:03:00.0: 0x0000006C | hw version
[ 5058.489465] iwlagn 0000:03:00.0: 0x00C80300 | board version
[ 5058.489466] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[ 5058.489468] iwlagn 0000:03:00.0: CSR values:
[ 5058.489469] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 5058.489473] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 5058.489478] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[ 5058.489482] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[ 5058.489486] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 5058.489490] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 5058.489494] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 5058.489498] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 5058.489503] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 5058.489507] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[ 5058.489511] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 5058.489515] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[ 5058.489519] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 5058.489523] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[ 5058.489528] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 5058.489532] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 5058.489537] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 5058.489541] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 5058.489546] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[ 5058.489550] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 5058.489555] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 5058.489559] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[ 5058.489563] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 5058.489567] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 5058.489569] iwlagn 0000:03:00.0: FH register values:
[ 5058.489582] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[ 5058.489595] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[ 5058.489608] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 5058.489621] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[ 5058.489634] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 5058.489648] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 5058.489661] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 5058.489674] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 5058.489688] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 5058.489742] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[ 5058.489759] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 5058.489770] iwlagn 0000:03:00.0: EVT_LOGT:0000000022:0x00000000:1208
[ 5058.489780] iwlagn 0000:03:00.0: EVT_LOGT:0000001007:0x00000001:0071
[ 5058.489790] iwlagn 0000:03:00.0: EVT_LOGT:0000001083:0x00000002:0071
[ 5058.489800] iwlagn 0000:03:00.0: EVT_LOGT:0000001089:0x00000000:0125
[ 5058.490213] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[ 5058.490348] iwlagn 0000:03:00.0: Unable to initialize device.
[ 5058.533967] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 5058.533970] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 5058.534048] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[ 5058.534049] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[ 5058.534051] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[ 5058.534053] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[ 5058.534054] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[ 5058.534055] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[ 5058.534056] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[ 5058.534057] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[ 5058.534059] iwlagn 0000:03:00.0: 0x00000000 | data1
[ 5058.534060] iwlagn 0000:03:00.0: 0x00000000 | data2
[ 5058.534061] iwlagn 0000:03:00.0: 0x00000616 | line
[ 5058.534062] iwlagn 0000:03:00.0: 0x00018BCB | beacon time
[ 5058.534063] iwlagn 0000:03:00.0: 0x00000435 | tsf low
[ 5058.534064] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[ 5058.534065] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[ 5058.534067] iwlagn 0000:03:00.0: 0x00000439 | time gp2
[ 5058.534068] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[ 5058.534069] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[ 5058.534070] iwlagn 0000:03:00.0: 0x0000006C | hw version
[ 5058.534071] iwlagn 0000:03:00.0: 0x00C80300 | board version
[ 5058.534073] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[ 5058.534074] iwlagn 0000:03:00.0: CSR values:
[ 5058.534075] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 5058.534080] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 5058.534084] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[ 5058.534088] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[ 5058.534093] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 5058.534097] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 5058.534102] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 5058.534106] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 5058.534110] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 5058.534114] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[ 5058.534118] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 5058.534122] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[ 5058.534127] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 5058.534131] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[ 5058.534135] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 5058.534139] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 5058.534144] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 5058.534148] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 5058.534152] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[ 5058.534157] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 5058.534160] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 5058.534165] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 5058.534169] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 5058.534174] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 5058.534175] iwlagn 0000:03:00.0: FH register values:
[ 5058.534189] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[ 5058.534202] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[ 5058.534214] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 5058.534227] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[ 5058.534240] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 5058.534254] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 5058.534267] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 5058.534281] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 5058.534294] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 5058.534348] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[ 5058.534366] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 5058.534376] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 5058.534386] iwlagn 0000:03:00.0: EVT_LOGT:0000001002:0x00000001:0071
[ 5058.534397] iwlagn 0000:03:00.0: EVT_LOGT:0000001078:0x00000002:0071
[ 5058.534408] iwlagn 0000:03:00.0: EVT_LOGT:0000001084:0x00000000:0125
[ 5058.534801] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[ 5058.534906] iwlagn 0000:03:00.0: Unable to initialize device.
[ 5058.550569] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 5058.550571] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 5058.550648] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[ 5058.550650] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[ 5058.550651] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[ 5058.550653] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[ 5058.550654] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[ 5058.550655] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[ 5058.550656] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[ 5058.550658] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[ 5058.550659] iwlagn 0000:03:00.0: 0x00000000 | data1
[ 5058.550660] iwlagn 0000:03:00.0: 0x00000000 | data2
[ 5058.550661] iwlagn 0000:03:00.0: 0x00000616 | line
[ 5058.550662] iwlagn 0000:03:00.0: 0x00018BCA | beacon time
[ 5058.550663] iwlagn 0000:03:00.0: 0x00000436 | tsf low
[ 5058.550664] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[ 5058.550665] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[ 5058.550667] iwlagn 0000:03:00.0: 0x0000043B | time gp2
[ 5058.550668] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[ 5058.550669] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[ 5058.550670] iwlagn 0000:03:00.0: 0x0000006C | hw version
[ 5058.550671] iwlagn 0000:03:00.0: 0x00C80300 | board version
[ 5058.550673] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[ 5058.550674] iwlagn 0000:03:00.0: CSR values:
[ 5058.550675] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 5058.550679] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 5058.550684] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[ 5058.550688] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[ 5058.550693] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 5058.550697] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 5058.550702] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 5058.550706] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 5058.550711] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 5058.550715] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[ 5058.550720] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 5058.550724] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[ 5058.550729] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 5058.550733] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[ 5058.550738] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 5058.550742] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 5058.550746] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 5058.550751] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 5058.550755] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[ 5058.550760] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 5058.550764] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 5058.550769] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 5058.550773] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 5058.550777] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 5058.550778] iwlagn 0000:03:00.0: FH register values:
[ 5058.550791] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[ 5058.550804] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[ 5058.550817] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 5058.550830] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[ 5058.550844] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 5058.550857] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 5058.550870] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 5058.550883] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 5058.550897] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 5058.550951] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[ 5058.550968] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 5058.550979] iwlagn 0000:03:00.0: EVT_LOGT:0000000022:0x00000000:1208
[ 5058.550989] iwlagn 0000:03:00.0: EVT_LOGT:0000001004:0x00000001:0071
[ 5058.550999] iwlagn 0000:03:00.0: EVT_LOGT:0000001080:0x00000002:0071
[ 5058.551010] iwlagn 0000:03:00.0: EVT_LOGT:0000001086:0x00000000:0125
[ 5058.551401] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[ 5058.551504] iwlagn 0000:03:00.0: Unable to initialize device.
[ 6314.470997] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 6314.471035] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8000004)
[ 6314.471044] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 6314.471055] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[ 6318.404784] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 6318.404788] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 6318.404866] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[ 6318.404867] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[ 6318.404869] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[ 6318.404870] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[ 6318.404872] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[ 6318.404873] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[ 6318.404874] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[ 6318.404875] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[ 6318.404876] iwlagn 0000:03:00.0: 0x00000000 | data1
[ 6318.404878] iwlagn 0000:03:00.0: 0x00000000 | data2
[ 6318.404879] iwlagn 0000:03:00.0: 0x00000616 | line
[ 6318.404880] iwlagn 0000:03:00.0: 0x00018BCD | beacon time
[ 6318.404881] iwlagn 0000:03:00.0: 0x00000433 | tsf low
[ 6318.404882] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[ 6318.404883] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[ 6318.404885] iwlagn 0000:03:00.0: 0x00000437 | time gp2
[ 6318.404886] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[ 6318.404887] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[ 6318.404888] iwlagn 0000:03:00.0: 0x0000006C | hw version
[ 6318.404889] iwlagn 0000:03:00.0: 0x00C80300 | board version
[ 6318.404891] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[ 6318.404892] iwlagn 0000:03:00.0: CSR values:
[ 6318.404893] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 6318.404898] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 6318.404902] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[ 6318.404907] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[ 6318.404911] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 6318.404915] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 6318.404919] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 6318.404924] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 6318.404928] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 6318.404932] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[ 6318.404936] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 6318.404941] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[ 6318.404945] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 6318.404949] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[ 6318.404953] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 6318.404958] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 6318.404962] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 6318.404966] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 6318.404970] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[ 6318.404975] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 6318.404979] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 6318.404983] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[ 6318.404987] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 6318.404992] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 6318.404993] iwlagn 0000:03:00.0: FH register values:
[ 6318.405006] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[ 6318.405019] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[ 6318.405033] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 6318.405046] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[ 6318.405060] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 6318.405073] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 6318.405086] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 6318.405099] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 6318.405112] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 6318.405166] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[ 6318.405184] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 6318.405194] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 6318.405204] iwlagn 0000:03:00.0: EVT_LOGT:0000001000:0x00000001:0071
[ 6318.405214] iwlagn 0000:03:00.0: EVT_LOGT:0000001076:0x00000002:0071
[ 6318.405224] iwlagn 0000:03:00.0: EVT_LOGT:0000001082:0x00000000:0125
[ 6318.405634] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[ 6318.405778] iwlagn 0000:03:00.0: Unable to initialize device.
[ 6318.449334] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 6318.449337] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 6318.449414] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[ 6318.449416] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[ 6318.449417] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[ 6318.449419] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[ 6318.449420] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[ 6318.449421] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[ 6318.449422] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[ 6318.449424] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[ 6318.449425] iwlagn 0000:03:00.0: 0x00000000 | data1
[ 6318.449426] iwlagn 0000:03:00.0: 0x00000000 | data2
[ 6318.449427] iwlagn 0000:03:00.0: 0x00000616 | line
[ 6318.449428] iwlagn 0000:03:00.0: 0x00018BCB | beacon time
[ 6318.449430] iwlagn 0000:03:00.0: 0x00000435 | tsf low
[ 6318.449431] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[ 6318.449432] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[ 6318.449433] iwlagn 0000:03:00.0: 0x00000439 | time gp2
[ 6318.449434] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[ 6318.449435] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[ 6318.449437] iwlagn 0000:03:00.0: 0x0000006C | hw version
[ 6318.449438] iwlagn 0000:03:00.0: 0x00C80300 | board version
[ 6318.449439] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[ 6318.449440] iwlagn 0000:03:00.0: CSR values:
[ 6318.449441] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 6318.449446] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 6318.449450] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[ 6318.449454] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[ 6318.449458] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 6318.449462] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 6318.449467] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 6318.449471] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 6318.449475] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 6318.449479] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[ 6318.449484] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 6318.449488] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[ 6318.449492] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 6318.449496] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[ 6318.449501] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 6318.449505] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 6318.449509] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 6318.449514] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 6318.449518] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[ 6318.449523] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 6318.449527] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 6318.449532] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 6318.449536] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 6318.449541] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 6318.449542] iwlagn 0000:03:00.0: FH register values:
[ 6318.449555] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[ 6318.449567] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[ 6318.449580] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 6318.449594] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[ 6318.449607] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 6318.449620] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 6318.449634] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 6318.449647] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 6318.449660] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 6318.449714] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[ 6318.449732] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 6318.449742] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 6318.449752] iwlagn 0000:03:00.0: EVT_LOGT:0000001002:0x00000001:0071
[ 6318.449762] iwlagn 0000:03:00.0: EVT_LOGT:0000001078:0x00000002:0071
[ 6318.449773] iwlagn 0000:03:00.0: EVT_LOGT:0000001084:0x00000000:0125
[ 6318.450165] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[ 6318.450269] iwlagn 0000:03:00.0: Unable to initialize device.
[ 6318.465990] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 6318.465991] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 6318.466068] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[ 6318.466070] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[ 6318.466071] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[ 6318.466073] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[ 6318.466074] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[ 6318.466075] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[ 6318.466076] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[ 6318.466077] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[ 6318.466079] iwlagn 0000:03:00.0: 0x00000000 | data1
[ 6318.466080] iwlagn 0000:03:00.0: 0x00000000 | data2
[ 6318.466081] iwlagn 0000:03:00.0: 0x00000616 | line
[ 6318.466082] iwlagn 0000:03:00.0: 0x00018BCC | beacon time
[ 6318.466083] iwlagn 0000:03:00.0: 0x00000434 | tsf low
[ 6318.466084] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[ 6318.466085] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[ 6318.466087] iwlagn 0000:03:00.0: 0x00000438 | time gp2
[ 6318.466088] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[ 6318.466089] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[ 6318.466090] iwlagn 0000:03:00.0: 0x0000006C | hw version
[ 6318.466091] iwlagn 0000:03:00.0: 0x00C80300 | board version
[ 6318.466092] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[ 6318.466093] iwlagn 0000:03:00.0: CSR values:
[ 6318.466095] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 6318.466099] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 6318.466104] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[ 6318.466108] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[ 6318.466112] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[ 6318.466116] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 6318.466120] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[ 6318.466125] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[ 6318.466130] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 6318.466134] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[ 6318.466138] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 6318.466143] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[ 6318.466147] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 6318.466152] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[ 6318.466156] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 6318.466161] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 6318.466165] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 6318.466169] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 6318.466174] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[ 6318.466178] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 6318.466183] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 6318.466187] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 6318.466192] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 6318.466196] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 6318.466197] iwlagn 0000:03:00.0: FH register values:
[ 6318.466210] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[ 6318.466223] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[ 6318.466236] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 6318.466249] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[ 6318.466262] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 6318.466275] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 6318.466288] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 6318.466300] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 6318.466313] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 6318.466366] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[ 6318.466384] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 6318.466395] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 6318.466405] iwlagn 0000:03:00.0: EVT_LOGT:0000001001:0x00000001:0071
[ 6318.466415] iwlagn 0000:03:00.0: EVT_LOGT:0000001077:0x00000002:0071
[ 6318.466425] iwlagn 0000:03:00.0: EVT_LOGT:0000001083:0x00000000:0125
[ 6318.466818] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[ 6318.466919] iwlagn 0000:03:00.0: Unable to initialize device.
[19744.147096] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[19744.147135] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8000004)
[19744.147143] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[19744.147154] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[19749.540902] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[19749.540930] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[19749.541051] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[19749.541060] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[19749.541070] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[19749.541089] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[19749.541096] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[19749.541104] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[19749.541123] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[19749.541130] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[19749.541137] iwlagn 0000:03:00.0: 0x00000000 | data1
[19749.541144] iwlagn 0000:03:00.0: 0x00000000 | data2
[19749.541162] iwlagn 0000:03:00.0: 0x00000616 | line
[19749.541169] iwlagn 0000:03:00.0: 0x00018BCB | beacon time
[19749.541176] iwlagn 0000:03:00.0: 0x00000435 | tsf low
[19749.541184] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[19749.541191] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[19749.541210] iwlagn 0000:03:00.0: 0x00000439 | time gp2
[19749.541217] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[19749.541224] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[19749.541243] iwlagn 0000:03:00.0: 0x0000006C | hw version
[19749.541250] iwlagn 0000:03:00.0: 0x00C80300 | board version
[19749.541258] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[19749.541265] iwlagn 0000:03:00.0: CSR values:
[19749.541283] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[19749.541296] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[19749.541308] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[19749.541331] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[19749.541343] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[19749.541365] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[19749.541377] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[19749.541389] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[19749.541412] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[19749.541423] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[19749.541445] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[19749.541456] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[19749.541468] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[19749.541491] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[19749.541502] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[19749.541525] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[19749.541536] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[19749.541547] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[19749.541569] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[19749.541580] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[19749.541603] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[19749.541615] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[19749.541626] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[19749.541646] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[19749.541654] iwlagn 0000:03:00.0: FH register values:
[19749.541687] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[19749.541709] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[19749.541741] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[19749.541773] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[19749.541806] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[19749.541828] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[19749.541859] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[19749.541890] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[19749.541911] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[19749.542005] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[19749.542045] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[19749.542063] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[19749.542091] iwlagn 0000:03:00.0: EVT_LOGT:0000001002:0x00000001:0071
[19749.542109] iwlagn 0000:03:00.0: EVT_LOGT:0000001078:0x00000002:0071
[19749.542138] iwlagn 0000:03:00.0: EVT_LOGT:0000001084:0x00000000:0125
[19749.542568] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[19749.542694] iwlagn 0000:03:00.0: Unable to initialize device.
[19749.579219] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[19749.579246] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[19749.579396] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[19749.579405] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[19749.579414] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[19749.579422] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[19749.579441] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[19749.579448] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[19749.579455] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[19749.579461] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[19749.579479] iwlagn 0000:03:00.0: 0x00000000 | data1
[19749.579486] iwlagn 0000:03:00.0: 0x00000000 | data2
[19749.579493] iwlagn 0000:03:00.0: 0x00000616 | line
[19749.579499] iwlagn 0000:03:00.0: 0x00018BCA | beacon time
[19749.579517] iwlagn 0000:03:00.0: 0x00000436 | tsf low
[19749.579524] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[19749.579531] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[19749.579538] iwlagn 0000:03:00.0: 0x0000043B | time gp2
[19749.579555] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[19749.579562] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[19749.579570] iwlagn 0000:03:00.0: 0x0000006C | hw version
[19749.579577] iwlagn 0000:03:00.0: 0x00C80300 | board version
[19749.579595] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[19749.579602] iwlagn 0000:03:00.0: CSR values:
[19749.579608] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[19749.579621] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[19749.579643] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[19749.579654] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[19749.579677] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[19749.579688] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[19749.579698] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[19749.579718] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[19749.579729] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[19749.579740] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[19749.579761] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[19749.579772] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[19749.579783] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[19749.579805] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[19749.579816] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[19749.579838] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[19749.579848] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[19749.579859] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[19749.579878] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[19749.579889] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[19749.579900] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[19749.579922] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[19749.579933] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[19749.579943] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[19749.579962] iwlagn 0000:03:00.0: FH register values:
[19749.579982] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[19749.580013] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[19749.580045] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[19749.580077] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[19749.580097] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[19749.580128] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[19749.580159] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[19749.580180] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[19749.580212] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[19749.580294] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[19749.580326] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[19749.580343] iwlagn 0000:03:00.0: EVT_LOGT:0000000022:0x00000000:1208
[19749.580373] iwlagn 0000:03:00.0: EVT_LOGT:0000001004:0x00000001:0071
[19749.580400] iwlagn 0000:03:00.0: EVT_LOGT:0000001080:0x00000002:0071
[19749.580417] iwlagn 0000:03:00.0: EVT_LOGT:0000001086:0x00000000:0125
[19749.580850] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[19749.580980] iwlagn 0000:03:00.0: Unable to initialize device.
[19749.609535] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[19749.609560] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[19749.609681] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[19749.609689] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[19749.609698] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[19749.609717] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[19749.609724] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[19749.609731] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[19749.609738] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[19749.609756] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[19749.609762] iwlagn 0000:03:00.0: 0x00000000 | data1
[19749.609768] iwlagn 0000:03:00.0: 0x00000000 | data2
[19749.609775] iwlagn 0000:03:00.0: 0x00000616 | line
[19749.609792] iwlagn 0000:03:00.0: 0x00018BCB | beacon time
[19749.609798] iwlagn 0000:03:00.0: 0x00000435 | tsf low
[19749.609804] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[19749.609810] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[19749.609816] iwlagn 0000:03:00.0: 0x0000043A | time gp2
[19749.609833] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[19749.609839] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[19749.609845] iwlagn 0000:03:00.0: 0x0000006C | hw version
[19749.609851] iwlagn 0000:03:00.0: 0x00C80300 | board version
[19749.609857] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[19749.609874] iwlagn 0000:03:00.0: CSR values:
[19749.609882] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[19749.609895] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[19749.609918] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[19749.609930] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[19749.609953] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[19749.609964] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[19749.609976] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[19749.609999] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[19749.610010] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[19749.610033] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[19749.610045] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[19749.610057] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[19749.610080] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[19749.610091] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[19749.610113] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[19749.610124] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[19749.610136] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[19749.610159] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[19749.610170] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[19749.610192] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[19749.610203] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[19749.610215] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[19749.610234] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[19749.610245] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[19749.610253] iwlagn 0000:03:00.0: FH register values:
[19749.610284] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[19749.610315] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[19749.610337] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[19749.610370] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[19749.610401] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[19749.610433] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[19749.610454] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[19749.610484] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[19749.610515] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[19749.610598] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[19749.610636] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[19749.610655] iwlagn 0000:03:00.0: EVT_LOGT:0000000022:0x00000000:1208
[19749.610682] iwlagn 0000:03:00.0: EVT_LOGT:0000001003:0x00000001:0071
[19749.610699] iwlagn 0000:03:00.0: EVT_LOGT:0000001079:0x00000002:0071
[19749.610728] iwlagn 0000:03:00.0: EVT_LOGT:0000001085:0x00000000:0125
[19749.611195] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[19749.611403] iwlagn 0000:03:00.0: Unable to initialize device.
[21892.087853] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[21892.087891] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8000004)
[21892.087900] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[21892.087911] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[21896.318955] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[21896.318961] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[21896.319040] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[21896.319043] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[21896.319046] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[21896.319049] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[21896.319051] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[21896.319053] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[21896.319055] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[21896.319058] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[21896.319060] iwlagn 0000:03:00.0: 0x00000000 | data1
[21896.319062] iwlagn 0000:03:00.0: 0x00000000 | data2
[21896.319064] iwlagn 0000:03:00.0: 0x00000616 | line
[21896.319066] iwlagn 0000:03:00.0: 0x00018BCA | beacon time
[21896.319068] iwlagn 0000:03:00.0: 0x00000436 | tsf low
[21896.319070] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[21896.319072] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[21896.319075] iwlagn 0000:03:00.0: 0x0000043A | time gp2
[21896.319077] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[21896.319079] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[21896.319081] iwlagn 0000:03:00.0: 0x0000006C | hw version
[21896.319084] iwlagn 0000:03:00.0: 0x00C80300 | board version
[21896.319086] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[21896.319088] iwlagn 0000:03:00.0: CSR values:
[21896.319090] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[21896.319096] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[21896.319101] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[21896.319107] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[21896.319112] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[21896.319118] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[21896.319123] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[21896.319129] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[21896.319134] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[21896.319140] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[21896.319146] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[21896.319152] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[21896.319158] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[21896.319163] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[21896.319169] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[21896.319174] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[21896.319179] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[21896.319184] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[21896.319190] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[21896.319195] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[21896.319201] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[21896.319206] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[21896.319211] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[21896.319217] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[21896.319219] iwlagn 0000:03:00.0: FH register values:
[21896.319234] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[21896.319248] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[21896.319263] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[21896.319277] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[21896.319291] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[21896.319306] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[21896.319320] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[21896.319335] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[21896.319349] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[21896.319409] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[21896.319428] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[21896.319439] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[21896.319451] iwlagn 0000:03:00.0: EVT_LOGT:0000001003:0x00000001:0071
[21896.319462] iwlagn 0000:03:00.0: EVT_LOGT:0000001079:0x00000002:0071
[21896.319474] iwlagn 0000:03:00.0: EVT_LOGT:0000001085:0x00000000:0125
[21896.319768] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[21896.319849] iwlagn 0000:03:00.0: Unable to initialize device.
[21896.347393] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[21896.347398] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[21896.347477] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[21896.347480] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[21896.347483] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[21896.347485] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[21896.347487] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[21896.347490] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[21896.347492] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[21896.347494] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[21896.347496] iwlagn 0000:03:00.0: 0x00000000 | data1
[21896.347498] iwlagn 0000:03:00.0: 0x00000000 | data2
[21896.347500] iwlagn 0000:03:00.0: 0x00000616 | line
[21896.347502] iwlagn 0000:03:00.0: 0x00018BCA | beacon time
[21896.347504] iwlagn 0000:03:00.0: 0x00000436 | tsf low
[21896.347506] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[21896.347508] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[21896.347511] iwlagn 0000:03:00.0: 0x0000043A | time gp2
[21896.347513] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[21896.347515] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[21896.347517] iwlagn 0000:03:00.0: 0x0000006C | hw version
[21896.347519] iwlagn 0000:03:00.0: 0x00C80300 | board version
[21896.347521] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[21896.347523] iwlagn 0000:03:00.0: CSR values:
[21896.347525] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[21896.347531] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[21896.347537] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[21896.347542] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[21896.347547] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[21896.347553] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[21896.347558] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[21896.347563] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[21896.347569] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[21896.347574] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[21896.347579] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[21896.347584] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[21896.347590] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[21896.347596] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[21896.347601] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[21896.347606] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[21896.347611] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[21896.347616] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[21896.347622] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[21896.347627] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[21896.347633] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[21896.347638] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[21896.347644] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[21896.347649] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[21896.347651] iwlagn 0000:03:00.0: FH register values:
[21896.347665] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[21896.347680] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[21896.347694] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[21896.347709] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[21896.347723] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[21896.347737] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[21896.347752] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[21896.347766] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[21896.347780] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[21896.347836] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[21896.347856] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[21896.347868] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[21896.347880] iwlagn 0000:03:00.0: EVT_LOGT:0000001003:0x00000001:0071
[21896.347891] iwlagn 0000:03:00.0: EVT_LOGT:0000001079:0x00000002:0071
[21896.347904] iwlagn 0000:03:00.0: EVT_LOGT:0000001085:0x00000000:0125
[21896.348703] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[21896.348787] iwlagn 0000:03:00.0: Unable to initialize device.
[21896.367063] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[21896.367067] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[21896.367145] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[21896.367147] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[21896.367148] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[21896.367150] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[21896.367151] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[21896.367152] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[21896.367154] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[21896.367155] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[21896.367156] iwlagn 0000:03:00.0: 0x00000000 | data1
[21896.367157] iwlagn 0000:03:00.0: 0x00000000 | data2
[21896.367159] iwlagn 0000:03:00.0: 0x00000616 | line
[21896.367160] iwlagn 0000:03:00.0: 0x00018BCC | beacon time
[21896.367161] iwlagn 0000:03:00.0: 0x00000434 | tsf low
[21896.367163] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[21896.367164] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[21896.367165] iwlagn 0000:03:00.0: 0x00000438 | time gp2
[21896.367166] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[21896.367168] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[21896.367169] iwlagn 0000:03:00.0: 0x0000006C | hw version
[21896.367170] iwlagn 0000:03:00.0: 0x00C80300 | board version
[21896.367171] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[21896.367173] iwlagn 0000:03:00.0: CSR values:
[21896.367174] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[21896.367179] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[21896.367183] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[21896.367188] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[21896.367192] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[21896.367197] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[21896.367202] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[21896.367206] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[21896.367211] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[21896.367216] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[21896.367220] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[21896.367225] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[21896.367229] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[21896.367234] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[21896.367239] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[21896.367243] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[21896.367248] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[21896.367252] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[21896.367257] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[21896.367262] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[21896.367266] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[21896.367271] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[21896.367276] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[21896.367280] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[21896.367282] iwlagn 0000:03:00.0: FH register values:
[21896.367295] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[21896.367308] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[21896.367321] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[21896.367334] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[21896.367348] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[21896.367361] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[21896.367374] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[21896.367388] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[21896.367401] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[21896.367455] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[21896.367473] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[21896.367483] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[21896.367494] iwlagn 0000:03:00.0: EVT_LOGT:0000001001:0x00000001:0071
[21896.367504] iwlagn 0000:03:00.0: EVT_LOGT:0000001077:0x00000002:0071
[21896.367515] iwlagn 0000:03:00.0: EVT_LOGT:0000001083:0x00000000:0125
[21896.367813] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[21896.367893] iwlagn 0000:03:00.0: Unable to initialize device.
[26078.260839] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[26078.260878] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8000004)
[26078.260886] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[26078.260897] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[26082.387487] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[26082.387491] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[26082.387569] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[26082.387570] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[26082.387572] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[26082.387574] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[26082.387575] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[26082.387576] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[26082.387578] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[26082.387579] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[26082.387580] iwlagn 0000:03:00.0: 0x00000000 | data1
[26082.387581] iwlagn 0000:03:00.0: 0x00000000 | data2
[26082.387582] iwlagn 0000:03:00.0: 0x00000616 | line
[26082.387583] iwlagn 0000:03:00.0: 0x00018BCB | beacon time
[26082.387585] iwlagn 0000:03:00.0: 0x00000435 | tsf low
[26082.387586] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[26082.387587] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[26082.387588] iwlagn 0000:03:00.0: 0x00000439 | time gp2
[26082.387589] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[26082.387590] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[26082.387592] iwlagn 0000:03:00.0: 0x0000006C | hw version
[26082.387593] iwlagn 0000:03:00.0: 0x00C80300 | board version
[26082.387594] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[26082.387595] iwlagn 0000:03:00.0: CSR values:
[26082.387597] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[26082.387602] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[26082.387606] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[26082.387611] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[26082.387615] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[26082.387620] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[26082.387625] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[26082.387629] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[26082.387634] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[26082.387638] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[26082.387643] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[26082.387647] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[26082.387652] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[26082.387656] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[26082.387661] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[26082.387665] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[26082.387670] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[26082.387674] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[26082.387679] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[26082.387683] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[26082.387688] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[26082.387692] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[26082.387697] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[26082.387701] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[26082.387703] iwlagn 0000:03:00.0: FH register values:
[26082.387716] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[26082.387729] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[26082.387741] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[26082.387754] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[26082.387767] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[26082.387780] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[26082.387792] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[26082.387805] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[26082.387818] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[26082.387872] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[26082.387890] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[26082.387900] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[26082.387910] iwlagn 0000:03:00.0: EVT_LOGT:0000001002:0x00000001:0071
[26082.387920] iwlagn 0000:03:00.0: EVT_LOGT:0000001078:0x00000002:0071
[26082.387931] iwlagn 0000:03:00.0: EVT_LOGT:0000001084:0x00000000:0125
[26082.388261] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[26082.388339] iwlagn 0000:03:00.0: Unable to initialize device.
[26082.415946] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[26082.415951] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[26082.416029] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[26082.416031] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[26082.416033] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[26082.416035] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[26082.416036] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[26082.416037] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[26082.416039] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[26082.416040] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[26082.416041] iwlagn 0000:03:00.0: 0x00000000 | data1
[26082.416043] iwlagn 0000:03:00.0: 0x00000000 | data2
[26082.416044] iwlagn 0000:03:00.0: 0x00000616 | line
[26082.416045] iwlagn 0000:03:00.0: 0x00018BCB | beacon time
[26082.416046] iwlagn 0000:03:00.0: 0x00000435 | tsf low
[26082.416048] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[26082.416049] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[26082.416050] iwlagn 0000:03:00.0: 0x0000043A | time gp2
[26082.416052] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[26082.416053] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[26082.416054] iwlagn 0000:03:00.0: 0x0000006C | hw version
[26082.416056] iwlagn 0000:03:00.0: 0x00C80300 | board version
[26082.416057] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[26082.416058] iwlagn 0000:03:00.0: CSR values:
[26082.416059] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[26082.416065] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[26082.416069] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[26082.416073] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[26082.416077] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[26082.416081] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[26082.416086] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[26082.416090] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[26082.416094] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[26082.416098] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[26082.416103] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[26082.416107] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[26082.416111] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[26082.416115] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[26082.416119] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[26082.416124] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[26082.416128] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[26082.416132] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[26082.416136] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[26082.416141] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[26082.416145] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[26082.416149] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[26082.416153] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[26082.416158] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[26082.416159] iwlagn 0000:03:00.0: FH register values:
[26082.416172] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[26082.416186] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[26082.416199] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[26082.416212] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[26082.416226] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[26082.416239] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[26082.416252] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[26082.416265] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[26082.416278] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[26082.416333] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[26082.416351] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[26082.416361] iwlagn 0000:03:00.0: EVT_LOGT:0000000022:0x00000000:1208
[26082.416372] iwlagn 0000:03:00.0: EVT_LOGT:0000001003:0x00000001:0071
[26082.416383] iwlagn 0000:03:00.0: EVT_LOGT:0000001079:0x00000002:0071
[26082.416393] iwlagn 0000:03:00.0: EVT_LOGT:0000001085:0x00000000:0125
[26082.416869] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[26082.416945] iwlagn 0000:03:00.0: Unable to initialize device.
[26082.433403] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[26082.433408] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[26082.433488] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[26082.433490] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[26082.433493] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[26082.433495] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[26082.433497] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[26082.433499] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[26082.433501] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[26082.433503] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[26082.433504] iwlagn 0000:03:00.0: 0x00000000 | data1
[26082.433506] iwlagn 0000:03:00.0: 0x00000000 | data2
[26082.433508] iwlagn 0000:03:00.0: 0x00000616 | line
[26082.433509] iwlagn 0000:03:00.0: 0x00018BC9 | beacon time
[26082.433511] iwlagn 0000:03:00.0: 0x00000437 | tsf low
[26082.433513] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[26082.433514] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[26082.433516] iwlagn 0000:03:00.0: 0x0000043B | time gp2
[26082.433518] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[26082.433520] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[26082.433522] iwlagn 0000:03:00.0: 0x0000006C | hw version
[26082.433524] iwlagn 0000:03:00.0: 0x00C80300 | board version
[26082.433525] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[26082.433527] iwlagn 0000:03:00.0: CSR values:
[26082.433529] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[26082.433535] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[26082.433540] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[26082.433544] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[26082.433550] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[26082.433555] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[26082.433561] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[26082.433565] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[26082.433571] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[26082.433576] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[26082.433581] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[26082.433585] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[26082.433591] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[26082.433596] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[26082.433601] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[26082.433606] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[26082.433610] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[26082.433615] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[26082.433620] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[26082.433624] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[26082.433629] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[26082.433634] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[26082.433639] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[26082.433643] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[26082.433645] iwlagn 0000:03:00.0: FH register values:
[26082.433674] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[26082.433698] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[26082.433712] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[26082.433728] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[26082.433742] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[26082.433756] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[26082.433770] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[26082.433784] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[26082.433798] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[26082.433854] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[26082.433873] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[26082.433884] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[26082.433895] iwlagn 0000:03:00.0: EVT_LOGT:0000001004:0x00000001:0071
[26082.433905] iwlagn 0000:03:00.0: EVT_LOGT:0000001080:0x00000002:0071
[26082.433916] iwlagn 0000:03:00.0: EVT_LOGT:0000001086:0x00000000:0125
[26082.434428] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[26082.434507] iwlagn 0000:03:00.0: Unable to initialize device.
[36457.458446] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[36457.458485] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8000004)
[36457.458493] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[36457.458504] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[36462.646453] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[36462.646460] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[36462.646542] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[36462.646547] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[36462.646551] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[36462.646555] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[36462.646559] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[36462.646562] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[36462.646566] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[36462.646569] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[36462.646572] iwlagn 0000:03:00.0: 0x00000000 | data1
[36462.646575] iwlagn 0000:03:00.0: 0x00000000 | data2
[36462.646578] iwlagn 0000:03:00.0: 0x00000616 | line
[36462.646581] iwlagn 0000:03:00.0: 0x00018BC9 | beacon time
[36462.646583] iwlagn 0000:03:00.0: 0x00000437 | tsf low
[36462.646586] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[36462.646588] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[36462.646591] iwlagn 0000:03:00.0: 0x0000043B | time gp2
[36462.646593] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[36462.646596] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[36462.646599] iwlagn 0000:03:00.0: 0x0000006C | hw version
[36462.646602] iwlagn 0000:03:00.0: 0x00C80300 | board version
[36462.646605] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[36462.646607] iwlagn 0000:03:00.0: CSR values:
[36462.646610] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[36462.646617] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[36462.646624] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[36462.646629] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[36462.646636] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[36462.646641] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[36462.646647] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[36462.646653] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[36462.646660] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[36462.646666] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[36462.646673] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[36462.646680] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[36462.646686] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[36462.646692] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[36462.646697] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[36462.646703] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[36462.646709] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[36462.646716] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[36462.646722] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[36462.646729] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[36462.646747] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[36462.646753] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[36462.646759] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[36462.646766] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[36462.646769] iwlagn 0000:03:00.0: FH register values:
[36462.646784] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[36462.646800] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[36462.646816] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[36462.646833] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[36462.646848] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[36462.646864] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[36462.646879] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[36462.646895] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[36462.646911] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[36462.646968] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[36462.646989] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[36462.647003] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[36462.647016] iwlagn 0000:03:00.0: EVT_LOGT:0000001004:0x00000001:0071
[36462.647029] iwlagn 0000:03:00.0: EVT_LOGT:0000001080:0x00000002:0071
[36462.647042] iwlagn 0000:03:00.0: EVT_LOGT:0000001086:0x00000000:0125
[36462.647674] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[36462.647756] iwlagn 0000:03:00.0: Unable to initialize device.
[36462.676715] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[36462.676722] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[36462.676806] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[36462.676810] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[36462.676814] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[36462.676817] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[36462.676821] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[36462.676824] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[36462.676827] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[36462.676830] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[36462.676834] iwlagn 0000:03:00.0: 0x00000000 | data1
[36462.676837] iwlagn 0000:03:00.0: 0x00000000 | data2
[36462.676840] iwlagn 0000:03:00.0: 0x00000616 | line
[36462.676843] iwlagn 0000:03:00.0: 0x00018BC9 | beacon time
[36462.676846] iwlagn 0000:03:00.0: 0x00000437 | tsf low
[36462.676849] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[36462.676852] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[36462.676855] iwlagn 0000:03:00.0: 0x0000043B | time gp2
[36462.676858] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[36462.676862] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[36462.676865] iwlagn 0000:03:00.0: 0x0000006C | hw version
[36462.676868] iwlagn 0000:03:00.0: 0x00C80300 | board version
[36462.676871] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[36462.676874] iwlagn 0000:03:00.0: CSR values:
[36462.676876] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[36462.676884] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[36462.676891] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[36462.676897] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[36462.676904] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[36462.676910] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[36462.676917] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[36462.676924] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[36462.676931] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[36462.676938] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[36462.676945] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[36462.676952] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[36462.676958] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[36462.676965] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[36462.676972] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[36462.676979] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[36462.676985] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[36462.676992] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[36462.676998] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[36462.677004] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[36462.677010] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[36462.677017] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[36462.677024] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[36462.677031] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[36462.677034] iwlagn 0000:03:00.0: FH register values:
[36462.677050] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[36462.677066] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[36462.677082] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[36462.677096] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[36462.677111] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[36462.677125] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[36462.677140] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[36462.677154] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[36462.677168] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[36462.677224] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[36462.677243] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[36462.677254] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[36462.677266] iwlagn 0000:03:00.0: EVT_LOGT:0000001004:0x00000001:0071
[36462.677277] iwlagn 0000:03:00.0: EVT_LOGT:0000001080:0x00000002:0071
[36462.677288] iwlagn 0000:03:00.0: EVT_LOGT:0000001086:0x00000000:0125
[36462.677597] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[36462.677680] iwlagn 0000:03:00.0: Unable to initialize device.
[36462.695157] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[36462.695165] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[36462.695246] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[36462.695249] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[36462.695253] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[36462.695256] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[36462.695258] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[36462.695261] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[36462.695264] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[36462.695266] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[36462.695269] iwlagn 0000:03:00.0: 0x00000000 | data1
[36462.695271] iwlagn 0000:03:00.0: 0x00000000 | data2
[36462.695274] iwlagn 0000:03:00.0: 0x00000616 | line
[36462.695276] iwlagn 0000:03:00.0: 0x00018BCB | beacon time
[36462.695279] iwlagn 0000:03:00.0: 0x00000435 | tsf low
[36462.695282] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[36462.695284] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[36462.695287] iwlagn 0000:03:00.0: 0x00000439 | time gp2
[36462.695289] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[36462.695292] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[36462.695295] iwlagn 0000:03:00.0: 0x0000006C | hw version
[36462.695298] iwlagn 0000:03:00.0: 0x00C80300 | board version
[36462.695300] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[36462.695303] iwlagn 0000:03:00.0: CSR values:
[36462.695305] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[36462.695312] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[36462.695318] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[36462.695324] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[36462.695330] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[36462.695336] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[36462.695342] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[36462.695348] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[36462.695354] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[36462.695360] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[36462.695366] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[36462.695372] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[36462.695377] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[36462.695384] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[36462.695390] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[36462.695395] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[36462.695401] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[36462.695407] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[36462.695413] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[36462.695418] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[36462.695424] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[36462.695430] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[36462.695436] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[36462.695442] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[36462.695445] iwlagn 0000:03:00.0: FH register values:
[36462.695459] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[36462.695475] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[36462.695490] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[36462.695505] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[36462.695521] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[36462.695536] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[36462.695552] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[36462.695567] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[36462.695582] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[36462.695638] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[36462.695658] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[36462.695671] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[36462.695683] iwlagn 0000:03:00.0: EVT_LOGT:0000001002:0x00000001:0071
[36462.695695] iwlagn 0000:03:00.0: EVT_LOGT:0000001078:0x00000002:0071
[36462.695707] iwlagn 0000:03:00.0: EVT_LOGT:0000001084:0x00000000:0125
[36462.696029] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[36462.696110] iwlagn 0000:03:00.0: Unable to initialize device.
[38242.521033] iwlagn 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[38242.521072] iwlagn 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8000004)
[38242.521080] iwlagn 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[38242.521091] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[38246.830080] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[38246.830085] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[38246.830172] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[38246.830174] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[38246.830177] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[38246.830179] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[38246.830181] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[38246.830182] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[38246.830184] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[38246.830186] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[38246.830188] iwlagn 0000:03:00.0: 0x00000000 | data1
[38246.830189] iwlagn 0000:03:00.0: 0x00000000 | data2
[38246.830191] iwlagn 0000:03:00.0: 0x00000616 | line
[38246.830193] iwlagn 0000:03:00.0: 0x00018BCA | beacon time
[38246.830194] iwlagn 0000:03:00.0: 0x00000436 | tsf low
[38246.830196] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[38246.830197] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[38246.830199] iwlagn 0000:03:00.0: 0x0000043A | time gp2
[38246.830201] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[38246.830202] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[38246.830204] iwlagn 0000:03:00.0: 0x0000006C | hw version
[38246.830206] iwlagn 0000:03:00.0: 0x00C80300 | board version
[38246.830208] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[38246.830210] iwlagn 0000:03:00.0: CSR values:
[38246.830211] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[38246.830217] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[38246.830222] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[38246.830227] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[38246.830232] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[38246.830237] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[38246.830241] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[38246.830246] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[38246.830251] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[38246.830255] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[38246.830260] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[38246.830265] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[38246.830270] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[38246.830275] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[38246.830280] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[38246.830285] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[38246.830289] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[38246.830294] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[38246.830299] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[38246.830303] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[38246.830308] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[38246.830313] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[38246.830318] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[38246.830322] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[38246.830324] iwlagn 0000:03:00.0: FH register values:
[38246.830338] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[38246.830351] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[38246.830366] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[38246.830380] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[38246.830393] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[38246.830407] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[38246.830420] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[38246.830434] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[38246.830448] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[38246.830503] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[38246.830521] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[38246.830533] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[38246.830544] iwlagn 0000:03:00.0: EVT_LOGT:0000001003:0x00000001:0071
[38246.830554] iwlagn 0000:03:00.0: EVT_LOGT:0000001079:0x00000002:0071
[38246.830565] iwlagn 0000:03:00.0: EVT_LOGT:0000001085:0x00000000:0125
[38246.830890] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[38246.830971] iwlagn 0000:03:00.0: Unable to initialize device.
[38246.858812] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[38246.858817] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[38246.858896] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[38246.858898] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[38246.858900] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[38246.858901] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[38246.858903] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[38246.858904] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[38246.858906] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[38246.858907] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[38246.858908] iwlagn 0000:03:00.0: 0x00000000 | data1
[38246.858909] iwlagn 0000:03:00.0: 0x00000000 | data2
[38246.858911] iwlagn 0000:03:00.0: 0x00000616 | line
[38246.858912] iwlagn 0000:03:00.0: 0x00018BC9 | beacon time
[38246.858913] iwlagn 0000:03:00.0: 0x00000437 | tsf low
[38246.858915] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[38246.858916] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[38246.858917] iwlagn 0000:03:00.0: 0x0000043C | time gp2
[38246.858919] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[38246.858920] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[38246.858921] iwlagn 0000:03:00.0: 0x0000006C | hw version
[38246.858923] iwlagn 0000:03:00.0: 0x00C80300 | board version
[38246.858924] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[38246.858926] iwlagn 0000:03:00.0: CSR values:
[38246.858928] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[38246.858933] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[38246.858938] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[38246.858943] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[38246.858948] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[38246.858953] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[38246.858958] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[38246.858963] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[38246.858969] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[38246.858974] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[38246.858978] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[38246.858983] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[38246.858988] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[38246.858993] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[38246.858998] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[38246.859002] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[38246.859007] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[38246.859012] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[38246.859018] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[38246.859023] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[38246.859028] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[38246.859033] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[38246.859038] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[38246.859044] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[38246.859046] iwlagn 0000:03:00.0: FH register values:
[38246.859060] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[38246.859075] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[38246.859089] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[38246.859104] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[38246.859118] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[38246.859133] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[38246.859147] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[38246.859161] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[38246.859176] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[38246.859232] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[38246.859251] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[38246.859262] iwlagn 0000:03:00.0: EVT_LOGT:0000000022:0x00000000:1208
[38246.859274] iwlagn 0000:03:00.0: EVT_LOGT:0000001005:0x00000001:0071
[38246.859285] iwlagn 0000:03:00.0: EVT_LOGT:0000001081:0x00000002:0071
[38246.859297] iwlagn 0000:03:00.0: EVT_LOGT:0000001087:0x00000000:0125
[38246.859599] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[38246.859678] iwlagn 0000:03:00.0: Unable to initialize device.
[38246.875924] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[38246.875930] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[38246.876009] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[38246.876011] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[38246.876013] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[38246.876014] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[38246.876016] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[38246.876017] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[38246.876018] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[38246.876020] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[38246.876021] iwlagn 0000:03:00.0: 0x00000000 | data1
[38246.876022] iwlagn 0000:03:00.0: 0x00000000 | data2
[38246.876024] iwlagn 0000:03:00.0: 0x00000616 | line
[38246.876025] iwlagn 0000:03:00.0: 0x00018BCA | beacon time
[38246.876026] iwlagn 0000:03:00.0: 0x00000436 | tsf low
[38246.876028] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[38246.876029] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[38246.876030] iwlagn 0000:03:00.0: 0x0000043A | time gp2
[38246.876032] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[38246.876033] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[38246.876035] iwlagn 0000:03:00.0: 0x0000006C | hw version
[38246.876036] iwlagn 0000:03:00.0: 0x00C80300 | board version
[38246.876037] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[38246.876039] iwlagn 0000:03:00.0: CSR values:
[38246.876040] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[38246.876045] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[38246.876049] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[38246.876054] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[38246.876058] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[38246.876062] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[38246.876066] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[38246.876071] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[38246.876075] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[38246.876079] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[38246.876083] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[38246.876087] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[38246.876092] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[38246.876096] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[38246.876100] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[38246.876104] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[38246.876109] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[38246.876113] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[38246.876117] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[38246.876122] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[38246.876126] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[38246.876130] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[38246.876135] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[38246.876139] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[38246.876140] iwlagn 0000:03:00.0: FH register values:
[38246.876153] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[38246.876167] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[38246.876180] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[38246.876193] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[38246.876207] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[38246.876220] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[38246.876233] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[38246.876247] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[38246.876260] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[38246.876314] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[38246.876332] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[38246.876343] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[38246.876353] iwlagn 0000:03:00.0: EVT_LOGT:0000001003:0x00000001:0071
[38246.876363] iwlagn 0000:03:00.0: EVT_LOGT:0000001079:0x00000002:0071
[38246.876374] iwlagn 0000:03:00.0: EVT_LOGT:0000001085:0x00000000:0125
[38246.876668] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[38246.876747] iwlagn 0000:03:00.0: Unable to initialize device.
[45189.267368] iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.
[45189.267379] iwlagn 0000:03:00.0: Loaded firmware version: 39.31.5.1 build 35138
[45189.267477] iwlagn 0000:03:00.0: Start IWL Error Log Dump:
[45189.267483] iwlagn 0000:03:00.0: Status: 0x00040224, count: 5
[45189.267489] iwlagn 0000:03:00.0: 0x00000005 | SYSASSERT                   
[45189.267495] iwlagn 0000:03:00.0: 0x00016E00 | uPc
[45189.267499] iwlagn 0000:03:00.0: 0x00016E00 | branchlink1
[45189.267503] iwlagn 0000:03:00.0: 0x00016E00 | branchlink2
[45189.267508] iwlagn 0000:03:00.0: 0x00000000 | interruptlink1
[45189.267512] iwlagn 0000:03:00.0: 0x00000000 | interruptlink2
[45189.267517] iwlagn 0000:03:00.0: 0x00000000 | data1
[45189.267521] iwlagn 0000:03:00.0: 0x00000000 | data2
[45189.267525] iwlagn 0000:03:00.0: 0x00000616 | line
[45189.267529] iwlagn 0000:03:00.0: 0x00018BCA | beacon time
[45189.267534] iwlagn 0000:03:00.0: 0x00000436 | tsf low
[45189.267538] iwlagn 0000:03:00.0: 0x00000000 | tsf hi
[45189.267543] iwlagn 0000:03:00.0: 0x00000000 | time gp1
[45189.267547] iwlagn 0000:03:00.0: 0x0000043A | time gp2
[45189.267551] iwlagn 0000:03:00.0: 0x00000000 | time gp3
[45189.267556] iwlagn 0000:03:00.0: 0x0001271F | uCode version
[45189.267561] iwlagn 0000:03:00.0: 0x0000006C | hw version
[45189.267565] iwlagn 0000:03:00.0: 0x00C80300 | board version
[45189.267570] iwlagn 0000:03:00.0: 0x00000000 | hcmd
[45189.267574] iwlagn 0000:03:00.0: CSR values:
[45189.267578] iwlagn 0000:03:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[45189.267589] iwlagn 0000:03:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[45189.267598] iwlagn 0000:03:00.0:          CSR_INT_COALESCING: 0X00000040
[45189.267607] iwlagn 0000:03:00.0:                     CSR_INT: 0X80000000
[45189.267616] iwlagn 0000:03:00.0:                CSR_INT_MASK: 0X00000000
[45189.267626] iwlagn 0000:03:00.0:           CSR_FH_INT_STATUS: 0X40010000
[45189.267635] iwlagn 0000:03:00.0:                 CSR_GPIO_IN: 0X00000000
[45189.267644] iwlagn 0000:03:00.0:                   CSR_RESET: 0X00000000
[45189.267653] iwlagn 0000:03:00.0:                CSR_GP_CNTRL: 0X080403c5
[45189.267662] iwlagn 0000:03:00.0:                  CSR_HW_REV: 0X0000006c
[45189.267671] iwlagn 0000:03:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[45189.267682] iwlagn 0000:03:00.0:               CSR_EEPROM_GP: 0X90000001
[45189.267694] iwlagn 0000:03:00.0:              CSR_OTP_GP_REG: 0X00210801
[45189.267706] iwlagn 0000:03:00.0:                 CSR_GIO_REG: 0X00080046
[45189.267717] iwlagn 0000:03:00.0:            CSR_GP_UCODE_REG: 0X00000000
[45189.267728] iwlagn 0000:03:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[45189.267739] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[45189.267749] iwlagn 0000:03:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[45189.267760] iwlagn 0000:03:00.0:                 CSR_LED_REG: 0X00000018
[45189.267771] iwlagn 0000:03:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[45189.267782] iwlagn 0000:03:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[45189.267800] iwlagn 0000:03:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[45189.267812] iwlagn 0000:03:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[45189.267823] iwlagn 0000:03:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[45189.267828] iwlagn 0000:03:00.0: FH register values:
[45189.267847] iwlagn 0000:03:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X19acf800
[45189.267867] iwlagn 0000:03:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01a84550
[45189.267887] iwlagn 0000:03:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[45189.267908] iwlagn 0000:03:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[45189.267927] iwlagn 0000:03:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[45189.267947] iwlagn 0000:03:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[45189.267968] iwlagn 0000:03:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[45189.267988] iwlagn 0000:03:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[45189.268008] iwlagn 0000:03:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[45189.268077] iwlagn 0000:03:00.0: Start IWL Event Log Dump: display last 5 entries
[45189.268103] iwlagn 0000:03:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[45189.268120] iwlagn 0000:03:00.0: EVT_LOGT:0000000021:0x00000000:1208
[45189.268137] iwlagn 0000:03:00.0: EVT_LOGT:0000001003:0x00000001:0071
[45189.268153] iwlagn 0000:03:00.0: EVT_LOGT:0000001079:0x00000002:0071
[45189.268169] iwlagn 0000:03:00.0: EVT_LOGT:0000001085:0x00000000:0125
[45189.268615] iwlagn 0000:03:00.0: Failed to run INIT ucode: -5
[45189.268722] iwlagn 0000:03:00.0: Unable to initialize device.

```

sudo lshw -C network

```
*-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:c4:60:50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-16-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:42 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: e8:9a:8f:07:76:3d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=sb ip=192.168.1.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 memory:f8400000-f840ffff

```

uname -mr gives:
```
3.0.0-16-generic x86_64
```

and sudo /etc/init.d/networking restart words, looks like.
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...   
```

---

### Post by amaz1ng on 2012-03-15
Naturally, my first inclination was to try and find the drivers for my card. But what I found was that, it appears that the driver for my card has been built into the Linux kernel. So I'm not sure what to do! Any advice would be appreciated.

---

### Post by chili555 on 2012-03-15
> iwlagn 0000:03:00.0: Microcode SW error detected.  Restarting 0x82000000.That surely is your problem. The driver iwlagn requires firmware. If it has an error or doesn't load correctly, the wireless interface wlan0 never starts and connects. It's a car without gas.

Googling turns up dozens of bug reports: [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2314](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2314)

[https://bbs.archlinux.org/viewtopic.php?id=125486](https://bbs.archlinux.org/viewtopic.php?id=125486)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779159)

What fixes there are seem to involve the firmware. Let's downgrade your firmware and see if it helps. Please go here: [http://intellinuxwireless.org/?n=downloads&f=ucodes_1000](http://intellinuxwireless.org/?n=downloads&f=ucodes_1000)

Download iwlwifi-1000-ucode-128.50.3.1.tgz to your desktop. Right-click it and select *Extract Here*. Open a terminal and back up the current firmware:```
sudo mv /lib/firmware/iwlwifi-1000-5.ucode /lib/firmware/iwlwifi-1000-5.bak
```Now we copy over the downloaded firmware:```
cd Desktop/iwlwifi-1000-ucode-128.50.3.1/
cp iwlwifi-3.ucode iwlwifi-1000-5.ucode
sudo cp iwlwifi-1000-5.ucode /lib/firmware
sudo modprobe -r iwlagn
sudo modprobe iwlagn 
```Now let's see what happened under the hood:```
dmesg | tail -n20
```

---

### Post by amaz1ng on 2012-03-15
Thanks Chili! Here's the output of dmesg | tail -n20:

```
[[80386.652922] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[80386.652925] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[80386.652927] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[80386.652929] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[80386.654907] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[80386.654910] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[80386.655014] iwlagn 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[80386.655046] iwlagn 0000:03:00.0: setting latency timer to 64
[80386.655120] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[80386.674895] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[80386.674898] iwlagn 0000:03:00.0: Device SKU: 0X9
[80386.674899] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[80386.674912] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[80386.675128] iwlagn 0000:03:00.0: irq 42 for MSI/MSI-X
[80386.677606] iwlagn 0000:03:00.0: Firmware has old API version. Expected v5, got v3. New firmware can be obtained from http://www.intellinuxwireless.org.
[80386.677612] iwlagn 0000:03:00.0: loaded firmware version 128.50.3.1 build 13488
[80386.677719] Registered led device: phy0-led
[80386.677743] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[80386.677961] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[80386.816720] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

(I think Chili made a typo in his (or her) post -- left out a bit of the filename for one of the .ucode files. Instead of > cp iwlwifi-3.ucode iwlwifi-1000-5.ucode the line should read > cp iwlwifi-1000-3.ucode iwlwifi-1000-5.ucode
 )

[/code]
)

---

### Post by amaz1ng on 2012-03-15
Interesting, I see the ```
[80386.816720] ADDRCONF(NETDEV_UP): wlan0: link is not ready
``` line, but I'm submitting this from my now-working wireless network. Thanks Chili!

EDIT: And it passes the restart test. Solved in my book.

---

### Post by chili555 on 2012-03-16
> I'm submitting this from my now-working wireless network. Thanks Chili!

EDIT: And it passes the restart test. Solved in my book.Awesome! Glad it's working. Perhaps you'd like to use Thread Tools at the top to Mark Solved.

---

