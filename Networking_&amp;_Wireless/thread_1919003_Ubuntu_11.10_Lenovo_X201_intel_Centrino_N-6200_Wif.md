---
title: "Ubuntu 11.10 Lenovo X201 intel Centrino N-6200 Wifi problem"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by dvorim4 on 2012-02-02
Hello,
I'm a beginer with linux and I have a problem with my wifi card. I think system can find it but can't turn it on. I tried to find something on the internet but without success.

Thanks for any help.

Here are some results of commands. 

dvorakm@dvorakmntb:~$ lspci | grep -i net
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

dvorakm@dvorakmntb:~$ sudo iwconfig wlan0
[sudo] password for dvorakm: 
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

dvorakm@dvorakmntb:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Chyba vstupu/výstupu

   (SIOCSIFFLAGS: Input output error)

dvorakm@dvorakmntb:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: tpacpi_wwan_sw: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2012-02-02
Let's have a look at a few more items. Please open a terminal and run and post:```
sudo iwlist wlan0 scan
dmesg | grep -e wlan -e iwlagn
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by dvorim4 on 2012-02-02
Thank you very much for your interest.

Here are the results
The result of second command is cutted when the log starts repeating but it is full in the atachement.

dvorakm@dvorakmntb:~$ sudo iwlist wlan0 scan
[sudo] password for dvorakm: 
wlan0     Interface doesn't support scanning : Network is down

dvorakm@dvorakmntb:~$ dmesg | grep -e wlan -e iwlagn
[   15.188694] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.188697] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   15.188776] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.188785] iwlagn 0000:02:00.0: setting latency timer to 64
[   15.188817] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   15.209209] iwlagn 0000:02:00.0: device EEPROM VER=0x436, CALIB=0x6
[   15.209213] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   15.209641] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.209768] iwlagn 0000:02:00.0: irq 41 for MSI/MSI-X
[   15.432056] iwlagn 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   17.008870] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   17.008879] iwlagn 0000:02:00.0: Loaded firmware version: 9.221.4.1 build 25532
[   17.008885] iwlagn 0000:02:00.0: Not valid error log pointer 0x00000000 for Init uCode
[   17.008889] iwlagn 0000:02:00.0: CSR values:
[   17.008892] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   17.008900] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[   17.008906] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X00000040
[   17.008913] iwlagn 0000:02:00.0:                     CSR_INT: 0X80000000
[   17.008919] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   17.008925] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   17.008931] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X0000000f
[   17.008937] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
[   17.008944] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   17.008950] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X00000074
[   17.008956] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0X00000000
[   17.009028] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000004
[   17.009040] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00020000
[   17.009047] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080044
[   17.009054] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   17.009059] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000002
[   17.009063] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   17.009067] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   17.009071] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[   17.009077] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   17.009082] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   17.009085] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   17.009090] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   17.009093] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   17.009095] iwlagn 0000:02:00.0: FH register values:
[   17.009108] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X121f1500
[   17.009121] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X0122fc60
[   17.009135] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   17.009147] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   17.009160] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   17.009173] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   17.009186] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   17.009198] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   17.009211] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   17.009214] iwlagn 0000:02:00.0: Invalid event log pointer 0x00000000 for Init uCode
[   17.009544] iwlagn 0000:02:00.0: Failed to run INIT ucode: -5
[   17.009579] iwlagn 0000:02:00.0: Unable to initialize device.
[   17.050417] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x82000000.

---

### Post by chili555 on 2012-02-02
> [ 17.009544] iwlagn 0000:02:00.0: Failed to run INIT ucode: -5
[ 17.009579] iwlagn 0000:02:00.0: Unable to initialize device.
[ 17.050417] iwlagn 0000:02:00.0: Microcode SW error detected. Restarting 0x82000000.I wonder if we've seen this before...hmmm...YES!

Please see here: [https://bbs.archlinux.org/viewtopic.php?id=125486](https://bbs.archlinux.org/viewtopic.php?id=125486) and here: [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2314](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2314)

In this case, the person loaded an older version of the firmware (microcode) and says:> the wireless is ok with the older uCode Let's see if we can try the same approach. Please go here: [http://intellinuxwireless.org/?n=downloads&f=ucodes_6000](http://intellinuxwireless.org/?n=downloads&f=ucodes_6000)

As you can see, the latest version is 9.221.4.1. That's what you have and what was loaded according to your dmesg:> [ 15.432056] iwlagn 0000:02:00.0: loaded firmware version [COLOR="Red"]9.221.4.1[/COLOR] build 25532Please download the previous version 9.193.4.1 to your desktop. Right-click it and select Extract Here. Now open a terminal and we back up your current ucode:```
sudo mv /lib/firmware/iwlwifi-6000-4.ucode /lib/firmware/iwlwifi-6000-4.ucode.bak
```Now we copy the earlier ucode from your desktop to /lib/firmware:```
sudo cp Desktop/iwlwifi-6000-ucode-9.193.4.1/iwlwifi-6000-4.ucode /lib/firmware
```Now reboot and let us see again:```
dmesg | grep -e wlan -e iwlagn
```

---

### Post by dvorim4 on 2012-02-02
I looked at the links you posted and saw that they had similar problem and intel card too.
So I tried both of older firmware from intel site but that bug is still there (and the truth is out there :))
Do you have any other idea?
Now I have 9.176.4.1 firmware in my laptop.

In attached files is log of dmesg | grep -e wlan -e iwlagn for each firmware

---

