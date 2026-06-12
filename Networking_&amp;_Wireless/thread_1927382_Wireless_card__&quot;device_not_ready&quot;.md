---
title: "Wireless card  &quot;device not ready&quot;"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by jgraham5481 on 2012-02-17
Hello, Im using an HP g71 Laptop, core2duo, 4 gigs ram, 320 gig HD, have HD partitioned for win7 and Ubuntu 11.10 64 bit. The wireless card in this machine is an Intel wifi link 1000 BGN. When I go to use the card it says "Device not ready". If I press the hardware button, it then says "Device disabled by hardware", I've redownloaded the driver from intel, something like iwlwifi-1000-5.ucode, but when i attempt to install, it says access denied and I don't remember how to remount as RW, i know its similar to an android phone, but I don't recall exactly. Anyone have any ideas???? Any help is greatly appreciated.... btw, the wired ethernet port works fine.

---

### Post by praseodym on 2012-02-18
Hi,

please show the following outputs of the terminal commands (ctrl+alt+t):

```
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep iwl
iwconfig
```
If the firmware is located in "Downloads" copy it to the right place via:

```
sudo cp ~/Downloads/iwlwifi-1000-5.ucode /lib/firmware
```

---

### Post by jgraham5481 on 2012-02-18
> **praseodym said:**
> Hi,

please show the following outputs of the terminal commands (ctrl+alt+t):

```
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep iwl
iwconfig
```If the firmware is located in "Downloads" copy it to the right place via:

```
sudo cp ~/Downloads/iwlwifi-1000-5.ucode /lib/firmware
```


I tried to reinstall the driver with your command and it still does the same thing. Here are the results from the queries....

[CODE] lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlagn
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:306b]
    Kernel driver in use: r8169



[CODE] lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
joydev                 17693  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
arc4                   12529  2 
snd_hda_codec_hdmi     32040  1 
hp_wmi                 18092  0 
snd_hda_codec_idt      70553  1 
sparse_keymap          13890  1 hp_wmi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                73882  0 
serio_raw              13166  0 
binfmt_misc            17540  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
iwlagn                314257  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  571221  3 
wmi                    19256  1 hp_wmi
mac80211              462046  1 iwlagn
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199630  2 iwlagn,mac80211
soundcore              12680  1 snd
i2c_algo_bit           13423  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
r8169                  52788  0 


