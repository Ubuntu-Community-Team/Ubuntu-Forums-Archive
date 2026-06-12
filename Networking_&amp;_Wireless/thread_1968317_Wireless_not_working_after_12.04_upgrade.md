---
title: "Wireless not working after 12.04 upgrade"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by pnkalaa on 2012-04-28
Hi ,

i am using DELL XPS laptop and recently upgraded from 11.10 to 12.04 , but then onwards the wireless is not working.
please help me .
it is using Network controller: Intel Corporation Centrino Wireless-N 1030

---

### Post by chili555 on 2012-04-29
Please open a termianl and run and post:```
rfkill list all
sudo modprobe iwlwifi
dmesg | grep iwl
```Thanks.

---

### Post by agatau on 2012-04-30
same problem here. dell studio xps 16, 64bit kubuntu

```
rfkill list all
```
returns
```
0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
```

modprobe loads the module

strangely enough, no instances of iwl have been found by dmesg meaning that the interface is not detected after all. lastly, switching the network button on and off doesn't make any difference

I have also tried the fn+f2 key combination to wake up wlan interface but that didn't work

---

### Post by chili555 on 2012-04-30
> **agatau said:**
> same problem here. dell studio xps 16, 64bit kubuntu

modprobe loads the module

strangely enough, no instances of iwl have been found by dmesg meaning that the interface is not detected after all. lastly, switching the network button on and off doesn't make any difference

I have also tried the fn+f2 key combination to wake up wlan interface but that didn't workI'd like to see it for myself. Please post:```
lspci -nn | grep 0280
```If it's not an Intel card, please start your own new thread. Thanks.

---

### Post by AdrianP on 2012-05-03
*[I]You might want to try post #2 of this thread* [/I][http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096)*  which has just worked  for me (see post #6 there for a description of the problem I had)             *

---

### Post by chili555 on 2012-05-03
> **AdrianP said:**
> *[I]You might want to try post #2 of this thread* [/I][http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096)*  which has just worked  for me (see post #6 there for a description of the problem I had)             *Your card is a Broadcom. pnkalaa's card is:> Intel Corporation Centrino Wireless-N 1030 Your fix won't work.

---

### Post by cjmanders on 2012-05-10
My own issue is the same:  No wifi. Fn+F2 does NOT turn on the wifi and no dmesg output is recorded when I do. It did in 11.10.  More data:  $ rfkill list all 0: hci0: Bluetooth 	Soft blocked: no 	Hard blocked: no 1: dell-wifi: Wireless LAN 	Soft blocked: no 	Hard blocked: no 2: dell-bluetooth: Bluetooth 	Soft blocked: no 	Hard blocked: no 3: dell-wwan: Wireless WAN 	Soft blocked: no 	Hard blocked: no  $ sudo modprobe iwlwifi FATAL: Module iwlwifi not found.  ~$ dmesg|grep iwl [   21.630046] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree: [   21.630048] iwlagn: Copyright(c) 2003-2011 Intel Corporation [   21.630142] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 [   21.630173] iwlagn 0000:03:00.0: setting latency timer to 64 [   21.630248] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0 [   21.645792] iwlagn 0000:03:00.0: device EEPROM VER=0x716, CALIB=0x6 [   21.645795] iwlagn 0000:03:00.0: Device SKU: 0Xb [   21.645796] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3 [   21.645822] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels [   21.645959] iwlagn 0000:03:00.0: irq 55 for MSI/MSI-X [   21.681755] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2b-5.ucode' failed. [   21.682706] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2b-4.ucode' failed. [   21.682709] iwlagn 0000:03:00.0: no suitable firmware found! [   21.682880] iwlagn 0000:03:00.0: PCI INT A disabled  $ sudo lspci -nn | grep 0280 03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)  It looks like 12.04 was actually a DOWNgrade, since many of my preferences were zeroed out.  So, when will it be fixed? Or, is there a fix?  Tx!

---

### Post by chili555 on 2012-05-10
> It looks like 12.04 was actually a DOWNgrade, since many of my preferences were zeroed out. So, when will it be fixed? Or, is there a fix? Tx!There is almost always a fix. May I see:```
uname -r
```Thanks.

---

### Post by Jeffbuntu on 2012-05-11
Thank goodness - I thought it was just me :) I'm having similar issues with wireless not working in 12.04 but this is with a new install on an Acer 281G Nettop using a realtek wireless card.
 
I'm also in the nothing (iwl) showing up in dmesg camp. 
 
The really odd thing is that the linpus lite that came with the acer runs the wireless flawlessly.
 
 
Duh! - Of course I won't see iwlwifi show up :D 
 
rwlwifi does show up in dmesg though.  I have seen one thing in the message that seems pretty confusing.  Does anyone know what unknown CUT! means?
 
Thanks
 
Jeff

---

### Post by gabrielshier on 2012-05-11
Bump.
Same issue here and could not find a fix. 
New laptop, with ubuntu 12.04 clean installation. Connects to the wireless network (encryption is configured!) and there is internet connectivity for the first few seconds, and then it dies. Can't resolve DNS or get any connectivity even inside the network. 

