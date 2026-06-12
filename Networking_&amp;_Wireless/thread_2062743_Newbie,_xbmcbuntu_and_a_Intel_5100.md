---
title: "Newbie, xbmcbuntu and a Intel 5100"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by vanzan on 2012-09-25
Let me preface things by saying I am an extremely inexperienced Linux user. Here goes: I have a Acer Revo R3600 and I installed Xbmcbuntu 11.0 to it. Things were working fine until I realised the wireless card was only b/g. I purchased a Intel 5100 wireless N card on eBay. I installed it today but have been unable to get online since then. I fail to get a ip address in XBMC. I had wicd curses installed and working with the old card but it can't even "see" my network now so I have nothing to connect to there. I continually get an "error" in the terminal:fail to flush all tx fifo queues

I've spent two hours in the XBMC irc freenode channel without success. I posted at the XBMC forums without a single reply. I thought the Linux community was supposed to be a friendly and helpful one? Hoping my experience here will reinforce that to me. Please please help as I would be very grateful to have wireless again. Thank you! :)

Solved:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/876147/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/876147/comments/16)

---

### Post by Department Q on 2012-09-26
Good luck, I think the 5100 is doomed. there are a few of us on here looking for relief. 

Here is my story: 

I have a random computer called a Seneca Data Carbon 14.  Made by a small NY company.
I loaded 12.04 LTS on it and I can't get wireless. Ehternet works fine.

The adapter is the **Intel® WiFi Link 5100.**

 I have a feeling the Wireless Radio is off but the FN+F2 Radio switch does nothing and the button that looks like a radio switch next to volume also does nothing. Wireless LED is off.

I tried installing WICD and uninstalling network-manager. no luck.  Now I have both installed. 

I tried downloading the iwlagn driver and installing per Chili555's instruction but I'm not sure it worked because as you can see below, iwlwifi seems prevalent. Also, I got no indication that the iwlwifi was removed.  I am running out of ideas and about to just go back to windows because a "non wifi" Laptop is not that great.

I also created a file: /etc/modprobe.d/intel_11n_disable.conf containing the line "options iwlagn 11n_disable=1". no luck but then again I don't think I have iwlagn either.

Thanks for your help and any advice.