[CODE]dmesg | grep iwl
[   20.136968] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   20.136972] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   20.137059] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.137068] iwlagn 0000:02:00.0: setting latency timer to 64
[   20.139384] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   20.157597] iwlagn 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   20.157600] iwlagn 0000:02:00.0: Device SKU: 0X9
[   20.157602] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   20.531622] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   20.531706] iwlagn 0000:02:00.0: irq 45 for MSI/MSI-X
[   21.145540] iwlagn 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138
[   21.181251] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.337289] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   21.337296] iwlagn 0000:02:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   21.337371] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
[   21.337374] iwlagn 0000:02:00.0: Status: 0x00040224, count: 5
[   21.337377] iwlagn 0000:02:00.0: 0x00000005 | SYSASSERT                   
[   21.337379] iwlagn 0000:02:00.0: 0x00016E00 | uPc
[   21.337381] iwlagn 0000:02:00.0: 0x00016E00 | branchlink1
[   21.337387] iwlagn 0000:02:00.0: 0x00016E00 | branchlink2
[   21.337389] iwlagn 0000:02:00.0: 0x00000000 | interruptlink1
[   21.337391] iwlagn 0000:02:00.0: 0x00000000 | interruptlink2
[   21.337393] iwlagn 0000:02:00.0: 0x00000000 | data1
[   21.337395] iwlagn 0000:02:00.0: 0x00000000 | data2
[   21.337397] iwlagn 0000:02:00.0: 0x00000616 | line
[   21.337399] iwlagn 0000:02:00.0: 0x00018BCA | beacon time
[   21.337401] iwlagn 0000:02:00.0: 0x00000436 | tsf low
[   21.337403] iwlagn 0000:02:00.0: 0x00000000 | tsf hi
[   21.337405] iwlagn 0000:02:00.0: 0x00000000 | time gp1
[   21.337408] iwlagn 0000:02:00.0: 0x0000043A | time gp2
[   21.337410] iwlagn 0000:02:00.0: 0x00000000 | time gp3
[   21.337412] iwlagn 0000:02:00.0: 0x0001271F | uCode version
[   21.337414] iwlagn 0000:02:00.0: 0x0000006C | hw version
[   21.337416] iwlagn 0000:02:00.0: 0x00C80300 | board version
[   21.337418] iwlagn 0000:02:00.0: 0x00000000 | hcmd
[   21.337420] iwlagn 0000:02:00.0: CSR values:
[   21.337422] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   21.337429] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   21.337434] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[   21.337438] iwlagn 0000:02:00.0:                     CSR_INT: 0X80000000
[   21.337443] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   21.337451] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   21.337456] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[   21.337461] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
[   21.337466] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   21.337471] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X0000006c
[   21.337476] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   21.337480] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000001
[   21.337485] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00210801
[   21.337490] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[   21.337495] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   21.337500] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   21.337504] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   21.337512] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   21.337517] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[   21.337522] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   21.337526] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   21.337532] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[   21.337537] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   21.337542] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   21.337544] iwlagn 0000:02:00.0: FH register values:
[   21.337559] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X12707b00
[   21.337572] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0124d160
[   21.337585] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   21.337597] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   21.337610] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   21.337623] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   21.337636] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   21.337648] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   21.337664] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   21.337714] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 5 entries
[   21.337731] iwlagn 0000:02:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   21.337741] iwlagn 0000:02:00.0: EVT_LOGT:0000000021:0x00000000:1208
[   21.337751] iwlagn 0000:02:00.0: EVT_LOGT:0000001003:0x00000001:0071
[   21.337762] iwlagn 0000:02:00.0: EVT_LOGT:0000001079:0x00000002:0071
[   21.337772] iwlagn 0000:02:00.0: EVT_LOGT:0000001085:0x00000000:0125
[   21.338271] iwlagn 0000:02:00.0: Failed to run INIT ucode: -5
[   21.338309] iwlagn 0000:02:00.0: Unable to initialize device.
[   21.378069] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   21.378076] iwlagn 0000:02:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   21.378151] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
[   21.378154] iwlagn 0000:02:00.0: Status: 0x00040224, count: 5
[   21.378157] iwlagn 0000:02:00.0: 0x00000005 | SYSASSERT                   
[   21.378159] iwlagn 0000:02:00.0: 0x00016E00 | uPc
[   21.378161] iwlagn 0000:02:00.0: 0x00016E00 | branchlink1
[   21.378164] iwlagn 0000:02:00.0: 0x00016E00 | branchlink2
[   21.378166] iwlagn 0000:02:00.0: 0x00000000 | interruptlink1
[   21.378168] iwlagn 0000:02:00.0: 0x00000000 | interruptlink2
[   21.378170] iwlagn 0000:02:00.0: 0x00000000 | data1
[   21.378172] iwlagn 0000:02:00.0: 0x00000000 | data2
[   21.378174] iwlagn 0000:02:00.0: 0x00000616 | line
[   21.378176] iwlagn 0000:02:00.0: 0x00018BCA | beacon time
[   21.378178] iwlagn 0000:02:00.0: 0x00000436 | tsf low
[   21.378180] iwlagn 0000:02:00.0: 0x00000000 | tsf hi
[   21.378182] iwlagn 0000:02:00.0: 0x00000000 | time gp1
[   21.378184] iwlagn 0000:02:00.0: 0x0000043B | time gp2
[   21.378187] iwlagn 0000:02:00.0: 0x00000000 | time gp3
[   21.378189] iwlagn 0000:02:00.0: 0x0001271F | uCode version
[   21.378191] iwlagn 0000:02:00.0: 0x0000006C | hw version
[   21.378193] iwlagn 0000:02:00.0: 0x00C80300 | board version
[   21.378195] iwlagn 0000:02:00.0: 0x00000000 | hcmd
[   21.378197] iwlagn 0000:02:00.0: CSR values:
[   21.378199] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   21.378205] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   21.378210] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[   21.378215] iwlagn 0000:02:00.0:                     CSR_INT: 0X80000000
[   21.378220] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   21.378225] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   21.378230] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[   21.378235] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
[   21.378240] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   21.378245] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X0000006c
[   21.378250] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   21.378255] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000001
[   21.378260] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00210801
[   21.378265] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[   21.378270] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   21.378275] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   21.378280] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   21.378285] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   21.378290] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[   21.378294] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   21.378299] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   21.378304] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   21.378309] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   21.378314] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   21.378316] iwlagn 0000:02:00.0: FH register values:
[   21.378330] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X12707b00
[   21.378343] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0124d160
[   21.378356] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   21.378369] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   21.378382] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   21.378396] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   21.378408] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   21.378421] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   21.378434] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   21.378485] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 5 entries
[   21.378503] iwlagn 0000:02:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   21.378513] iwlagn 0000:02:00.0: EVT_LOGT:0000000022:0x00000000:1208
[   21.378524] iwlagn 0000:02:00.0: EVT_LOGT:0000001004:0x00000001:0071
[   21.378534] iwlagn 0000:02:00.0: EVT_LOGT:0000001080:0x00000002:0071
[   21.378545] iwlagn 0000:02:00.0: EVT_LOGT:0000001086:0x00000000:0125
[   21.378814] iwlagn 0000:02:00.0: Failed to run INIT ucode: -5
[   21.378853] iwlagn 0000:02:00.0: Unable to initialize device.
[   21.396532] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   21.396539] iwlagn 0000:02:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   21.396612] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
[   21.396615] iwlagn 0000:02:00.0: Status: 0x00040224, count: 5
[   21.396618] iwlagn 0000:02:00.0: 0x00000005 | SYSASSERT                   
[   21.396620] iwlagn 0000:02:00.0: 0x00016E00 | uPc
[   21.396622] iwlagn 0000:02:00.0: 0x00016E00 | branchlink1
[   21.396625] iwlagn 0000:02:00.0: 0x00016E00 | branchlink2
[   21.396627] iwlagn 0000:02:00.0: 0x00000000 | interruptlink1
[   21.396629] iwlagn 0000:02:00.0: 0x00000000 | interruptlink2
[   21.396631] iwlagn 0000:02:00.0: 0x00000000 | data1
[   21.396633] iwlagn 0000:02:00.0: 0x00000000 | data2
[   21.396635] iwlagn 0000:02:00.0: 0x00000616 | line
[   21.396637] iwlagn 0000:02:00.0: 0x00018BCA | beacon time
[   21.396639] iwlagn 0000:02:00.0: 0x00000436 | tsf low
[   21.396641] iwlagn 0000:02:00.0: 0x00000000 | tsf hi
[   21.396643] iwlagn 0000:02:00.0: 0x00000000 | time gp1
[   21.396646] iwlagn 0000:02:00.0: 0x0000043A | time gp2
[   21.396648] iwlagn 0000:02:00.0: 0x00000000 | time gp3
[   21.396650] iwlagn 0000:02:00.0: 0x0001271F | uCode version
[   21.396652] iwlagn 0000:02:00.0: 0x0000006C | hw version
[   21.396654] iwlagn 0000:02:00.0: 0x00C80300 | board version
[   21.396657] iwlagn 0000:02:00.0: 0x00000000 | hcmd
[   21.396659] iwlagn 0000:02:00.0: CSR values:
[   21.396661] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   21.396667] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   21.396672] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[   21.396677] iwlagn 0000:02:00.0:                     CSR_INT: 0X80000000
[   21.396681] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   21.396687] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   21.396692] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X00000000
[   21.396697] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
[   21.396702] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   21.396707] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X0000006c
[   21.396712] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   21.396717] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000001
[   21.396722] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00210801
[   21.396727] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[   21.396732] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   21.396737] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   21.396742] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   21.396747] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   21.396751] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[   21.396756] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   21.396761] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   21.396766] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   21.396771] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   21.396776] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   21.396779] iwlagn 0000:02:00.0: FH register values:
[   21.396792] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X12707b00
[   21.396806] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0124d160
[   21.396819] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   21.396832] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   21.396846] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   21.396859] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   21.396872] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   21.396885] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   21.396897] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   21.396947] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 5 entries
[   21.396966] iwlagn 0000:02:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   21.396977] iwlagn 0000:02:00.0: EVT_LOGT:0000000021:0x00000000:1208
[   21.396987] iwlagn 0000:02:00.0: EVT_LOGT:0000001003:0x00000001:0071
[   21.396998] iwlagn 0000:02:00.0: EVT_LOGT:0000001079:0x00000002:0071
[   21.397008] iwlagn 0000:02:00.0: EVT_LOGT:0000001085:0x00000000:0125
[   21.397279] iwlagn 0000:02:00.0: Failed to run INIT ucode: -5
[   21.397317] iwlagn 0000:02:00.0: Unable to initialize device.