```
rfkill list all
sudo modprobe iwlwifi
dmesg | grep iwl
```
gave this back:
```
[  146.940604] iwlwifi 0000:0d:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  146.940633] iwlwifi 0000:0d:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  146.940659] iwlwifi 0000:0d:00.0:          CSR_INT_COALESCING: 0X00000040
[  146.940685] iwlwifi 0000:0d:00.0:                     CSR_INT: 0X00000000
[  146.940711] iwlwifi 0000:0d:00.0:                CSR_INT_MASK: 0X00000000
[  146.940737] iwlwifi 0000:0d:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  146.940764] iwlwifi 0000:0d:00.0:                 CSR_GPIO_IN: 0X00000030
[  146.940790] iwlwifi 0000:0d:00.0:                   CSR_RESET: 0X00000000
[  146.940816] iwlwifi 0000:0d:00.0:                CSR_GP_CNTRL: 0X080403c5
[  146.940842] iwlwifi 0000:0d:00.0:                  CSR_HW_REV: 0X000000b0
[  146.940868] iwlwifi 0000:0d:00.0:              CSR_EEPROM_REG: 0X50010ffd
[  146.940894] iwlwifi 0000:0d:00.0:               CSR_EEPROM_GP: 0X90000001
[  146.940920] iwlwifi 0000:0d:00.0:              CSR_OTP_GP_REG: 0X00030001
[  146.940946] iwlwifi 0000:0d:00.0:                 CSR_GIO_REG: 0X00080042
[  146.940972] iwlwifi 0000:0d:00.0:            CSR_GP_UCODE_REG: 0X0000449d
[  146.940998] iwlwifi 0000:0d:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  146.941024] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  146.941049] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  146.941075] iwlwifi 0000:0d:00.0:                 CSR_LED_REG: 0X00000078
[  146.941102] iwlwifi 0000:0d:00.0:        CSR_DRAM_INT_TBL_REG: 0X8824fd12
[  146.941128] iwlwifi 0000:0d:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  146.941154] iwlwifi 0000:0d:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  146.941180] iwlwifi 0000:0d:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  146.941206] iwlwifi 0000:0d:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  146.941208] iwlwifi 0000:0d:00.0: FH register values:
[  146.941245] iwlwifi 0000:0d:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X24f5e100
[  146.941281] iwlwifi 0000:0d:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02418030
[  146.941321] iwlwifi 0000:0d:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000d8
[  146.941366] iwlwifi 0000:0d:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00819104
[  146.941393] iwlwifi 0000:0d:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  146.941416] iwlwifi 0000:0d:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  146.941444] iwlwifi 0000:0d:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  146.941479] iwlwifi 0000:0d:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  146.941520] iwlwifi 0000:0d:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  146.941630] iwlwifi 0000:0d:00.0: Start IWL Event Log Dump: display last 20 entries
[  146.941683] iwlwifi 0000:0d:00.0: EVT_LOGT:0060292829:0xa3289fec:0636
[  146.941729] iwlwifi 0000:0d:00.0: EVT_LOGT:0060292869:0x000000fa:0106
[  146.941768] iwlwifi 0000:0d:00.0: EVT_LOGT:0060292871:0x00000000:0301
[  146.941808] iwlwifi 0000:0d:00.0: EVT_LOGT:0060293246:0x00000080:0313
[  146.941847] iwlwifi 0000:0d:00.0: EVT_LOGT:0060293248:0x00000576:0501
[  146.941892] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294844:0x000002c0:0501
[  146.941926] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294850:0x00000000:0504
[  146.941971] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294852:0x00000000:0504
[  146.942017] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294852:0x0000006e:0601
[  146.942063] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294852:0x9301882b:0600
[  146.942109] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294853:0x0000008e:0601
[  146.942155] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294854:0x9301882b:0600
[  146.942188] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294854:0x01000000:0600
[  146.942221] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294865:0x00c01007:0310
[  146.942266] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294879:0x000000e5:0601
[  146.942300] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294887:0x0000024d:0635
[  146.942332] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294922:0x000000fa:0106
[  146.942365] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294923:0x00000000:0301
[  146.942398] iwlwifi 0000:0d:00.0: EVT_LOGT:0060494916:0x000000f6:0123
[  146.942431] iwlwifi 0000:0d:00.0: EVT_LOGT:0060494940:0x00000000:0125
[  146.943162] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[  146.950202] iwlwifi 0000:0d:00.0: Radio type=0x1-0x2-0x0
[  155.886057] iwlwifi 0000:0d:00.0: Tx aggregation enabled on ra = 5c:d9:98:c0:d5:14 tid = 0
[  155.934996] iwlwifi 0000:0d:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  155.935007] iwlwifi 0000:0d:00.0: Loaded firmware version: 17.168.5.3 build 42301
[  155.935283] iwlwifi 0000:0d:00.0: Start IWL Error Log Dump:
[  155.935289] iwlwifi 0000:0d:00.0: Status: 0x000412E4, count: 6
[  155.935296] iwlwifi 0000:0d:00.0: 0x00000EDC | ADVANCED_SYSASSERT          
[  155.935301] iwlwifi 0000:0d:00.0: 0x00020DE0 | uPc
[  155.935306] iwlwifi 0000:0d:00.0: 0x00020DA8 | branchlink1
[  155.935340] iwlwifi 0000:0d:00.0: 0x00020DA8 | branchlink2
[  155.935345] iwlwifi 0000:0d:00.0: 0x0000D1F2 | interruptlink1
[  155.935350] iwlwifi 0000:0d:00.0: 0x00000000 | interruptlink2
[  155.935355] iwlwifi 0000:0d:00.0: 0x00000001 | data1
[  155.935359] iwlwifi 0000:0d:00.0: 0x7473FFFF | data2
[  155.935364] iwlwifi 0000:0d:00.0: 0x00000ACA | line
[  155.935368] iwlwifi 0000:0d:00.0: 0x15800303 | beacon time
[  155.935373] iwlwifi 0000:0d:00.0: 0xA3B53CFD | tsf low
[  155.935377] iwlwifi 0000:0d:00.0: 0x0000001B | tsf hi
[  155.935382] iwlwifi 0000:0d:00.0: 0x00000000 | time gp1
[  155.935386] iwlwifi 0000:0d:00.0: 0x0089443F | time gp2
[  155.935391] iwlwifi 0000:0d:00.0: 0x00000000 | time gp3
[  155.935395] iwlwifi 0000:0d:00.0: 0x000111A8 | uCode version
[  155.935400] iwlwifi 0000:0d:00.0: 0x000000B0 | hw version
[  155.935405] iwlwifi 0000:0d:00.0: 0x00480303 | board version
[  155.935409] iwlwifi 0000:0d:00.0: 0x7473FFFF | hcmd
[  155.935414] iwlwifi 0000:0d:00.0: CSR values:
[  155.935419] iwlwifi 0000:0d:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  155.935452] iwlwifi 0000:0d:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  155.935484] iwlwifi 0000:0d:00.0:          CSR_INT_COALESCING: 0X0000ff40
[  155.935517] iwlwifi 0000:0d:00.0:                     CSR_INT: 0X00000000
[  155.935549] iwlwifi 0000:0d:00.0:                CSR_INT_MASK: 0X00000000
[  155.935582] iwlwifi 0000:0d:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  155.935615] iwlwifi 0000:0d:00.0:                 CSR_GPIO_IN: 0X00000030
[  155.935647] iwlwifi 0000:0d:00.0:                   CSR_RESET: 0X00000000
[  155.935677] iwlwifi 0000:0d:00.0:                CSR_GP_CNTRL: 0X080403c5
[  155.935708] iwlwifi 0000:0d:00.0:                  CSR_HW_REV: 0X000000b0
[  155.935738] iwlwifi 0000:0d:00.0:              CSR_EEPROM_REG: 0X50010ffd
[  155.935770] iwlwifi 0000:0d:00.0:               CSR_EEPROM_GP: 0X90000001
[  155.935802] iwlwifi 0000:0d:00.0:              CSR_OTP_GP_REG: 0X00030001
[  155.935835] iwlwifi 0000:0d:00.0:                 CSR_GIO_REG: 0X00080042
[  155.935868] iwlwifi 0000:0d:00.0:            CSR_GP_UCODE_REG: 0X00000846
[  155.935901] iwlwifi 0000:0d:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  155.935934] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  155.935963] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  155.935995] iwlwifi 0000:0d:00.0:                 CSR_LED_REG: 0X00000078
[  155.936027] iwlwifi 0000:0d:00.0:        CSR_DRAM_INT_TBL_REG: 0X8824fd12
[  155.936060] iwlwifi 0000:0d:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  155.936093] iwlwifi 0000:0d:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  155.936125] iwlwifi 0000:0d:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  155.936158] iwlwifi 0000:0d:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  155.936163] iwlwifi 0000:0d:00.0: FH register values:
[  155.936225] iwlwifi 0000:0d:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X24f5e100
[  155.936285] iwlwifi 0000:0d:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02418030
[  155.936347] iwlwifi 0000:0d:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000080
[  155.936408] iwlwifi 0000:0d:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[  155.936470] iwlwifi 0000:0d:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  155.936530] iwlwifi 0000:0d:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  155.936600] iwlwifi 0000:0d:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  155.936661] iwlwifi 0000:0d:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  155.936721] iwlwifi 0000:0d:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  155.936902] iwlwifi 0000:0d:00.0: Start IWL Event Log Dump: display last 20 entries
[  155.936975] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995385:0x00000000:0302
[  155.937027] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995418:0x00000001:0203
[  155.937079] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995423:0x0b19001c:0206
[  155.937132] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995424:0x00000040:0204
[  155.937178] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995427:0x2b1048df:0222
[  155.937231] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995427:0xc0100084:0223
[  155.937277] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995429:0x00000040:0219
[  155.937329] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995430:0x03000090:0211
[  155.937382] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995434:0x00000000:0212
[  155.937428] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995461:0x00000000:0215
[  155.937481] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995464:0x00000008:0220
[  155.937534] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995483:0x00000000:0302
[  155.937586] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995513:0x000000d4:0303
[  155.937639] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995517:0x0000141a:0217
[  155.937691] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995518:0x0b19001c:0217
[  155.937744] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995637:0x000000fa:0106
[  155.937796] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995639:0x00000000:0302
[  155.937849] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995785:0x000000d4:0322
[  155.937901] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995815:0x0066171f:0310
[  155.937954] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995923:0x00000000:0125
[  155.939058] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[  155.946120] iwlwifi 0000:0d:00.0: Radio type=0x1-0x2-0x0
gabriels@Johns-Asus:~$ dmesg | grep iwl
[   15.140673] iwlwifi 0000:0d:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.140728] iwlwifi 0000:0d:00.0: setting latency timer to 64
[   15.140775] iwlwifi 0000:0d:00.0: pci_resource_len = 0x00002000
[   15.140778] iwlwifi 0000:0d:00.0: pci_resource_base = ffffc900118b8000
[   15.140780] iwlwifi 0000:0d:00.0: HW Revision ID = 0x34
[   15.141272] iwlwifi 0000:0d:00.0: irq 52 for MSI/MSI-X
[   15.141446] iwlwifi 0000:0d:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   15.141621] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[   15.159741] iwlwifi 0000:0d:00.0: device EEPROM VER=0x715, CALIB=0x6
[   15.159745] iwlwifi 0000:0d:00.0: Device SKU: 0X1f0
[   15.159748] iwlwifi 0000:0d:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   15.160221] iwlwifi 0000:0d:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.198680] iwlwifi 0000:0d:00.0: loaded firmware version 17.168.5.3 build 42301
[   15.200801] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.243304] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[   17.250341] iwlwifi 0000:0d:00.0: Radio type=0x1-0x2-0x0
[   17.538368] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[   17.545360] iwlwifi 0000:0d:00.0: Radio type=0x1-0x2-0x0
[   50.130053] iwlwifi 0000:0d:00.0: Tx aggregation enabled on ra = 5c:d9:98:c0:d5:14 tid = 0
[   50.304149] iwlwifi 0000:0d:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   50.304160] iwlwifi 0000:0d:00.0: Loaded firmware version: 17.168.5.3 build 42301
[   50.304365] iwlwifi 0000:0d:00.0: Start IWL Error Log Dump:
[   50.304367] iwlwifi 0000:0d:00.0: Status: 0x000412E4, count: 6
[   50.304369] iwlwifi 0000:0d:00.0: 0x00000EDC | ADVANCED_SYSASSERT          
[   50.304371] iwlwifi 0000:0d:00.0: 0x00020DE0 | uPc
[   50.304372] iwlwifi 0000:0d:00.0: 0x00020DA8 | branchlink1
[   50.304373] iwlwifi 0000:0d:00.0: 0x00020DA8 | branchlink2
[   50.304375] iwlwifi 0000:0d:00.0: 0x0000D1F2 | interruptlink1
[   50.304376] iwlwifi 0000:0d:00.0: 0x00000000 | interruptlink2
[   50.304378] iwlwifi 0000:0d:00.0: 0x00000001 | data1
[   50.304379] iwlwifi 0000:0d:00.0: 0x090CFFFF | data2
[   50.304380] iwlwifi 0000:0d:00.0: 0x00000ACA | line
[   50.304382] iwlwifi 0000:0d:00.0: 0x3D4112CB | beacon time
[   50.304383] iwlwifi 0000:0d:00.0: 0x9D661D35 | tsf low
[   50.304384] iwlwifi 0000:0d:00.0: 0x0000001B | tsf hi
[   50.304386] iwlwifi 0000:0d:00.0: 0x00000000 | time gp1
[   50.304387] iwlwifi 0000:0d:00.0: 0x01F3DFED | time gp2
[   50.304388] iwlwifi 0000:0d:00.0: 0x00000000 | time gp3
[   50.304389] iwlwifi 0000:0d:00.0: 0x000111A8 | uCode version
[   50.304391] iwlwifi 0000:0d:00.0: 0x000000B0 | hw version
[   50.304392] iwlwifi 0000:0d:00.0: 0x00480303 | board version
[   50.304393] iwlwifi 0000:0d:00.0: 0x090CFFFF | hcmd
[   50.304395] iwlwifi 0000:0d:00.0: CSR values:
[   50.304396] iwlwifi 0000:0d:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   50.304431] iwlwifi 0000:0d:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[   50.304460] iwlwifi 0000:0d:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   50.304485] iwlwifi 0000:0d:00.0:                     CSR_INT: 0X00000000
[   50.304511] iwlwifi 0000:0d:00.0:                CSR_INT_MASK: 0X00000000
[   50.304537] iwlwifi 0000:0d:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   50.304562] iwlwifi 0000:0d:00.0:                 CSR_GPIO_IN: 0X00000030
[   50.304588] iwlwifi 0000:0d:00.0:                   CSR_RESET: 0X00000000
[   50.304614] iwlwifi 0000:0d:00.0:                CSR_GP_CNTRL: 0X080403c5
[   50.304639] iwlwifi 0000:0d:00.0:                  CSR_HW_REV: 0X000000b0
[   50.304665] iwlwifi 0000:0d:00.0:              CSR_EEPROM_REG: 0X50010ffd
[   50.304690] iwlwifi 0000:0d:00.0:               CSR_EEPROM_GP: 0X90000001
[   50.304716] iwlwifi 0000:0d:00.0:              CSR_OTP_GP_REG: 0X00030001
[   50.304742] iwlwifi 0000:0d:00.0:                 CSR_GIO_REG: 0X00080042
[   50.304767] iwlwifi 0000:0d:00.0:            CSR_GP_UCODE_REG: 0X00002227
[   50.304793] iwlwifi 0000:0d:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   50.304818] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   50.304844] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   50.304870] iwlwifi 0000:0d:00.0:                 CSR_LED_REG: 0X00000058
[   50.304896] iwlwifi 0000:0d:00.0:        CSR_DRAM_INT_TBL_REG: 0X8824fd12
[   50.304921] iwlwifi 0000:0d:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   50.304947] iwlwifi 0000:0d:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   50.304973] iwlwifi 0000:0d:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   50.304998] iwlwifi 0000:0d:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[   50.305000] iwlwifi 0000:0d:00.0: FH register values:
[   50.305048] iwlwifi 0000:0d:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X24f5e100
[   50.305063] iwlwifi 0000:0d:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02418030
[   50.305079] iwlwifi 0000:0d:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000020
[   50.305094] iwlwifi 0000:0d:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   50.305110] iwlwifi 0000:0d:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   50.305132] iwlwifi 0000:0d:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   50.305148] iwlwifi 0000:0d:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   50.305185] iwlwifi 0000:0d:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   50.305200] iwlwifi 0000:0d:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   50.305276] iwlwifi 0000:0d:00.0: Start IWL Event Log Dump: display last 20 entries
[   50.305303] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759465:0x0bb8001c:0206
[   50.305336] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759466:0x00000001:0204
[   50.305375] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759468:0x01101080:0205
[   50.305408] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759494:0x00000020:0208
[   50.305440] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759513:0x00000000:0302
[   50.305473] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759547:0x00000001:0203
[   50.305506] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759552:0x0bb8001c:0206
[   50.305538] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759553:0x00000040:0204
[   50.305577] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759556:0x2b10fbe0:0222
[   50.305617] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759556:0xc0100084:0223
[   50.305649] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759558:0x00000040:0219
[   50.305682] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759559:0x03000090:0211
[   50.305714] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759563:0x00000000:0212
[   50.305747] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759590:0x00000000:0215
[   50.305780] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759593:0x00000008:0220
[   50.305813] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759612:0x00000000:0302
[   50.305845] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759642:0x000000d4:0303
[   50.305878] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759646:0x000010b9:0217
[   50.305917] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759647:0x0bb8001c:0217
[   50.305990] iwlwifi 0000:0d:00.0: EVT_LOGT:0032759809:0x00000000:0125
[   50.306675] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[   50.313687] iwlwifi 0000:0d:00.0: Radio type=0x1-0x2-0x0
[   86.408459] iwlwifi 0000:0d:00.0: Tx aggregation enabled on ra = 5c:d9:98:c0:d5:14 tid = 0
[   86.553432] iwlwifi 0000:0d:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   86.553443] iwlwifi 0000:0d:00.0: Loaded firmware version: 17.168.5.3 build 42301
[   86.553610] iwlwifi 0000:0d:00.0: Start IWL Error Log Dump:
[   86.553613] iwlwifi 0000:0d:00.0: Status: 0x000412E4, count: 6
[   86.553617] iwlwifi 0000:0d:00.0: 0x00000EDC | ADVANCED_SYSASSERT          
[   86.553620] iwlwifi 0000:0d:00.0: 0x00020DE0 | uPc
[   86.553623] iwlwifi 0000:0d:00.0: 0x00020DA8 | branchlink1
[   86.553626] iwlwifi 0000:0d:00.0: 0x00020DA8 | branchlink2
[   86.553628] iwlwifi 0000:0d:00.0: 0x0000D1F2 | interruptlink1
[   86.553631] iwlwifi 0000:0d:00.0: 0x00000000 | interruptlink2
[   86.553634] iwlwifi 0000:0d:00.0: 0x00000001 | data1
[   86.553637] iwlwifi 0000:0d:00.0: 0x79E3EBAE | data2
[   86.553639] iwlwifi 0000:0d:00.0: 0x00000ACA | line
[   86.553642] iwlwifi 0000:0d:00.0: 0x58817FB4 | beacon time
[   86.553644] iwlwifi 0000:0d:00.0: 0x9F90604C | tsf low
[   86.553647] iwlwifi 0000:0d:00.0: 0x0000001B | tsf hi
[   86.553650] iwlwifi 0000:0d:00.0: 0x00000000 | time gp1
[   86.553653] iwlwifi 0000:0d:00.0: 0x022A02EE | time gp2
[   86.553655] iwlwifi 0000:0d:00.0: 0x00000000 | time gp3
[   86.553658] iwlwifi 0000:0d:00.0: 0x000111A8 | uCode version
[   86.553660] iwlwifi 0000:0d:00.0: 0x000000B0 | hw version
[   86.553663] iwlwifi 0000:0d:00.0: 0x00480303 | board version
[   86.553666] iwlwifi 0000:0d:00.0: 0x79E3EBAE | hcmd
[   86.553668] iwlwifi 0000:0d:00.0: CSR values:
[   86.553671] iwlwifi 0000:0d:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   86.553701] iwlwifi 0000:0d:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[   86.553728] iwlwifi 0000:0d:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   86.553756] iwlwifi 0000:0d:00.0:                     CSR_INT: 0X00000000
[   86.553782] iwlwifi 0000:0d:00.0:                CSR_INT_MASK: 0X00000000
[   86.553809] iwlwifi 0000:0d:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   86.553836] iwlwifi 0000:0d:00.0:                 CSR_GPIO_IN: 0X00000030
[   86.553863] iwlwifi 0000:0d:00.0:                   CSR_RESET: 0X00000000
[   86.553890] iwlwifi 0000:0d:00.0:                CSR_GP_CNTRL: 0X080403c5
[   86.553916] iwlwifi 0000:0d:00.0:                  CSR_HW_REV: 0X000000b0
[   86.553943] iwlwifi 0000:0d:00.0:              CSR_EEPROM_REG: 0X50010ffd
[   86.553970] iwlwifi 0000:0d:00.0:               CSR_EEPROM_GP: 0X90000001
[   86.553996] iwlwifi 0000:0d:00.0:              CSR_OTP_GP_REG: 0X00030001
[   86.554034] iwlwifi 0000:0d:00.0:                 CSR_GIO_REG: 0X00080042
[   86.554061] iwlwifi 0000:0d:00.0:            CSR_GP_UCODE_REG: 0X00002820
[   86.554087] iwlwifi 0000:0d:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   86.554114] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   86.554141] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   86.554177] iwlwifi 0000:0d:00.0:                 CSR_LED_REG: 0X00000078
[   86.554208] iwlwifi 0000:0d:00.0:        CSR_DRAM_INT_TBL_REG: 0X8824fd12
[   86.554234] iwlwifi 0000:0d:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   86.554261] iwlwifi 0000:0d:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   86.554288] iwlwifi 0000:0d:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   86.554314] iwlwifi 0000:0d:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   86.554317] iwlwifi 0000:0d:00.0: FH register values:
[   86.554424] iwlwifi 0000:0d:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X24f5e100
[   86.554468] iwlwifi 0000:0d:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02418030
[   86.554505] iwlwifi 0000:0d:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000040
[   86.554549] iwlwifi 0000:0d:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   86.554592] iwlwifi 0000:0d:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   86.554629] iwlwifi 0000:0d:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   86.554672] iwlwifi 0000:0d:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   86.554710] iwlwifi 0000:0d:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   86.554753] iwlwifi 0000:0d:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   86.554911] iwlwifi 0000:0d:00.0: Start IWL Event Log Dump: display last 20 entries
[   86.554964] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307399:0x01101080:0205
[   86.554998] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307425:0x00000020:0208
[   86.555031] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307445:0x00000000:0302
[   86.555065] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307478:0x00000001:0203
[   86.555099] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307483:0x0b83001c:0206
[   86.555133] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307484:0x00000040:0204
[   86.555167] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307487:0x2b110000:0222
[   86.555242] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307488:0xc0100090:0223
[   86.555275] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307490:0x00000040:0219
[   86.555307] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307490:0x03000090:0211
[   86.555340] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307494:0x00000000:0212
[   86.555372] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307521:0x00000000:0215
[   86.555405] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307524:0x00000008:0220
[   86.555437] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307543:0x00000000:0302
[   86.555470] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307574:0x000000d4:0303
[   86.555503] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307578:0x00001784:0217
[   86.555536] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307579:0x0b83001c:0217
[   86.555569] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307649:0x00000482:0511
[   86.555601] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307650:0x00000000:0512
[   86.555634] iwlwifi 0000:0d:00.0: EVT_LOGT:0036307698:0x00000000:0125
[   86.556206] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[   86.563185] iwlwifi 0000:0d:00.0: Radio type=0x1-0x2-0x0
[  145.405462] iwlwifi 0000:0d:00.0: Tx aggregation enabled on ra = 5c:d9:98:c0:d5:14 tid = 0
[  146.940447] iwlwifi 0000:0d:00.0: Microcode SW error detected.  Restarting 0x2000000.
[  146.940452] iwlwifi 0000:0d:00.0: Loaded firmware version: 17.168.5.3 build 42301
[  146.940566] iwlwifi 0000:0d:00.0: Start IWL Error Log Dump:
[  146.940568] iwlwifi 0000:0d:00.0: Status: 0x000412E4, count: 6
[  146.940570] iwlwifi 0000:0d:00.0: 0x00000034 | NMI_INTERRUPT_WDG           
[  146.940572] iwlwifi 0000:0d:00.0: 0x0000F71C | uPc
[  146.940574] iwlwifi 0000:0d:00.0: 0x0000F708 | branchlink1
[  146.940575] iwlwifi 0000:0d:00.0: 0x0000F73A | branchlink2
[  146.940577] iwlwifi 0000:0d:00.0: 0x0000D1F2 | interruptlink1
[  146.940579] iwlwifi 0000:0d:00.0: 0x000194DA | interruptlink2
[  146.940580] iwlwifi 0000:0d:00.0: 0x00000002 | data1
[  146.940582] iwlwifi 0000:0d:00.0: 0x07030000 | data2
[  146.940584] iwlwifi 0000:0d:00.0: 0x0000E1C4 | line
[  146.940585] iwlwifi 0000:0d:00.0: 0x93400AA7 | beacon time
[  146.940587] iwlwifi 0000:0d:00.0: 0xA32BB559 | tsf low
[  146.940589] iwlwifi 0000:0d:00.0: 0x0000001B | tsf hi
[  146.940590] iwlwifi 0000:0d:00.0: 0x00000000 | time gp1
[  146.940592] iwlwifi 0000:0d:00.0: 0x039B1448 | time gp2
[  146.940594] iwlwifi 0000:0d:00.0: 0x00000000 | time gp3
[  146.940595] iwlwifi 0000:0d:00.0: 0x000111A8 | uCode version
[  146.940597] iwlwifi 0000:0d:00.0: 0x000000B0 | hw version
[  146.940599] iwlwifi 0000:0d:00.0: 0x00480303 | board version
[  146.940600] iwlwifi 0000:0d:00.0: 0x0B97001C | hcmd
[  146.940602] iwlwifi 0000:0d:00.0: CSR values:
[  146.940604] iwlwifi 0000:0d:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  146.940633] iwlwifi 0000:0d:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  146.940659] iwlwifi 0000:0d:00.0:          CSR_INT_COALESCING: 0X00000040
[  146.940685] iwlwifi 0000:0d:00.0:                     CSR_INT: 0X00000000
[  146.940711] iwlwifi 0000:0d:00.0:                CSR_INT_MASK: 0X00000000
[  146.940737] iwlwifi 0000:0d:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  146.940764] iwlwifi 0000:0d:00.0:                 CSR_GPIO_IN: 0X00000030
[  146.940790] iwlwifi 0000:0d:00.0:                   CSR_RESET: 0X00000000
[  146.940816] iwlwifi 0000:0d:00.0:                CSR_GP_CNTRL: 0X080403c5
[  146.940842] iwlwifi 0000:0d:00.0:                  CSR_HW_REV: 0X000000b0
[  146.940868] iwlwifi 0000:0d:00.0:              CSR_EEPROM_REG: 0X50010ffd
[  146.940894] iwlwifi 0000:0d:00.0:               CSR_EEPROM_GP: 0X90000001
[  146.940920] iwlwifi 0000:0d:00.0:              CSR_OTP_GP_REG: 0X00030001
[  146.940946] iwlwifi 0000:0d:00.0:                 CSR_GIO_REG: 0X00080042
[  146.940972] iwlwifi 0000:0d:00.0:            CSR_GP_UCODE_REG: 0X0000449d
[  146.940998] iwlwifi 0000:0d:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  146.941024] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  146.941049] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  146.941075] iwlwifi 0000:0d:00.0:                 CSR_LED_REG: 0X00000078
[  146.941102] iwlwifi 0000:0d:00.0:        CSR_DRAM_INT_TBL_REG: 0X8824fd12
[  146.941128] iwlwifi 0000:0d:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  146.941154] iwlwifi 0000:0d:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  146.941180] iwlwifi 0000:0d:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  146.941206] iwlwifi 0000:0d:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  146.941208] iwlwifi 0000:0d:00.0: FH register values:
[  146.941245] iwlwifi 0000:0d:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X24f5e100
[  146.941281] iwlwifi 0000:0d:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02418030
[  146.941321] iwlwifi 0000:0d:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000d8
[  146.941366] iwlwifi 0000:0d:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00819104
[  146.941393] iwlwifi 0000:0d:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  146.941416] iwlwifi 0000:0d:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  146.941444] iwlwifi 0000:0d:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  146.941479] iwlwifi 0000:0d:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  146.941520] iwlwifi 0000:0d:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  146.941630] iwlwifi 0000:0d:00.0: Start IWL Event Log Dump: display last 20 entries
[  146.941683] iwlwifi 0000:0d:00.0: EVT_LOGT:0060292829:0xa3289fec:0636
[  146.941729] iwlwifi 0000:0d:00.0: EVT_LOGT:0060292869:0x000000fa:0106
[  146.941768] iwlwifi 0000:0d:00.0: EVT_LOGT:0060292871:0x00000000:0301
[  146.941808] iwlwifi 0000:0d:00.0: EVT_LOGT:0060293246:0x00000080:0313
[  146.941847] iwlwifi 0000:0d:00.0: EVT_LOGT:0060293248:0x00000576:0501
[  146.941892] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294844:0x000002c0:0501
[  146.941926] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294850:0x00000000:0504
[  146.941971] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294852:0x00000000:0504
[  146.942017] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294852:0x0000006e:0601
[  146.942063] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294852:0x9301882b:0600
[  146.942109] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294853:0x0000008e:0601
[  146.942155] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294854:0x9301882b:0600
[  146.942188] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294854:0x01000000:0600
[  146.942221] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294865:0x00c01007:0310
[  146.942266] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294879:0x000000e5:0601
[  146.942300] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294887:0x0000024d:0635
[  146.942332] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294922:0x000000fa:0106
[  146.942365] iwlwifi 0000:0d:00.0: EVT_LOGT:0060294923:0x00000000:0301
[  146.942398] iwlwifi 0000:0d:00.0: EVT_LOGT:0060494916:0x000000f6:0123
[  146.942431] iwlwifi 0000:0d:00.0: EVT_LOGT:0060494940:0x00000000:0125
[  146.943162] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[  146.950202] iwlwifi 0000:0d:00.0: Radio type=0x1-0x2-0x0
[  155.886057] iwlwifi 0000:0d:00.0: Tx aggregation enabled on ra = 5c:d9:98:c0:d5:14 tid = 0
[  155.934996] iwlwifi 0000:0d:00.0: Microcode SW error detected.  Restarting 0x82000000.
[  155.935007] iwlwifi 0000:0d:00.0: Loaded firmware version: 17.168.5.3 build 42301
[  155.935283] iwlwifi 0000:0d:00.0: Start IWL Error Log Dump:
[  155.935289] iwlwifi 0000:0d:00.0: Status: 0x000412E4, count: 6
[  155.935296] iwlwifi 0000:0d:00.0: 0x00000EDC | ADVANCED_SYSASSERT          
[  155.935301] iwlwifi 0000:0d:00.0: 0x00020DE0 | uPc
[  155.935306] iwlwifi 0000:0d:00.0: 0x00020DA8 | branchlink1
[  155.935340] iwlwifi 0000:0d:00.0: 0x00020DA8 | branchlink2
[  155.935345] iwlwifi 0000:0d:00.0: 0x0000D1F2 | interruptlink1
[  155.935350] iwlwifi 0000:0d:00.0: 0x00000000 | interruptlink2
[  155.935355] iwlwifi 0000:0d:00.0: 0x00000001 | data1
[  155.935359] iwlwifi 0000:0d:00.0: 0x7473FFFF | data2
[  155.935364] iwlwifi 0000:0d:00.0: 0x00000ACA | line
[  155.935368] iwlwifi 0000:0d:00.0: 0x15800303 | beacon time
[  155.935373] iwlwifi 0000:0d:00.0: 0xA3B53CFD | tsf low
[  155.935377] iwlwifi 0000:0d:00.0: 0x0000001B | tsf hi
[  155.935382] iwlwifi 0000:0d:00.0: 0x00000000 | time gp1
[  155.935386] iwlwifi 0000:0d:00.0: 0x0089443F | time gp2
[  155.935391] iwlwifi 0000:0d:00.0: 0x00000000 | time gp3
[  155.935395] iwlwifi 0000:0d:00.0: 0x000111A8 | uCode version
[  155.935400] iwlwifi 0000:0d:00.0: 0x000000B0 | hw version
[  155.935405] iwlwifi 0000:0d:00.0: 0x00480303 | board version
[  155.935409] iwlwifi 0000:0d:00.0: 0x7473FFFF | hcmd
[  155.935414] iwlwifi 0000:0d:00.0: CSR values:
[  155.935419] iwlwifi 0000:0d:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[  155.935452] iwlwifi 0000:0d:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[  155.935484] iwlwifi 0000:0d:00.0:          CSR_INT_COALESCING: 0X0000ff40
[  155.935517] iwlwifi 0000:0d:00.0:                     CSR_INT: 0X00000000
[  155.935549] iwlwifi 0000:0d:00.0:                CSR_INT_MASK: 0X00000000
[  155.935582] iwlwifi 0000:0d:00.0:           CSR_FH_INT_STATUS: 0X00000000
[  155.935615] iwlwifi 0000:0d:00.0:                 CSR_GPIO_IN: 0X00000030
[  155.935647] iwlwifi 0000:0d:00.0:                   CSR_RESET: 0X00000000
[  155.935677] iwlwifi 0000:0d:00.0:                CSR_GP_CNTRL: 0X080403c5
[  155.935708] iwlwifi 0000:0d:00.0:                  CSR_HW_REV: 0X000000b0
[  155.935738] iwlwifi 0000:0d:00.0:              CSR_EEPROM_REG: 0X50010ffd
[  155.935770] iwlwifi 0000:0d:00.0:               CSR_EEPROM_GP: 0X90000001
[  155.935802] iwlwifi 0000:0d:00.0:              CSR_OTP_GP_REG: 0X00030001
[  155.935835] iwlwifi 0000:0d:00.0:                 CSR_GIO_REG: 0X00080042
[  155.935868] iwlwifi 0000:0d:00.0:            CSR_GP_UCODE_REG: 0X00000846
[  155.935901] iwlwifi 0000:0d:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[  155.935934] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[  155.935963] iwlwifi 0000:0d:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[  155.935995] iwlwifi 0000:0d:00.0:                 CSR_LED_REG: 0X00000078
[  155.936027] iwlwifi 0000:0d:00.0:        CSR_DRAM_INT_TBL_REG: 0X8824fd12
[  155.936060] iwlwifi 0000:0d:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[  155.936093] iwlwifi 0000:0d:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[  155.936125] iwlwifi 0000:0d:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[  155.936158] iwlwifi 0000:0d:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[  155.936163] iwlwifi 0000:0d:00.0: FH register values:
[  155.936225] iwlwifi 0000:0d:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X24f5e100
[  155.936285] iwlwifi 0000:0d:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X02418030
[  155.936347] iwlwifi 0000:0d:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000080
[  155.936408] iwlwifi 0000:0d:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[  155.936470] iwlwifi 0000:0d:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[  155.936530] iwlwifi 0000:0d:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[  155.936600] iwlwifi 0000:0d:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[  155.936661] iwlwifi 0000:0d:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[  155.936721] iwlwifi 0000:0d:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[  155.936902] iwlwifi 0000:0d:00.0: Start IWL Event Log Dump: display last 20 entries
[  155.936975] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995385:0x00000000:0302
[  155.937027] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995418:0x00000001:0203
[  155.937079] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995423:0x0b19001c:0206
[  155.937132] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995424:0x00000040:0204
[  155.937178] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995427:0x2b1048df:0222
[  155.937231] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995427:0xc0100084:0223
[  155.937277] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995429:0x00000040:0219
[  155.937329] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995430:0x03000090:0211
[  155.937382] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995434:0x00000000:0212
[  155.937428] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995461:0x00000000:0215
[  155.937481] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995464:0x00000008:0220
[  155.937534] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995483:0x00000000:0302
[  155.937586] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995513:0x000000d4:0303
[  155.937639] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995517:0x0000141a:0217
[  155.937691] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995518:0x0b19001c:0217
[  155.937744] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995637:0x000000fa:0106
[  155.937796] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995639:0x00000000:0302
[  155.937849] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995785:0x000000d4:0322
[  155.937901] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995815:0x0066171f:0310
[  155.937954] iwlwifi 0000:0d:00.0: EVT_LOGT:0008995923:0x00000000:0125
[  155.939058] iwlwifi 0000:0d:00.0: L1 Enabled; Disabling L0S
[  155.946120] iwlwifi 0000:0d:00.0: Radio type=0x1-0x2-0x0

```