Here are a few results:
```


    carbon@carbon-pro:~$ rfkill list all
    0: cmpc_rfkill: Wireless LAN
        Soft blocked: no
        Hard blocked: no
    1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
   

    carbon@carbon-pro:~$ sudo modprobe iwlagn
    [sudo] password for carbon: 
    carbon@carbon-pro:~$ dmesg | grep iwl
    [   23.137796] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
    [   23.137806] iwlwifi 0000:01:00.0: setting latency timer to 64
    [   23.137830] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
    [   23.137833] iwlwifi 0000:01:00.0: pci_resource_base = ffffc9000035c000
    [   23.137836] iwlwifi 0000:01:00.0: HW Revision ID = 0x0
    [   23.138016] iwlwifi 0000:01:00.0: irq 48 for MSI/MSI-X
    [   23.138066] iwlwifi 0000:01:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
    [   23.138232] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [   23.160065] iwlwifi 0000:01:00.0: device EEPROM VER=0x11f, CALIB=0x4
    [   23.160070] iwlwifi 0000:01:00.0: Device SKU: 0Xf0
    [   23.160097] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
    [   23.395299] iwlwifi 0000:01:00.0: loaded firmware version 8.83.5.1 build 33692
    [   23.400039] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
    [   23.898631] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [   23.901656] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
    [   23.937458] iwlwifi 0000:01:00.0: Hardware error detected.  Restarting.
    [   23.937464] iwlwifi 0000:01:00.0: Loaded firmware version: 8.83.5.1 build 33692
    [   23.937536] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
    [   23.937538] iwlwifi 0000:01:00.0: Status: 0x00040220, count: -1222849788
    [   23.937542] iwlwifi 0000:01:00.0: 0x9D93948F | ADVANCED_SYSASSERT          
    [   23.937545] iwlwifi 0000:01:00.0: 0x74BC6C25 | uPc
    [   23.937547] iwlwifi 0000:01:00.0: 0xD4D8EAF7 | branchlink1
    [   23.937550] iwlwifi 0000:01:00.0: 0x79F929A3 | branchlink2
    [   23.937552] iwlwifi 0000:01:00.0: 0x25185FAF | interruptlink1
    [   23.937555] iwlwifi 0000:01:00.0: 0x7367EF6F | interruptlink2
    [   23.937557] iwlwifi 0000:01:00.0: 0x7686C34C | data1
    [   23.937559] iwlwifi 0000:01:00.0: 0x6F06C975 | data2
    [   23.937562] iwlwifi 0000:01:00.0: 0xFBAF3ACB | line
    [   23.937564] iwlwifi 0000:01:00.0: 0xF7C9DD06 | beacon time
    [   23.937566] iwlwifi 0000:01:00.0: 0x7D93D56F | tsf low
    [   23.937569] iwlwifi 0000:01:00.0: 0x4C3ED509 | tsf hi
    [   23.937571] iwlwifi 0000:01:00.0: 0xFD0DAAFE | time gp1
    [   23.937573] iwlwifi 0000:01:00.0: 0x6EEFE341 | time gp2
    [   23.937576] iwlwifi 0000:01:00.0: 0x66FF4FF5 | time gp3
    [   23.937578] iwlwifi 0000:01:00.0: 0x28E5C81E | uCode version
    [   23.937580] iwlwifi 0000:01:00.0: 0x97F79493 | hw version
    [   23.937583] iwlwifi 0000:01:00.0: 0x4FFFDB4F | board version
    [   23.937585] iwlwifi 0000:01:00.0: 0x6530D9E0 | hcmd
    [   23.937588] iwlwifi 0000:01:00.0: CSR values:
    [   23.937590] iwlwifi 0000:01:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
    [   23.937596] iwlwifi 0000:01:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
    [   23.937601] iwlwifi 0000:01:00.0:          CSR_INT_COALESCING: 0X00000040
    [   23.937606] iwlwifi 0000:01:00.0:                     CSR_INT: 0X20000000
    [   23.937611] iwlwifi 0000:01:00.0:                CSR_INT_MASK: 0X00000000
    [   23.937617] iwlwifi 0000:01:00.0:           CSR_FH_INT_STATUS: 0X00000000
    [   23.937622] iwlwifi 0000:01:00.0:                 CSR_GPIO_IN: 0X00000000
    [   23.937627] iwlwifi 0000:01:00.0:                   CSR_RESET: 0X00000009
    [   23.937632] iwlwifi 0000:01:00.0:                CSR_GP_CNTRL: 0X080003c5
    [   23.937637] iwlwifi 0000:01:00.0:                  CSR_HW_REV: 0X00000054
    [   23.937642] iwlwifi 0000:01:00.0:              CSR_EEPROM_REG: 0X00000000
    [   23.937647] iwlwifi 0000:01:00.0:               CSR_EEPROM_GP: 0X90000004
    [   23.937652] iwlwifi 0000:01:00.0:              CSR_OTP_GP_REG: 0X00060000
    [   23.937658] iwlwifi 0000:01:00.0:                 CSR_GIO_REG: 0X00080044
    [   23.937663] iwlwifi 0000:01:00.0:            CSR_GP_UCODE_REG: 0X00000000
    [   23.937668] iwlwifi 0000:01:00.0:           CSR_GP_DRIVER_REG: 0X00000000
    [   23.937673] iwlwifi 0000:01:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
    [   23.937678] iwlwifi 0000:01:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
    [   23.937683] iwlwifi 0000:01:00.0:                 CSR_LED_REG: 0X00000018
    [   23.937688] iwlwifi 0000:01:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
    [   23.937694] iwlwifi 0000:01:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
    [   23.937699] iwlwifi 0000:01:00.0:             CSR_ANA_PLL_CFG: 0X00880300
    [   23.937704] iwlwifi 0000:01:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
    [   23.937709] iwlwifi 0000:01:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
    [   23.937712] iwlwifi 0000:01:00.0: FH register values:
    [   23.937726] iwlwifi 0000:01:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X06607400
    [   23.937739] iwlwifi 0000:01:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X006626b0
    [   23.937752] iwlwifi 0000:01:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
    [   23.937765] iwlwifi 0000:01:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
    [   23.937778] iwlwifi 0000:01:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X0000003c
    [   23.937791] iwlwifi 0000:01:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
    [   23.937805] iwlwifi 0000:01:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
    [   23.937819] iwlwifi 0000:01:00.0:                FH_TSSR_TX_STATUS_REG: 0X05ff0000
    [   23.937833] iwlwifi 0000:01:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
    [   23.937882] iwlwifi 0000:01:00.0: Log capacity 118980931 is bogus, limit to 256 entries
    [   23.937885] iwlwifi 0000:01:00.0: Log write index -479274738 is bogus, limit to 256
    [   23.937888] iwlwifi 0000:01:00.0: Start IWL Event Log Dump: display last 20 entries
    [   23.937906] iwlwifi 0000:01:00.0: EVT_LOGT:0570291876:0xcf42790d:3081624423
    [   23.937917] iwlwifi 0000:01:00.0: EVT_LOGT:2080102228:0x510cdfeb:3867114880
    [   23.937928] iwlwifi 0000:01:00.0: EVT_LOGT:1204167583:0xd3a9b49f:3757509231
    [   23.937939] iwlwifi 0000:01:00.0: EVT_LOGT:3598207773:0xad5cf0ae:601834879
    [   23.937951] iwlwifi 0000:01:00.0: EVT_LOGT:3616630249:0xe7e9be8d:1596430253
    [   23.937962] iwlwifi 0000:01:00.0: EVT_LOGT:4175233537:0xd5da39b3:970899957
    [   23.937974] iwlwifi 0000:01:00.0: EVT_LOGT:2712366750:0x153f51e7:2721607275
    [   23.937985] iwlwifi 0000:01:00.0: EVT_LOGT:0718138711:0x3cdffdbf:1641189246
    [   23.937995] iwlwifi 0000:01:00.0: EVT_LOGT:3712401141:0xbf759b0c:602864538
    [   23.938007] iwlwifi 0000:01:00.0: EVT_LOGT:3884957690:0x1fdcff2f:3120168423
    [   23.938018] iwlwifi 0000:01:00.0: EVT_LOGT:3667864789:0x9c29b57d:2389098332
    [   23.938029] iwlwifi 0000:01:00.0: EVT_LOGT:3692789065:0xb7fb175f:2138878854
    [   23.938040] iwlwifi 0000:01:00.0: EVT_LOGT:4233080783:0xdba22fae:3672233812
    [   23.938051] iwlwifi 0000:01:00.0: EVT_LOGT:0431416889:0x8bf6f7f5:1811855613
    [   23.938062] iwlwifi 0000:01:00.0: EVT_LOGT:1801449446:0x2a7798ad:4025966542
    [   23.938074] iwlwifi 0000:01:00.0: EVT_LOGT:1850948857:0x7b21c75f:2990459829
    [   23.938084] iwlwifi 0000:01:00.0: EVT_LOGT:3841960874:0xf4dcb9bc:182299815
    [   23.938095] iwlwifi 0000:01:00.0: EVT_LOGT:4290679089:0xef2d9b57:3602627871
    [   23.938105] iwlwifi 0000:01:00.0: EVT_LOGT:3388896124:0x267f4374:3117114591
    [   23.938116] iwlwifi 0000:01:00.0: EVT_LOGT:1093868139:0x2ed05ba1:4279663190
    [   28.900054] iwlwifi 0000:01:00.0: Could not load the INST uCode section
    [   28.900299] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
    [   28.900341] iwlwifi 0000:01:00.0: Unable to initialize device.
    [   28.901740] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [   28.904736] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
    [   28.941191] iwlwifi 0000:01:00.0: Hardware error detected.  Restarting.
    [   28.941197] iwlwifi 0000:01:00.0: Loaded firmware version: 8.83.5.1 build 33692
    [   28.941268] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
    [   28.941270] iwlwifi 0000:01:00.0: Status: 0x00040220, count: -1222849788
    [   28.941274] iwlwifi 0000:01:00.0: 0x9D93948F | ADVANCED_SYSASSERT          
    [   28.941277] iwlwifi 0000:01:00.0: 0x74BC6C25 | uPc
    [   28.941279] iwlwifi 0000:01:00.0: 0xD4D8EAF7 | branchlink1
    [   28.941282] iwlwifi 0000:01:00.0: 0x79F929A3 | branchlink2
    [   28.941284] iwlwifi 0000:01:00.0: 0x25185FAF | interruptlink1
    [   28.941286] iwlwifi 0000:01:00.0: 0x7367EF6F | interruptlink2
    [   28.941289] iwlwifi 0000:01:00.0: 0x7686C34C | data1
    [   28.941291] iwlwifi 0000:01:00.0: 0x6F06C975 | data2
    [   28.941293] iwlwifi 0000:01:00.0: 0xFBAF3ACB | line
    [   28.941296] iwlwifi 0000:01:00.0: 0xF7C9DD06 | beacon time
    [   28.941298] iwlwifi 0000:01:00.0: 0x7D93D56F | tsf low
    [   28.941301] iwlwifi 0000:01:00.0: 0x4C3ED509 | tsf hi
    [   28.941303] iwlwifi 0000:01:00.0: 0xFD0DAAFE | time gp1
    [   28.941305] iwlwifi 0000:01:00.0: 0x6EEFE341 | time gp2
    [   28.941308] iwlwifi 0000:01:00.0: 0x66FF4FF5 | time gp3
    [   28.941310] iwlwifi 0000:01:00.0: 0x28E5C81E | uCode version
    [   28.941312] iwlwifi 0000:01:00.0: 0x97F79493 | hw version
    [   28.941315] iwlwifi 0000:01:00.0: 0x4FFFDB4F | board version
    [   28.941317] iwlwifi 0000:01:00.0: 0x6530D9E0 | hcmd
    [   28.941320] iwlwifi 0000:01:00.0: CSR values:
    [   28.941322] iwlwifi 0000:01:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
    [   28.941327] iwlwifi 0000:01:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
    [   28.941333] iwlwifi 0000:01:00.0:          CSR_INT_COALESCING: 0X00000040
    [   28.941338] iwlwifi 0000:01:00.0:                     CSR_INT: 0X20000000
    [   28.941343] iwlwifi 0000:01:00.0:                CSR_INT_MASK: 0X00000000
    [   28.941348] iwlwifi 0000:01:00.0:           CSR_FH_INT_STATUS: 0X00000000
    [   28.941353] iwlwifi 0000:01:00.0:                 CSR_GPIO_IN: 0X00000000
    [   28.941358] iwlwifi 0000:01:00.0:                   CSR_RESET: 0X00000009
    [   28.941363] iwlwifi 0000:01:00.0:                CSR_GP_CNTRL: 0X080003c5
    [   28.941368] iwlwifi 0000:01:00.0:                  CSR_HW_REV: 0X00000054
    [   28.941373] iwlwifi 0000:01:00.0:              CSR_EEPROM_REG: 0X00000000
    [   28.941378] iwlwifi 0000:01:00.0:               CSR_EEPROM_GP: 0X90000004
    [   28.941384] iwlwifi 0000:01:00.0:              CSR_OTP_GP_REG: 0X00060000
    [   28.941389] iwlwifi 0000:01:00.0:                 CSR_GIO_REG: 0X00080044
    [   28.941394] iwlwifi 0000:01:00.0:            CSR_GP_UCODE_REG: 0X00000000
    [   28.941399] iwlwifi 0000:01:00.0:           CSR_GP_DRIVER_REG: 0X00000000
    [   28.941404] iwlwifi 0000:01:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
    [   28.941409] iwlwifi 0000:01:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
    [   28.941415] iwlwifi 0000:01:00.0:                 CSR_LED_REG: 0X00000018
    [   28.941420] iwlwifi 0000:01:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
    [   28.941425] iwlwifi 0000:01:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
    [   28.941430] iwlwifi 0000:01:00.0:             CSR_ANA_PLL_CFG: 0X00000000
    [   28.941435] iwlwifi 0000:01:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
    [   28.941440] iwlwifi 0000:01:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
    [   28.941443] iwlwifi 0000:01:00.0: FH register values:
    [   28.941456] iwlwifi 0000:01:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X06607400
    [   28.941469] iwlwifi 0000:01:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X006626b0
    [   28.941482] iwlwifi 0000:01:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
    [   28.941495] iwlwifi 0000:01:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
    [   28.941508] iwlwifi 0000:01:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X0000003c
    [   28.941521] iwlwifi 0000:01:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
    [   28.941534] iwlwifi 0000:01:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
    [   28.941546] iwlwifi 0000:01:00.0:                FH_TSSR_TX_STATUS_REG: 0X05ff0000
    [   28.941559] iwlwifi 0000:01:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
    [   28.941609] iwlwifi 0000:01:00.0: Log capacity 118980931 is bogus, limit to 256 entries
    [   28.941612] iwlwifi 0000:01:00.0: Log write index -479274738 is bogus, limit to 256
    [   28.941614] iwlwifi 0000:01:00.0: Start IWL Event Log Dump: display last 20 entries
    [   28.941632] iwlwifi 0000:01:00.0: EVT_LOGT:0570291876:0xcf42790d:3081624423
    [   28.941643] iwlwifi 0000:01:00.0: EVT_LOGT:2080102228:0x510cdfeb:3867114880
    [   28.941653] iwlwifi 0000:01:00.0: EVT_LOGT:1204167583:0xd3a9b49f:3757509231
    [   28.941664] iwlwifi 0000:01:00.0: EVT_LOGT:3598207773:0xad5cf0ae:601834879
    [   28.941674] iwlwifi 0000:01:00.0: EVT_LOGT:3616630249:0xe7e9be8d:1596430253
    [   28.941685] iwlwifi 0000:01:00.0: EVT_LOGT:4175233537:0xd5da39b3:970899957
    [   28.941695] iwlwifi 0000:01:00.0: EVT_LOGT:2712366750:0x153f51e7:2721607275
    [   28.941705] iwlwifi 0000:01:00.0: EVT_LOGT:0718138711:0x3cdffdbf:1641189246
    [   28.941716] iwlwifi 0000:01:00.0: EVT_LOGT:3712401141:0xbf759b0c:602864538
    [   28.941726] iwlwifi 0000:01:00.0: EVT_LOGT:3884957690:0x1fdcff2f:3120168423
    [   28.941736] iwlwifi 0000:01:00.0: EVT_LOGT:3667864789:0x9c29b57d:2389098332
    [   28.941747] iwlwifi 0000:01:00.0: EVT_LOGT:3692789065:0xb7fb175f:2138878854
    [   28.941757] iwlwifi 0000:01:00.0: EVT_LOGT:4233080783:0xdba22fae:3672233812
    [   28.941768] iwlwifi 0000:01:00.0: EVT_LOGT:0431416889:0x8bf6f7f5:1811855613
    [   28.941778] iwlwifi 0000:01:00.0: EVT_LOGT:1801449446:0x2a7798ad:4025966542
    [   28.941788] iwlwifi 0000:01:00.0: EVT_LOGT:1850948857:0x7b21c75f:2990459829
    [   28.941799] iwlwifi 0000:01:00.0: EVT_LOGT:3841960874:0xf4dcb9bc:182299815
    [   28.941809] iwlwifi 0000:01:00.0: EVT_LOGT:4290679089:0xef2d9b57:3602627871
    [   28.941820] iwlwifi 0000:01:00.0: EVT_LOGT:3388896124:0x267f4374:3117114591
    [   28.941830] iwlwifi 0000:01:00.0: EVT_LOGT:1093868139:0x2ed05ba1:4279663190
    [   33.904118] iwlwifi 0000:01:00.0: Could not load the INST uCode section
    [   33.904470] iwlwifi 0000:01:00.0: Master Disable Timed Out, 100 usec
    [   33.904489] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
    [   33.904528] iwlwifi 0000:01:00.0: Unable to initialize device.
    [   33.911541] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [   33.914547] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
    [   38.916152] iwlwifi 0000:01:00.0: Could not load the INST uCode section
    [   38.916505] iwlwifi 0000:01:00.0: Master Disable Timed Out, 100 usec
    [   38.916529] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
    [   38.916570] iwlwifi 0000:01:00.0: Unable to initialize device.
    [   38.916874] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [   38.919824] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
    [   43.920062] iwlwifi 0000:01:00.0: Could not load the INST uCode section
    [   43.920417] iwlwifi 0000:01:00.0: Master Disable Timed Out, 100 usec
    [   43.920437] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
    [   43.920476] iwlwifi 0000:01:00.0: Unable to initialize device.
    [   44.092216] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [   44.095158] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
    [   49.092115] iwlwifi 0000:01:00.0: Could not load the INST uCode section
    [   49.092468] iwlwifi 0000:01:00.0: Master Disable Timed Out, 100 usec
    [   49.092487] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
    [   49.092529] iwlwifi 0000:01:00.0: Unable to initialize device.
    [   49.107129] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [   49.110113] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
    [   54.108112] iwlwifi 0000:01:00.0: Could not load the INST uCode section
    [   54.108465] iwlwifi 0000:01:00.0: Master Disable Timed Out, 100 usec
    [   54.108485] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
    [   54.108524] iwlwifi 0000:01:00.0: Unable to initialize device.
    [   96.874102] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [   96.877101] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
    [  101.876061] iwlwifi 0000:01:00.0: Could not load the INST uCode section
    [  101.876411] iwlwifi 0000:01:00.0: Master Disable Timed Out, 100 usec
    [  101.876431] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
    [  101.876468] iwlwifi 0000:01:00.0: Unable to initialize device.
    [  102.986344] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
    [  102.989317] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
    [  107.988209] iwlwifi 0000:01:00.0: Could not load the INST uCode section
    [  107.988591] iwlwifi 0000:01:00.0: Master Disable Timed Out, 100 usec
    [  107.988618] iwlwifi 0000:01:00.0: Failed to run INIT ucode: -110
    [  107.988672] iwlwifi 0000:01:00.0: Unable to initialize device.
    carbon@carbon-pro:~$
```