[CODE] iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by josephmills on 2012-02-18
try ```
sudo rmmod hp_wmi && sudo modprobe iwlang
``` 
wireless ?

---

### Post by praseodym on 2012-02-18
Hi,

try to deactivate the power management and the N-mode of the driver iwlagn (buggy in 11.10):

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
sudo iwconfig wlan0 power off
```

---

### Post by jgraham5481 on 2012-02-18
> **josephmills said:**
> try ```
sudo rmmod hp_wmi && sudo modprobe iwlang
```wireless ?


tried this and it returned:
Module iwlang not found.

---

### Post by jgraham5481 on 2012-02-18
> **praseodym said:**
> Hi,

try to deactivate the power management and the N-mode of the driver iwlagn (buggy in 11.10):

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
sudo iwconfig wlan0 power off
```

Tired, and this is what it returned:
james@james-HP-G71-Notebook-PC:~$ echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
options iwlagn 11n_disable=1
james@james-HP-G71-Notebook-PC:~$ sudo modprobe -rfv iwlang
FATAL: Module iwlang not found.
james@james-HP-G71-Notebook-PC:~$ sudo modprobe -v iwlang
FATAL: Module iwlang not found.
james@james-HP-G71-Notebook-PC:~$ sudo iwconfig wlan0 power off
james@james-HP-G71-Notebook-PC:~$ 


I think my issue may lie with that iwlang module, what is that?

---

### Post by wildmanne39 on 2012-02-18
Hi, there is a typo this iwlang should be iwlagn so rerun the command by praseodym using iwlagn.
Thanks

---

### Post by jgraham5481 on 2012-02-18
Ok, I tried these with the proper spelling "agn" and heres what I got, still the same, but I will restart and see what I get. I do appreciate all the help!

sudo rmmod hp_wmi && sudo modprobe iwlagn
[sudo] password for james: 
james@james-HP-G71-Notebook-PC:~$ echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
options iwlagn 11n_disable=1
james@james-HP-G71-Notebook-PC:~$ sudo modprobe -rfv iwlagn
rmmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
rmmod /lib/modules/3.0.0-16-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.0.0-16-generic/kernel/net/wireless/cfg80211.ko
james@james-HP-G71-Notebook-PC:~$ sudo modprobe -v iwlagn
insmod /lib/modules/3.0.0-16-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 11n_disable=1
james@james-HP-G71-Notebook-PC:~$ sudo iwconfig wlan0 power off
james@james-HP-G71-Notebook-PC:~$

---