kernel:
3.2.0-24-generic

Thanks

---

### Post by chili555 on 2012-05-11
It's having a problem with loading the firmware:> 
[  155.886057] iwlwifi 0000:0d:00.0: Tx aggregation enabled on ra = 5c:d9:98:c0:d5:14 tid = 0
[  155.934996] iwlwifi 0000:0d:00.0: [COLOR="Red"]Microcode SW error detected.[/COLOR]  Restarting 0x82000000.
[  155.935007] iwlwifi 0000:0d:00.0: [COLOR="Red"]Loaded firmware version[/COLOR]: 17.168.5.3 build 42301
[  155.935283] iwlwifi 0000:0d:00.0: [COLOR="Red"]Start IWL Error Log Dump[/COLOR]:Let's try one thing first and then try to verify the integrity of your firmware packages. Please open a terminal and do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Any change or improvement? Also please post:```
md5sum /lib/firmware/iwlwifi*
```It will be helpful to see the wireless part of this:```
sudo lshw -C network
```

---

### Post by cjmanders on 2012-05-11
Not sure why my last post was mangled, but here is another go.

My symptoms are best described by bluetooth icon is LIT, not no wireless appears to exist, even though on mine, the Centrino Advanced-N 6230, they are part of the same controller.

Thoughts?

Do I need the firmware?

**$ rfkill list all**
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
3: dell-wwan: Wireless WAN
    Soft blocked: yes
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

**$ sudo modprobe iwlwifi**
FATAL: Module iwlwifi not found.

**$ dmesg|grep iwl**
[   23.832460] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   23.832462] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   23.832552] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.832590] iwlagn 0000:03:00.0: setting latency timer to 64
[   23.832662] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[   23.849742] iwlagn 0000:03:00.0: device EEPROM VER=0x716, CALIB=0x6
[   23.849744] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   23.849745] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   23.849777] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   23.850046] iwlagn 0000:03:00.0: irq 54 for MSI/MSI-X
[   23.927297] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2b-5.ucode' failed.
[   23.928223] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2b-4.ucode' failed.
[   23.928225] iwlagn 0000:03:00.0: no suitable firmware found!
[   23.928448] iwlagn 0000:03:00.0: PCI INT A disabled

**$ sudo lspci -nn | grep 0280**
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)

**$ sudo iwconfig wlan0 power off**
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.
[B]
$ sudo  cp  iwlwifi-6000g2b-5.ucode  /lib/firmware[/B]
cp: cannot stat `iwlwifi-6000g2b-5.ucode': No such file or directory
--big q on whether i need to get the new/existing firmware and install?