---

### Post by chili555 on 2012-09-26
> I tried downloading the iwlagn driver and installing per Chili555's instruction I am sure those instructions are as old as my grandpa. For 12.04, they are no longer valid.

The key to your problem is here:> iwlwifi 0000:01:00.0: [COLOR="Red"]Hardware error detected.  Restarting.[/COLOR]
    [   23.937464] iwlwifi 0000:01:00.0: Loaded firmware version: 8.83.5.1 build 33692
    [   23.937536] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
    [   23.937538] iwlwifi 0000:01:00.0: Status: 0x00040220, count: -1222849788Before we blame the hardware and suggest radical surgery, there are a few things we can look at. First, is your firmware file intact and not corrupt? Please run and post:```
md5sum /lib/firmware/iwlwifi-5*
```On my perfectly operating iwlwifi laptop, the result is:> d1f08911dfdbad1603b31d6f5113d852  /lib/firmware/iwlwifi-5000-5.ucode
fd5e408b84517c8c77e761d23d8ffa98  /lib/firmware/iwlwifi-5150-2.ucode
If yours are not the same, we can replace yours.

Second, there is an updated iwlwifi available. Please do:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic
```Reboot and run and post:```
dmesg | grep iwl
```Are the error messages gone?> I have a feeling the Wireless Radio is off but the FN+F2 Radio switch does nothing and the button that looks like a radio switch next to volume also does nothing. Wireless LED is off.According to your rfkill results, you have no problem. The light and switch show no activity because the hardware won't start.

---