**$ sudo modprobe iwlagn power_level=5**
--success! at least no errors.

**$ sudo modprobe iwlagn power_level=5**
--again, no errors.

**$ sudo rfkill unblock all**
--again, no errors.
[B]
last part of dmesg when I do a Fn+F2:[/B]
[ 4269.329152] usb 2-1.5: USB disconnect, device number 5
[ 4269.329284] btusb_intr_complete: hci0 urb ffff88019d663540 failed to resubmit (19)
[ 4269.329299] btusb_bulk_complete: hci0 urb ffff88019d663300 failed to resubmit (19)
[ 4269.329415] btusb_bulk_complete: hci0 urb ffff88019d663840 failed to resubmit (19)
[ 4269.329462] btusb_send_frame: hci0 urb ffff88019d6c6900 submission failed

---

### Post by cjmanders on 2012-05-11
Also, I have tried:

**$ sudo modprobe -r iwlwifi**
FATAL: Module iwlwifi not found.

**$ sudo modprobe iwlwifi 11n_disable=1**
FATAL: Module iwlwifi not found.

[B]$ ls /lib/firmware/*iwlwifi*
[/B]/lib/firmware/iwlwifi-1000-5.ucode  /lib/firmware/iwlwifi-4965-2.ucode
/lib/firmware/iwlwifi-100-5.ucode   /lib/firmware/iwlwifi-5000-5.ucode
/lib/firmware/iwlwifi-105-6.ucode   /lib/firmware/iwlwifi-5150-2.ucode
/lib/firmware/iwlwifi-135-6.ucode   /lib/firmware/iwlwifi-6000-4.ucode
/lib/firmware/iwlwifi-2000-6.ucode  /lib/firmware/iwlwifi-6000g2a-5.ucode
/lib/firmware/iwlwifi-2030-6.ucode  /lib/firmware/iwlwifi-6000g2b-6.ucode
/lib/firmware/iwlwifi-3945-2.ucode  /lib/firmware/iwlwifi-6050-5.ucode

**$ sudo lshw -C network**
  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Advanced-N 6230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f1b00000-f1b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: aa:00:04:00:0a:04
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=10.0.0.250 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes

I appear to be lacking the module?

---

### Post by chili555 on 2012-05-11
> [ 23.832460] [COLOR="Red"]iwlagn[/COLOR]: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:iwlagn is the module for Ubuntu versions prior to 12.04. The title of this thread is 'Wireless not working *after 12.04 upgrade*.' Can you please clarify? Or, better yet, start a new thread and ask there.

---

### Post by cjmanders on 2012-05-12
Ah! 

Well, my problems are AFTER UPGRADE to 12.04.

Wireless worked in pre-12.04.

I will open another thread if necessary, but this is where I think my discussion belongs.

I am just about to upgrade back to 11.10 if I can't get it working in post upgrade to 12.04.

No help??

**$ uname -a**
Linux NaCl03 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

**$ cat /etc/issue**
Ubuntu 12.04 LTS \n \l

So far no big need for me to upgrade to 12.04, since it seems to have been a serious downgrade so far.

Is there really no help to be had on this subject?

Do I need to post in *more* forums?

Thanks in advance!

Considerate and thoughtful replies much appreciated.

---

### Post by cjmanders on 2012-05-12
Ah ha!

The ANSWER! It is not solved, but an answer is what I needed.

+++++++++
[Résolu] Carte Intel centrino N 3600 ne fonctione pas sur Ubuntu 12.04.
+++++++++

Translation: The Intel Centrino N 3600 does not function (and does not appear to be supported) by Ubuntu 12.04 (yet).

I should have known it was not supported. 

Thank god for multiple language support.

And, special thanks to the other more helpful users around the world.

And, of course, for being able to understand them!

If I had stopped with English I would not have found the answer. 

Le Français est une langue merveilleuse. J'aime le Français beaucoup.

Les orateurs de l'anglais seulement sont si arrogants, après tous. 

LOL!

Thank you so much for all of the helpful comments.

I am going back to 11.10 where things worked and then wait for my hardware to, in fact, be supported.

If anyone does get this working, please post the answer.

And, meanwhile I will continue to follow the French posts, since they appear to be on target so far for me.

Ciao!

---

### Post by chili555 on 2012-05-12
I find it very difficult to accept that an Intel wireless device was correctly supported in 11.10 but not (yet??) in 12.04. Moreover, this kernel is for 11.10 and not 12.04:> Linux NaCl03 [COLOR="Red"]3.0.0-17-generic[/COLOR] Here is my 12.04 kernel:> $ uname -r
[COLOR="Red"]**3.2**[/COLOR].0-24-generic-paeYour first post says:> 03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N [COLOR="Red"]6230[/COLOR] [8086:0091] (rev 34) Your post just above says:> [Résolu] Carte Intel centrino N [COLOR="Red"]3600[/COLOR] ne fonctione pas sur Ubuntu 12.04.I am unaware of *any* Intel Centrino wireless chipset that is not supported in Ubuntu 12.04.

---

### Post by scrapper82 on 2012-05-13
@chili555
> I am unaware of *any* Intel Centrino wireless chipset that is not supported in Ubuntu 12.04. 	


Network controller: Intel Corporation Centrino Wireless-N 1030 (rev34) 
supported - MAYBE
working - NO
wifi access point WPA/WPA2 Personal 

The wifi connection with the router gets established and seems to work. But no data transfer is possible.
No browser, no ping, no traceroute ...
So the wireless lan is not working on fresh Ubuntu 12.04 precise.

No fix so far...

Good luck

---

### Post by scrapper82 on 2012-05-13
I now fixxed the problem with the 12.04 instructions.
Thanks to this post: [http://askubuntu.com/questions/130499/how-do-i-fix-slow-wireless-on-intel-wireless-cards/131749#131749](http://askubuntu.com/questions/130499/how-do-i-fix-slow-wireless-on-intel-wireless-cards/131749#131749)

Quick and fast solution.

have fun!

---

### Post by cjmanders on 2012-05-13
Interesting.

I tried that and got some extra data in my /var/log/messages:

[172462.745920] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[172462.745931] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[172462.746122] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[172462.746209] iwlagn 0000:03:00.0: setting latency timer to 64
[172462.746503] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[172462.764220] iwlagn 0000:03:00.0: device EEPROM VER=0x716, CALIB=0x6
[172462.764227] iwlagn 0000:03:00.0: Device SKU: 0Xb
[172462.764231] iwlagn 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[172462.764295] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[172462.764669] iwlagn 0000:03:00.0: irq 55 for MSI/MSI-X
[172462.778047] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2b-5.ucode' failed.
[172462.780307] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2b-4.ucode' failed.
[172462.780321] iwlagn 0000:03:00.0: no suitable firmware found!
[172462.780933] iwlagn 0000:03:00.0: PCI INT A disabled
[172483.247931] usb 2-1.5: new full speed USB device number 6 using ehci_hcd
[172546.955608] usb 2-1.5: USB disconnect, device number 6
[172546.955650] btusb_bulk_complete: hci0 urb ffff880154511f00 failed to resubmit (19)
[172546.955678] btusb_intr_complete: hci0 urb ffff880154511840 failed to resubmit (19)
[172546.955785] btusb_bulk_complete: hci0 urb ffff880154511540 failed to resubmit (19)
[172546.956003] btusb_send_frame: hci0 urb ffff88019d6b20c0 submission failed


Looks like a firmware thing?

Well, I am going to re-install instead of upgrading. If there is support then it may be an upgrade issue.

We shall see.

back in a bit.

---

### Post by dewapur on 2012-05-25
Hi I think I can post my problem here since it's upgraded from Natty and the wireless worked for sometimes until today.

After search maybe all and all through google and other threads here but seem can't solve my problem. I already put ```
options iwlwifi 11n_disable=1
``` as a file in the /etc/modprobe.d/iwlwifi.conf but the result is still the same, my wireless isn't working. Is there any other way or did I miss something?

I'm using thinkpad edge e120 with checking point as follows :

uname -mr
```
3.2.0-24-generic x86_64
```
rfkill list
```
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```
dmesg | grep iwl
```
[   21.399454] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.399473] iwlwifi 0000:02:00.0: setting latency timer to 64
[   21.399508] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   21.399513] iwlwifi 0000:02:00.0: pci_resource_base = ffffc90005098000
[   21.399517] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   21.399639] iwlwifi 0000:02:00.0: irq 42 for MSI/MSI-X
[   21.399695] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   21.399779] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   21.421333] iwlwifi 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   21.421340] iwlwifi 0000:02:00.0: Device SKU: 0X50
[   21.421344] iwlwifi 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   21.422853] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   21.427944] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[   21.718853] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138
[   21.723517] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

```
lshw -C network
```
  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:a5:3f:cc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:42 memory:e1500000-e1501fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: e8:9a:8f:4e:e6:80
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:e0c00000-e0c3ffff ioport:2000(size=128)

```

---

### Post by chili555 on 2012-05-25
> RF_KILL bit toggled to disable radio.> 1: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="Red"]Hard blocked: yes[/COLOR]Please move the wireless switch back to ON.

---

### Post by dewapur on 2012-05-25
> **chili555 said:**
> Please move the wireless switch back to ON.
I can't find anything that can be used as hardswitch on my laptop. It seem it doesn't come with the hardswitch as mentioned [here]("http://forums.lenovo.com/t5/ThinkPad-Edge/E120-how-to-turn-on-off-wifi-using-ONLY-keyboard/td-p/747779"). Is there any workaround ?

thanks for the reply

---

### Post by chili555 on 2012-05-25
What happens when you press the Fn+F9 combination?```
rfkill list all
```How about F9?```
rfkill list all
```

---

### Post by dewapur on 2012-05-26
before push wireless button on keyboard :
```
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

```After push the button :
```
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
It seem first, the wireless was ON and in the second one, the wireless is OFF but it didn't affect Wifi

---

### Post by chili555 on 2012-05-26
Is, perhaps, the key combination sequential; something like first press turns off wireless, second turns off wireless and bluetooth, third turns on wireless but bluetooth is still off and fourth press is all on? Please experiment and keep checking rfkill.

Is *thinkpad_acpi* loaded?```
lsmod | grep think
```

---

### Post by dewapur on 2012-05-26
here is the result of lsmod
```
thinkpad_acpi          81819  0 
snd                    78855  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
nvram                  14413  1 thinkpad_acpi
```
If I pressed the button repeatedly, it shows repeatedly the output as previous post. So I guess it doesn't work sequentially. Before yesterday wifi worked normally. This makes me wonder what the cause...

---

### Post by chili555 on 2012-05-26
This is a long shot, but please try:```
sudo modprobe -r thinkpad_acpi
sudo modprobe thinkpad_acpi wlsw_state=ON
sudo rfkill unblock all
rfkill list all
```Any errors, warnings or other messages are important; please note and post them.

---

### Post by dewapur on 2012-05-27
After I remove thinkpad_acpi, bluetooth was directly enabled. To check  this I put again the mod and check bluetooth condition then remove  thinkpad_acpi and check the wireless. The sequence as follows:
This is initial condition.
```

deka@light:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
12: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
14: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
After I remove thinkpad_acpi. Bluetooth become enabled. I tried to unblock but Wifi only soft switch that enabled.
```

deka@light:~$ sudo modprobe -r thinkpad_acpi
[sudo] password for deka:
deka@light:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
14: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
deka@light:~$ sudo rfkill unblock all
deka@light:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
14: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
I tried to insert the module again. But it seem argument wasn't correct.  I put back again the module with no argument and check the rfkill. It  seem all wireless is OFF.
```

deka@light:~$ sudo modprobe thinkpad_acpi wlsw_state=ON
FATAL: Error inserting thinkpad_acpi  (/lib/modules/3.2.0-24-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko):  Invalid argument
deka@light:~$ sudo modprobe thinkpad_acpi
deka@light:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
15: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

```
I push the wireless button :
```

deka@light:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
15: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
17: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

After doing these steps, it seem the problem is in thinkpad acpi, isn't  it? Also when I checked the Setting in Network, Airplane Mode is turned  ON and it can't be OFF. It is turn back to ON when I close the window.  This could be something... I am currently online by USB modem.

---

### Post by chili555 on 2012-05-27
> deka@light:~$ sudo modprobe thinkpad_acpi wlsw_state=ON
FATAL: Error inserting thinkpad_acpi  (/lib/modules/3.2.0-24-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko):  Invalid argumentCan you try again with:```
sudo modprobe -r thinkpad_acpi
sudo modprobe thinkpad_acpi wlsw_state=[COLOR="Red"]1[/COLOR]
sudo rfkill unblock all
rfkill list all
```The fault surely is with thinkpad_acpi. That's the little module that's supposed to translate Fn+F9 into action.

Here is a snip from your User Guide that I'm attaching for reference.

Is there any relevant setting in the computer's BIOS?

---

### Post by dewapur on 2012-05-27
I did it like this :
```

deka@light:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
deka@light:~$ sudo modprobe -r thinkpad_acpi
[sudo] password for deka: 
deka@light:~$ sudo modprobe thinkpad_acpi wlsw_state=1
deka@light:~$ sudo rfkill unblock all
deka@light:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: yes
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

Regarding User Guide, it is for use with Windows so it can use ThinkVantage Connection (a program provided by Lenovo for Windows OS). BIOS setting already set to enabled. If I look in [here]("http://www.thinkwiki.org/wiki/Thinkpad-acpi"), still not sure what to do with the info...

---

### Post by chili555 on 2012-05-27
Sadly, I'm not sure there is much you can do except add to an existing bug or file a new one: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I've tried everything I know to do and we haven't for a second cured wireless hard blocked.

I am sorry I could not be of more help.

PS - I think I'd try the live CD for 11.10; if the wireless works, I'd install it. Then, later, I'd try the live CD for subsequent versions until your Lenovo, thinkpad_acpi and Ubuntu all cooperate.

---

### Post by richardh9936 on 2012-05-27
thanks.  "rfkill" listed the problem - soft-blocked.  and Fn F2 fixed that step.  Then the rest was just following the menus in the top bar.  I can now connect to my Time Capsule (apple airport express).

---

### Post by cjmanders on 2012-06-02
Hi again,

I am back after my upgrade back down to 11.10 from 12.04. 
What a pain in the patutkas.

Just an FYI that the roll-back *did* solve my new Dell laptop L502X system's Intel Centrino 6230 N, and several other minor, issues.

While I know the whole of Intel wireless cards are *supposed* to work in Ubuntu 12.04, I was not able to get it to work at all under 12.04 (see my previous post). In point of fact, the solution was automatic in 11.10.

lsmod in 12.04 did *not* show the iwlagn module loaded, even after several changes and modprobes of the module ($sudo modprobe iwlagn). The module was definitely there for the attempt to load in 12.04, but was *not* functioning properly (i.e. gave errors that I reported in my previous post). Not sure what the issue is, but by rolling back to 11.10 everything works fine.

lsmod |grep iwlagn shows that the module is there. The wifi light on the laptop lights up, too! YaY!

I will stick with 11.10 for now until things are smoothed out with the other areas as well (my volume control in 12.04 was weird, the HDMI still does not work properly, and somehow ALT+TABing through my apps stopped with the upgrade). I know these are somewhat minor, but why upgrade when things are functional, after all.

Perhaps in 12.10 things will be better.

All the best for anyone else with the same issue.

---

### Post by chili555 on 2012-06-02
> lsmod in 12.04 did *not* show the iwlagn module loaded, As of 12.04, the name of the module is changed to *iwlwifi*.

---

### Post by espenore on 2012-06-14
Dell Inspiron Mini 1018: My Wifi did work for some time after I upgraded to 12.04 but then never came back on after I turned off the software (in System settings, Network). Instead it became stuck in Airplane mode, and whenever I try tu turn that off it sets itself back. I have also tried to start the computer from a live 11.10, and I have reinstalled from scratch 12.04 a couple of times. The 1018 dows not have a separate wireless swicth, instead it is supposed to use the media-F2 (or Fn-F2 depending on BIOS-setting, have tried both). It seems to me that Ubuntu does not react to the F2-button although the other buttns such as sound volume and screen light do work. The NetworkConfig tab claims that the wireless has been turned off by a switch, and it seems that something has been set deep inside the computer. I would be grateful for any help - I have tried (I believe) everything suggested in various threads here as far is it could be related to this computer system and network hardware.

rfkill list all:


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


sudo lshw -C network:

...

  *-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:9f:c0:ec
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-25-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:f0100000-f0103fff

---------------
Espen

---

### Post by chili555 on 2012-06-14
You might try this: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/875668](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/875668)> set default bios configuration solved the problem.

---

### Post by espenore on 2012-06-14
> **chili555 said:**
> You might try this: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/875668](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/875668)

I do not understand: I have checked in the BIOS-setting that Wifi is turned on. Is there anything else I can do? Does:

"set default bios configuration solved the problem.
Even if wifi adapter was enabled."

mean anything else?

Espen

---

### Post by chili555 on 2012-06-14
> **espenore said:**
> I do not understand: I have checked in the BIOS-setting that Wifi is turned on. Is there anything else I can do? Does:

"set default bios configuration solved the problem.
Even if wifi adapter was enabled."

mean anything else?

EspenI believe they are suggesting you go into the BIOS and reset everything to default. In some BIOS' it is F9 followed by F10 to save and exit. I don't have a Dell, so I can't be sure what yours is.

Please see F9 and F10 in the attached.

---

### Post by espenore on 2012-06-14
> **chili555 said:**
> I believe they are suggesting you go into the BIOS and reset everything to default. In some BIOS' it is F9 followed by F10 to save and exit. I don't have a Dell, so I can't be sure what yours is.

Please see F9 and F10 in the attached.

Thank you very much! This was the solution, indeed. (And yes, on the Dell Insprion Mini 1018 it is the F9, F10-combination.) I am happily sending this with a Wifi connection and the ethernet plug removed.

Espen

---

### Post by chili555 on 2012-06-14
> **espenore said:**
> Thank you very much! This was the solution, indeed. (And yes, on the Dell Insprion Mini 1018 it is the F9, F10-combination.) I am happily sending this with a Wifi connection and the ethernet plug removed.

EspenAwesome! I think the unspoken message is don't ever touch the Fn+F2 combination or disable wireless in Network Manager unless you want to start over in the BIOS. 

Great news!

---

