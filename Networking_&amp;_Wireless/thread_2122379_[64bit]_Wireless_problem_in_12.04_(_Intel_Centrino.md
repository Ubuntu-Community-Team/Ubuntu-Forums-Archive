---
title: "[64bit] Wireless problem in 12.04 ( Intel Centrino Wireless-N 1000 )"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by 67kyj on 2013-03-05
I have a fresh installation on my Lenovo laptop Y470, which has a Intel Centrino Wireless-N 1000 network controller.
Now the problem is that I can't access my wifi router under ubuntu, but it's ok under win7.

First I'm very sure that both my hardware switch and soft switch are on. Below is output from ' rfkill list all'
```
nico@jacob-pc:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
nico@jacob-pc:~$ 

```

Then I want to paste my output from these command ' lspci -nn | grep Wireless',
```

nico@jacob-pc:~$ lspci -nn | grep Wireless
08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
nico@jacob-pc:~$ 

```

Output from ' iwconfig' and ' ifconfig'
```

nico@jacob-pc:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
nico@jacob-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:30:b7:1d  
          inet addr:192.168.211.230  Bcast:192.168.211.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe30:b71d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4641286 (4.6 MB)  TX bytes:463510 (463.5 KB)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78153 (78.1 KB)  TX bytes:78153 (78.1 KB)


nico@jacob-pc:~$ 


```

When I use a command ' iwlist  scan ', it gives me this
```

nico@jacob-pc:~$ iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Failed to read scan data : Network is down


nico@jacob-pc:~$

```

and ' sudo ifup wlan0'
```

nico@jacob-pc:~$ sudo ifup wlan0
[sudo] password for nico: 
Ignoring unknown interface wlan0=wlan0.
nico@jacob-pc:~$ 

```

When I use ' sudo dhclient wlan0'
```

nico@jacob-pc:~$ sudo dhclient wlan0
RTNETLINK answers: Input/output error
^C

```
As you can see, I have to use Ctrl-C to terminate this command.

There are some outputs from these two command ' dmesg | grep wlan' and ' dmesg | grep iwl'.
```

nico@jacob-pc:~$ dmesg | grep wlan
[   18.997378] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2884.882201] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2896.589165] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
nico@jacob-pc:~$ dmesg | grep iwl
[   16.739907] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.739911] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   16.740040] iwlwifi 0000:08:00.0: pci_resource_len = 0x00002000
[   16.740042] iwlwifi 0000:08:00.0: pci_resource_base = ffffc900051b0000
[   16.740043] iwlwifi 0000:08:00.0: HW Revision ID = 0x0
[   16.740310] iwlwifi 0000:08:00.0: irq 44 for MSI/MSI-X
[   16.741750] iwlwifi 0000:08:00.0: loaded firmware version 39.31.5.1 build 35138
[   16.741857] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.741860] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.741863] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.741865] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   16.741867] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_P2P disabled
[   16.741870] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   16.742029] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   16.761591] iwlwifi 0000:08:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   16.761593] iwlwifi 0000:08:00.0: Device SKU: 0x50
[   16.761595] iwlwifi 0000:08:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[   16.761604] iwlwifi 0000:08:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   16.892705] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.980583] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   18.996197] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   18.996210] iwlwifi 0000:08:00.0: CSR values:
[   18.996216] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   18.996226] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   18.996236] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[   18.996245] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[   18.996254] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[   18.996262] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   18.996271] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[   18.996287] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[   18.996292] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[   18.996298] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[   18.996303] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   18.996308] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[   18.996313] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[   18.996318] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[   18.996323] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   18.996328] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   18.996333] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   18.996339] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   18.996344] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[   18.996349] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   18.996354] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   18.996359] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[   18.996364] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   18.996369] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   18.996370] iwlwifi 0000:08:00.0: FH register values:
[   18.996386] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X126a2c00
[   18.996401] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X012682e0
[   18.996417] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   18.996432] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[   18.996447] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   18.996461] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   18.996477] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   18.996493] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   18.996508] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   18.996510] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   18.996645] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[   18.996646] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[   18.996648] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[   18.996650] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[   18.996651] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[   18.996653] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[   18.996654] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[   18.996655] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[   18.996657] iwlwifi 0000:08:00.0: 0x00000000 | data1
[   18.996658] iwlwifi 0000:08:00.0: 0x00000000 | data2
[   18.996659] iwlwifi 0000:08:00.0: 0x00000616 | line
[   18.996661] iwlwifi 0000:08:00.0: 0x00018BCA | beacon time
[   18.996662] iwlwifi 0000:08:00.0: 0x00000436 | tsf low
[   18.996664] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[   18.996665] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[   18.996667] iwlwifi 0000:08:00.0: 0x0000043A | time gp2
[   18.996668] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[   18.996669] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[   18.996671] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[   18.996672] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[   18.996674] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[   18.996675] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[   18.996676] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[   18.996678] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[   18.996679] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[   18.996681] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[   18.996682] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[   18.996683] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[   18.996685] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[   18.996686] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[   18.996688] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[   18.996689] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[   18.996690] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[   18.996692] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[   18.996693] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[   18.996755] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[   18.996776] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   18.996789] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[   18.996801] iwlwifi 0000:08:00.0: EVT_LOGT:0000001003:0x00000001:0071
[   18.996812] iwlwifi 0000:08:00.0: EVT_LOGT:0000001079:0x00000002:0071
[   18.996825] iwlwifi 0000:08:00.0: EVT_LOGT:0000001085:0x00000000:0125
[   18.997177] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[   18.997273] iwlwifi 0000:08:00.0: Unable to initialize device.
[   19.002417] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   19.018032] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   19.018045] iwlwifi 0000:08:00.0: CSR values:
[   19.018050] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   19.018061] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   19.018070] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[   19.018078] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[   19.018087] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[   19.018096] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   19.018105] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[   19.018114] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[   19.018122] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[   19.018131] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[   19.018146] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   19.018151] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[   19.018156] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[   19.018161] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[   19.018166] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   19.018171] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   19.018176] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   19.018181] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   19.018186] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[   19.018190] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   19.018195] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   19.018199] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   19.018204] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   19.018209] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   19.018211] iwlwifi 0000:08:00.0: FH register values:
[   19.018227] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X126a2c00
[   19.018242] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X012682e0
[   19.018257] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   19.018272] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[   19.018287] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   19.018302] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   19.018318] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   19.018333] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   19.018347] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   19.018350] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   19.018484] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[   19.018485] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[   19.018487] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[   19.018488] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[   19.018490] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[   19.018491] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[   19.018492] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[   19.018493] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[   19.018495] iwlwifi 0000:08:00.0: 0x00000000 | data1
[   19.018496] iwlwifi 0000:08:00.0: 0x00000000 | data2
[   19.018497] iwlwifi 0000:08:00.0: 0x00000616 | line
[   19.018498] iwlwifi 0000:08:00.0: 0x00018BC9 | beacon time
[   19.018500] iwlwifi 0000:08:00.0: 0x00000437 | tsf low
[   19.018501] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[   19.018502] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[   19.018503] iwlwifi 0000:08:00.0: 0x0000043C | time gp2
[   19.018505] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[   19.018506] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[   19.018507] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[   19.018508] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[   19.018510] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[   19.018511] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[   19.018512] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[   19.018513] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[   19.018515] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[   19.018516] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[   19.018517] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[   19.018519] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[   19.018520] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[   19.018521] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[   19.018522] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[   19.018524] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[   19.018525] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[   19.018526] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[   19.018527] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[   19.018589] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[   19.018609] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   19.018620] iwlwifi 0000:08:00.0: EVT_LOGT:0000000022:0x00000000:1208
[   19.018632] iwlwifi 0000:08:00.0: EVT_LOGT:0000001005:0x00000001:0071
[   19.018644] iwlwifi 0000:08:00.0: EVT_LOGT:0000001081:0x00000002:0071
[   19.018656] iwlwifi 0000:08:00.0: EVT_LOGT:0000001087:0x00000000:0125
[   19.019005] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[   19.019106] iwlwifi 0000:08:00.0: Unable to initialize device.
[   19.104087] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[   19.125128] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[   19.125134] iwlwifi 0000:08:00.0: CSR values:
[   19.125137] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   19.125143] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[   19.125148] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[   19.125154] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[   19.125159] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[   19.125165] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[   19.125171] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[   19.125176] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[   19.125182] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[   19.125187] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[   19.125193] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[   19.125199] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[   19.125204] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[   19.125210] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[   19.125216] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[   19.125221] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   19.125227] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   19.125232] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   19.125238] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[   19.125244] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   19.125249] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   19.125254] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   19.125260] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   19.125265] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   19.125267] iwlwifi 0000:08:00.0: FH register values:
[   19.125283] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X126a2c00
[   19.125298] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X012682e0
[   19.125313] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[   19.125327] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[   19.125341] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   19.125356] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   19.125370] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   19.125385] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   19.125399] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   19.125403] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[   19.125524] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[   19.125527] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[   19.125530] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[   19.125532] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[   19.125535] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[   19.125537] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[   19.125539] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[   19.125541] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[   19.125544] iwlwifi 0000:08:00.0: 0x00000000 | data1
[   19.125546] iwlwifi 0000:08:00.0: 0x00000000 | data2
[   19.125549] iwlwifi 0000:08:00.0: 0x00000616 | line
[   19.125551] iwlwifi 0000:08:00.0: 0x00018BC8 | beacon time
[   19.125553] iwlwifi 0000:08:00.0: 0x00000438 | tsf low
[   19.125556] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[   19.125558] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[   19.125560] iwlwifi 0000:08:00.0: 0x0000043C | time gp2
[   19.125562] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[   19.125564] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[   19.125567] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[   19.125569] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[   19.125571] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[   19.125574] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[   19.125576] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[   19.125578] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[   19.125580] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[   19.125582] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[   19.125585] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[   19.125587] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[   19.125590] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[   19.125592] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[   19.125594] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[   19.125596] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[   19.125598] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[   19.125600] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[   19.125602] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[   19.125660] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[   19.125680] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[   19.125692] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[   19.125704] iwlwifi 0000:08:00.0: EVT_LOGT:0000001005:0x00000001:0071
[   19.125716] iwlwifi 0000:08:00.0: EVT_LOGT:0000001081:0x00000002:0071
[   19.125727] iwlwifi 0000:08:00.0: EVT_LOGT:0000001087:0x00000000:0125
[   19.126048] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[   19.126139] iwlwifi 0000:08:00.0: Unable to initialize device.
[ 2884.832304] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2884.832307] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[ 2884.832456] iwlwifi 0000:08:00.0: pci_resource_len = 0x00002000
[ 2884.832459] iwlwifi 0000:08:00.0: pci_resource_base = ffffc900051b0000
[ 2884.832462] iwlwifi 0000:08:00.0: HW Revision ID = 0x0
[ 2884.832747] iwlwifi 0000:08:00.0: irq 44 for MSI/MSI-X
[ 2884.836182] iwlwifi 0000:08:00.0: loaded firmware version 39.31.5.1 build 35138
[ 2884.836314] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2884.836316] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2884.836318] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2884.836320] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[ 2884.836322] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_P2P disabled
[ 2884.836325] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[ 2884.836449] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 2884.855920] iwlwifi 0000:08:00.0: device EEPROM VER=0x15d, CALIB=0x6
[ 2884.855922] iwlwifi 0000:08:00.0: Device SKU: 0x50
[ 2884.855923] iwlwifi 0000:08:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[ 2884.855932] iwlwifi 0000:08:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[ 2884.856127] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2884.865376] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 2884.881164] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 2884.881168] iwlwifi 0000:08:00.0: CSR values:
[ 2884.881170] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 2884.881174] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 2884.881179] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[ 2884.881184] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[ 2884.881189] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 2884.881193] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 2884.881198] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[ 2884.881203] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 2884.881207] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 2884.881212] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[ 2884.881216] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 2884.881221] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[ 2884.881226] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 2884.881230] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[ 2884.881235] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 2884.881239] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 2884.881244] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 2884.881248] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 2884.881253] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[ 2884.881257] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 2884.881262] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 2884.881266] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[ 2884.881271] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 2884.881276] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 2884.881277] iwlwifi 0000:08:00.0: FH register values:
[ 2884.881290] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X10f2a400
[ 2884.881305] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01136ad0
[ 2884.881318] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 2884.881331] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[ 2884.881344] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 2884.881357] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 2884.881370] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 2884.881383] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 2884.881396] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 2884.881398] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 2884.881517] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 2884.881518] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[ 2884.881520] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[ 2884.881522] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[ 2884.881523] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[ 2884.881525] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[ 2884.881526] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[ 2884.881527] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[ 2884.881529] iwlwifi 0000:08:00.0: 0x00000000 | data1
[ 2884.881530] iwlwifi 0000:08:00.0: 0x00000000 | data2
[ 2884.881531] iwlwifi 0000:08:00.0: 0x00000616 | line
[ 2884.881533] iwlwifi 0000:08:00.0: 0x00018BC9 | beacon time
[ 2884.881534] iwlwifi 0000:08:00.0: 0x00000437 | tsf low
[ 2884.881535] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[ 2884.881537] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 2884.881538] iwlwifi 0000:08:00.0: 0x0000043B | time gp2
[ 2884.881539] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 2884.881541] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[ 2884.881542] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[ 2884.881543] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[ 2884.881545] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[ 2884.881546] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[ 2884.881548] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[ 2884.881549] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[ 2884.881550] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[ 2884.881552] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 2884.881553] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[ 2884.881554] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[ 2884.881556] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[ 2884.881557] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[ 2884.881558] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[ 2884.881560] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[ 2884.881561] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[ 2884.881562] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[ 2884.881564] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[ 2884.881618] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[ 2884.881636] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 2884.881647] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 2884.881657] iwlwifi 0000:08:00.0: EVT_LOGT:0000001004:0x00000001:0071
[ 2884.881668] iwlwifi 0000:08:00.0: EVT_LOGT:0000001080:0x00000002:0071
[ 2884.881679] iwlwifi 0000:08:00.0: EVT_LOGT:0000001086:0x00000000:0125
[ 2884.882000] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[ 2884.882093] iwlwifi 0000:08:00.0: Unable to initialize device.
[ 2884.883217] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 2884.898504] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 2884.898510] iwlwifi 0000:08:00.0: CSR values:
[ 2884.898513] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 2884.898519] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 2884.898525] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[ 2884.898531] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[ 2884.898537] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 2884.898543] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 2884.898549] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[ 2884.898554] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 2884.898559] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 2884.898565] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[ 2884.898571] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 2884.898576] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[ 2884.898582] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 2884.898587] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[ 2884.898593] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 2884.898599] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 2884.898604] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 2884.898610] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 2884.898616] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[ 2884.898622] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 2884.898628] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 2884.898634] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 2884.898639] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 2884.898645] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 2884.898648] iwlwifi 0000:08:00.0: FH register values:
[ 2884.898663] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X10f2a400
[ 2884.898679] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01136ad0
[ 2884.898693] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 2884.898707] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[ 2884.898721] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 2884.898734] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 2884.898747] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 2884.898760] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 2884.898773] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 2884.898775] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 2884.898894] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 2884.898895] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[ 2884.898897] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[ 2884.898899] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[ 2884.898900] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[ 2884.898902] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[ 2884.898903] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[ 2884.898904] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[ 2884.898906] iwlwifi 0000:08:00.0: 0x00000000 | data1
[ 2884.898907] iwlwifi 0000:08:00.0: 0x00000000 | data2
[ 2884.898908] iwlwifi 0000:08:00.0: 0x00000616 | line
[ 2884.898910] iwlwifi 0000:08:00.0: 0x00018BCB | beacon time
[ 2884.898911] iwlwifi 0000:08:00.0: 0x00000435 | tsf low
[ 2884.898912] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[ 2884.898914] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 2884.898915] iwlwifi 0000:08:00.0: 0x00000439 | time gp2
[ 2884.898916] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 2884.898918] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[ 2884.898919] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[ 2884.898921] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[ 2884.898922] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[ 2884.898923] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[ 2884.898925] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[ 2884.898926] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[ 2884.898927] iwlwifi 0000:08:00.0: 0x004400C0 | isr3
[ 2884.898929] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 2884.898930] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[ 2884.898931] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[ 2884.898933] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[ 2884.898934] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[ 2884.898935] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[ 2884.898937] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[ 2884.898938] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[ 2884.898940] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[ 2884.898941] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[ 2884.898995] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[ 2884.899013] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 2884.899024] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 2884.899034] iwlwifi 0000:08:00.0: EVT_LOGT:0000001002:0x00000001:0071
[ 2884.899045] iwlwifi 0000:08:00.0: EVT_LOGT:0000001078:0x00000002:0071
[ 2884.899057] iwlwifi 0000:08:00.0: EVT_LOGT:0000001084:0x00000000:0125
[ 2884.899365] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[ 2884.899443] iwlwifi 0000:08:00.0: Unable to initialize device.
[ 2884.899707] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 2884.914933] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 2884.914937] iwlwifi 0000:08:00.0: CSR values:
[ 2884.914939] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 2884.914944] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 2884.914948] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[ 2884.914953] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[ 2884.914958] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 2884.914962] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 2884.914967] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[ 2884.914971] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 2884.914976] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 2884.914981] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[ 2884.914985] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 2884.914989] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[ 2884.914994] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 2884.914999] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[ 2884.915003] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 2884.915008] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 2884.915012] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 2884.915017] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 2884.915021] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[ 2884.915026] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 2884.915030] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 2884.915035] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 2884.915040] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 2884.915044] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 2884.915046] iwlwifi 0000:08:00.0: FH register values:
[ 2884.915060] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X10f2a400
[ 2884.915073] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01136ad0
[ 2884.915087] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 2884.915100] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[ 2884.915113] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 2884.915126] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 2884.915139] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 2884.915152] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 2884.915166] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 2884.915168] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 2884.915285] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 2884.915286] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[ 2884.915288] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[ 2884.915290] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[ 2884.915291] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[ 2884.915293] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[ 2884.915294] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[ 2884.915295] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[ 2884.915296] iwlwifi 0000:08:00.0: 0x00000000 | data1
[ 2884.915298] iwlwifi 0000:08:00.0: 0x00000000 | data2
[ 2884.915299] iwlwifi 0000:08:00.0: 0x00000616 | line
[ 2884.915301] iwlwifi 0000:08:00.0: 0x00018BCB | beacon time
[ 2884.915302] iwlwifi 0000:08:00.0: 0x00000435 | tsf low
[ 2884.915303] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[ 2884.915304] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 2884.915306] iwlwifi 0000:08:00.0: 0x00000439 | time gp2
[ 2884.915307] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 2884.915308] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[ 2884.915310] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[ 2884.915311] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[ 2884.915313] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[ 2884.915314] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[ 2884.915315] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[ 2884.915317] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[ 2884.915318] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[ 2884.915319] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 2884.915321] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[ 2884.915322] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[ 2884.915323] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[ 2884.915325] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[ 2884.915326] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[ 2884.915328] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[ 2884.915329] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[ 2884.915330] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[ 2884.915332] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[ 2884.915385] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[ 2884.915403] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 2884.915414] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 2884.915425] iwlwifi 0000:08:00.0: EVT_LOGT:0000001002:0x00000001:0071
[ 2884.915435] iwlwifi 0000:08:00.0: EVT_LOGT:0000001078:0x00000002:0071
[ 2884.915446] iwlwifi 0000:08:00.0: EVT_LOGT:0000001084:0x00000000:0125
[ 2884.915741] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[ 2884.915840] iwlwifi 0000:08:00.0: Unable to initialize device.
[ 2896.536035] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2896.536038] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[ 2896.536180] iwlwifi 0000:08:00.0: pci_resource_len = 0x00002000
[ 2896.536182] iwlwifi 0000:08:00.0: pci_resource_base = ffffc900051b0000
[ 2896.536184] iwlwifi 0000:08:00.0: HW Revision ID = 0x0
[ 2896.536444] iwlwifi 0000:08:00.0: irq 44 for MSI/MSI-X
[ 2896.540422] iwlwifi 0000:08:00.0: loaded firmware version 39.31.5.1 build 35138
[ 2896.540548] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 2896.540551] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 2896.540553] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 2896.540555] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[ 2896.540557] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_P2P disabled
[ 2896.540560] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[ 2896.540712] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 2896.560235] iwlwifi 0000:08:00.0: device EEPROM VER=0x15d, CALIB=0x6
[ 2896.560237] iwlwifi 0000:08:00.0: Device SKU: 0x50
[ 2896.560239] iwlwifi 0000:08:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[ 2896.560246] iwlwifi 0000:08:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[ 2896.560436] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2896.571964] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 2896.588094] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 2896.588107] iwlwifi 0000:08:00.0: CSR values:
[ 2896.588113] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 2896.588123] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 2896.588131] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[ 2896.588140] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[ 2896.588148] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 2896.588157] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 2896.588165] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[ 2896.588173] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 2896.588181] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 2896.588189] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[ 2896.588204] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 2896.588208] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[ 2896.588213] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 2896.588218] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[ 2896.588222] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 2896.588227] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 2896.588231] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 2896.588236] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 2896.588240] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[ 2896.588245] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 2896.588249] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 2896.588254] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00880300
[ 2896.588258] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 2896.588263] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 2896.588265] iwlwifi 0000:08:00.0: FH register values:
[ 2896.588278] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X108a3200
[ 2896.588291] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X010f2ea0
[ 2896.588305] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 2896.588318] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[ 2896.588331] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 2896.588345] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 2896.588358] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 2896.588371] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 2896.588385] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 2896.588387] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 2896.588505] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 2896.588506] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[ 2896.588508] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[ 2896.588510] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[ 2896.588511] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[ 2896.588513] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[ 2896.588514] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[ 2896.588515] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[ 2896.588517] iwlwifi 0000:08:00.0: 0x00000000 | data1
[ 2896.588518] iwlwifi 0000:08:00.0: 0x00000000 | data2
[ 2896.588519] iwlwifi 0000:08:00.0: 0x00000616 | line
[ 2896.588521] iwlwifi 0000:08:00.0: 0x00018BCB | beacon time
[ 2896.588522] iwlwifi 0000:08:00.0: 0x00000435 | tsf low
[ 2896.588524] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[ 2896.588525] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 2896.588526] iwlwifi 0000:08:00.0: 0x00000439 | time gp2
[ 2896.588528] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 2896.588529] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[ 2896.588530] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[ 2896.588532] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[ 2896.588533] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[ 2896.588534] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[ 2896.588536] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[ 2896.588537] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[ 2896.588538] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[ 2896.588540] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 2896.588541] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[ 2896.588542] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[ 2896.588544] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[ 2896.588545] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[ 2896.588547] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[ 2896.588548] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[ 2896.588549] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[ 2896.588551] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[ 2896.588552] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[ 2896.588607] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[ 2896.588625] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 2896.588636] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 2896.588646] iwlwifi 0000:08:00.0: EVT_LOGT:0000001002:0x00000001:0071
[ 2896.588657] iwlwifi 0000:08:00.0: EVT_LOGT:0000001078:0x00000002:0071
[ 2896.588667] iwlwifi 0000:08:00.0: EVT_LOGT:0000001084:0x00000000:0125
[ 2896.588968] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[ 2896.589047] iwlwifi 0000:08:00.0: Unable to initialize device.
[ 2896.590231] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 2896.605450] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 2896.605455] iwlwifi 0000:08:00.0: CSR values:
[ 2896.605458] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 2896.605464] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 2896.605470] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[ 2896.605476] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[ 2896.605482] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 2896.605487] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 2896.605493] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[ 2896.605498] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 2896.605504] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 2896.605510] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[ 2896.605516] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 2896.605522] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[ 2896.605528] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 2896.605534] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[ 2896.605540] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 2896.605546] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 2896.605551] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 2896.605557] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 2896.605562] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[ 2896.605568] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 2896.605573] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 2896.605578] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 2896.605585] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 2896.605590] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 2896.605593] iwlwifi 0000:08:00.0: FH register values:
[ 2896.605610] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X108a3200
[ 2896.605625] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X010f2ea0
[ 2896.605641] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 2896.605657] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[ 2896.605674] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 2896.605690] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 2896.605706] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 2896.605721] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 2896.605736] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 2896.605739] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 2896.605874] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 2896.605877] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[ 2896.605880] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[ 2896.605883] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[ 2896.605885] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[ 2896.605888] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[ 2896.605890] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[ 2896.605893] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[ 2896.605895] iwlwifi 0000:08:00.0: 0x00000000 | data1
[ 2896.605897] iwlwifi 0000:08:00.0: 0x00000000 | data2
[ 2896.605899] iwlwifi 0000:08:00.0: 0x00000616 | line
[ 2896.605902] iwlwifi 0000:08:00.0: 0x00018BCB | beacon time
[ 2896.605904] iwlwifi 0000:08:00.0: 0x00000435 | tsf low
[ 2896.605906] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[ 2896.605909] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 2896.605911] iwlwifi 0000:08:00.0: 0x00000439 | time gp2
[ 2896.605914] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 2896.605916] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[ 2896.605919] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[ 2896.605921] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[ 2896.605924] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[ 2896.605926] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[ 2896.605929] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[ 2896.605931] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[ 2896.605934] iwlwifi 0000:08:00.0: 0x004400C0 | isr3
[ 2896.605936] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 2896.605938] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[ 2896.605941] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[ 2896.605943] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[ 2896.605945] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[ 2896.605948] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[ 2896.605950] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[ 2896.605952] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[ 2896.605955] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[ 2896.605957] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[ 2896.606015] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[ 2896.606035] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 2896.606048] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 2896.606060] iwlwifi 0000:08:00.0: EVT_LOGT:0000001002:0x00000001:0071
[ 2896.606072] iwlwifi 0000:08:00.0: EVT_LOGT:0000001078:0x00000002:0071
[ 2896.606085] iwlwifi 0000:08:00.0: EVT_LOGT:0000001084:0x00000000:0125
[ 2896.606785] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[ 2896.606887] iwlwifi 0000:08:00.0: Unable to initialize device.
[ 2896.607138] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 2896.622461] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 2896.622473] iwlwifi 0000:08:00.0: CSR values:
[ 2896.622479] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 2896.622489] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 2896.622498] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[ 2896.622506] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[ 2896.622514] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 2896.622523] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 2896.622531] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[ 2896.622546] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 2896.622550] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 2896.622555] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[ 2896.622560] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 2896.622564] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[ 2896.622569] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 2896.622573] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[ 2896.622577] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 2896.622581] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 2896.622586] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 2896.622590] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 2896.622595] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[ 2896.622599] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 2896.622603] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 2896.622608] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 2896.622612] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 2896.622616] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 2896.622618] iwlwifi 0000:08:00.0: FH register values:
[ 2896.622631] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X108a3200
[ 2896.622645] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X010f2ea0
[ 2896.622658] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 2896.622671] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[ 2896.622684] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 2896.622698] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 2896.622711] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 2896.622724] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 2896.622737] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 2896.622739] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 2896.622857] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 2896.622858] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[ 2896.622860] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[ 2896.622861] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[ 2896.622863] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[ 2896.622864] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[ 2896.622865] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[ 2896.622866] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[ 2896.622868] iwlwifi 0000:08:00.0: 0x00000000 | data1
[ 2896.622869] iwlwifi 0000:08:00.0: 0x00000000 | data2
[ 2896.622870] iwlwifi 0000:08:00.0: 0x00000616 | line
[ 2896.622871] iwlwifi 0000:08:00.0: 0x00018BCC | beacon time
[ 2896.622873] iwlwifi 0000:08:00.0: 0x00000434 | tsf low
[ 2896.622874] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[ 2896.622875] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 2896.622876] iwlwifi 0000:08:00.0: 0x00000438 | time gp2
[ 2896.622878] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 2896.622879] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[ 2896.622880] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[ 2896.622881] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[ 2896.622883] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[ 2896.622884] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[ 2896.622885] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[ 2896.622887] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[ 2896.622888] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[ 2896.622889] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 2896.622890] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[ 2896.622892] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[ 2896.622893] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[ 2896.622894] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[ 2896.622895] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[ 2896.622897] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[ 2896.622898] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[ 2896.622899] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[ 2896.622901] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[ 2896.622954] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[ 2896.622972] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 2896.622983] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 2896.622993] iwlwifi 0000:08:00.0: EVT_LOGT:0000001001:0x00000001:0071
[ 2896.623003] iwlwifi 0000:08:00.0: EVT_LOGT:0000001077:0x00000002:0071
[ 2896.623014] iwlwifi 0000:08:00.0: EVT_LOGT:0000001083:0x00000000:0125
[ 2896.623319] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[ 2896.623397] iwlwifi 0000:08:00.0: Unable to initialize device.
[ 4436.388508] iwlwifi 0000:08:00.0: L1 Enabled; Disabling L0S
[ 4436.404554] iwlwifi 0000:08:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 4436.404567] iwlwifi 0000:08:00.0: CSR values:
[ 4436.404573] iwlwifi 0000:08:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 4436.404583] iwlwifi 0000:08:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c80300
[ 4436.404591] iwlwifi 0000:08:00.0:          CSR_INT_COALESCING: 0X00000040
[ 4436.404600] iwlwifi 0000:08:00.0:                     CSR_INT: 0X80000000
[ 4436.404608] iwlwifi 0000:08:00.0:                CSR_INT_MASK: 0X00000000
[ 4436.404616] iwlwifi 0000:08:00.0:           CSR_FH_INT_STATUS: 0X40010000
[ 4436.404625] iwlwifi 0000:08:00.0:                 CSR_GPIO_IN: 0X00000000
[ 4436.404633] iwlwifi 0000:08:00.0:                   CSR_RESET: 0X00000000
[ 4436.404641] iwlwifi 0000:08:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 4436.404650] iwlwifi 0000:08:00.0:                  CSR_HW_REV: 0X0000006c
[ 4436.404658] iwlwifi 0000:08:00.0:              CSR_EEPROM_REG: 0Xc63f3885
[ 4436.404666] iwlwifi 0000:08:00.0:               CSR_EEPROM_GP: 0X90000001
[ 4436.404675] iwlwifi 0000:08:00.0:              CSR_OTP_GP_REG: 0X00210801
[ 4436.404683] iwlwifi 0000:08:00.0:                 CSR_GIO_REG: 0X00080046
[ 4436.404692] iwlwifi 0000:08:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 4436.404700] iwlwifi 0000:08:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 4436.404708] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 4436.404716] iwlwifi 0000:08:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 4436.404724] iwlwifi 0000:08:00.0:                 CSR_LED_REG: 0X00000018
[ 4436.404732] iwlwifi 0000:08:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[ 4436.404740] iwlwifi 0000:08:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 4436.404748] iwlwifi 0000:08:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 4436.404756] iwlwifi 0000:08:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 4436.404764] iwlwifi 0000:08:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 4436.404769] iwlwifi 0000:08:00.0: FH register values:
[ 4436.404788] iwlwifi 0000:08:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X108a3200
[ 4436.404808] iwlwifi 0000:08:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X010f2ea0
[ 4436.404825] iwlwifi 0000:08:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000f8
[ 4436.404844] iwlwifi 0000:08:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80811104
[ 4436.404863] iwlwifi 0000:08:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 4436.404883] iwlwifi 0000:08:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 4436.404902] iwlwifi 0000:08:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 4436.404921] iwlwifi 0000:08:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 4436.404940] iwlwifi 0000:08:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 4436.404946] iwlwifi 0000:08:00.0: Loaded firmware version: 39.31.5.1 build 35138
[ 4436.405083] iwlwifi 0000:08:00.0: Start IWL Error Log Dump:
[ 4436.405088] iwlwifi 0000:08:00.0: Status: 0x00000010, count: 5
[ 4436.405094] iwlwifi 0000:08:00.0: 0x00000005 | SYSASSERT                   
[ 4436.405099] iwlwifi 0000:08:00.0: 0x00016E00 | uPc
[ 4436.405104] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink1
[ 4436.405109] iwlwifi 0000:08:00.0: 0x00016E00 | branchlink2
[ 4436.405113] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink1
[ 4436.405117] iwlwifi 0000:08:00.0: 0x00000000 | interruptlink2
[ 4436.405122] iwlwifi 0000:08:00.0: 0x00000000 | data1
[ 4436.405126] iwlwifi 0000:08:00.0: 0x00000000 | data2
[ 4436.405131] iwlwifi 0000:08:00.0: 0x00000616 | line
[ 4436.405136] iwlwifi 0000:08:00.0: 0x00018BCB | beacon time
[ 4436.405140] iwlwifi 0000:08:00.0: 0x00000435 | tsf low
[ 4436.405145] iwlwifi 0000:08:00.0: 0x00000000 | tsf hi
[ 4436.405149] iwlwifi 0000:08:00.0: 0x00000000 | time gp1
[ 4436.405154] iwlwifi 0000:08:00.0: 0x00000439 | time gp2
[ 4436.405158] iwlwifi 0000:08:00.0: 0x00000000 | time gp3
[ 4436.405162] iwlwifi 0000:08:00.0: 0x0001271F | uCode version
[ 4436.405167] iwlwifi 0000:08:00.0: 0x0000006C | hw version
[ 4436.405172] iwlwifi 0000:08:00.0: 0x00C80300 | board version
[ 4436.405176] iwlwifi 0000:08:00.0: 0x00000000 | hcmd
[ 4436.405181] iwlwifi 0000:08:00.0: 0x00122000 | isr0
[ 4436.405186] iwlwifi 0000:08:00.0: 0x00000000 | isr1
[ 4436.405190] iwlwifi 0000:08:00.0: 0x00000002 | isr2
[ 4436.405195] iwlwifi 0000:08:00.0: 0x004000C0 | isr3
[ 4436.405199] iwlwifi 0000:08:00.0: 0x00000000 | isr4
[ 4436.405204] iwlwifi 0000:08:00.0: 0x00000000 | isr_pref
[ 4436.405208] iwlwifi 0000:08:00.0: 0x00002BFE | wait_event
[ 4436.405213] iwlwifi 0000:08:00.0: 0x00000000 | l2p_control
[ 4436.405218] iwlwifi 0000:08:00.0: 0x00000000 | l2p_duration
[ 4436.405222] iwlwifi 0000:08:00.0: 0x00000000 | l2p_mhvalid
[ 4436.405227] iwlwifi 0000:08:00.0: 0x00100040 | l2p_addr_match
[ 4436.405231] iwlwifi 0000:08:00.0: 0x00000007 | lmpm_pmg_sel
[ 4436.405236] iwlwifi 0000:08:00.0: 0x00000000 | timestamp
[ 4436.405241] iwlwifi 0000:08:00.0: 0x0000F808 | flow_handler
[ 4436.405308] iwlwifi 0000:08:00.0: Start IWL Event Log Dump: display last 5 entries
[ 4436.405334] iwlwifi 0000:08:00.0: EVT_LOGT:0000000000:0x0000028c:0117
[ 4436.405350] iwlwifi 0000:08:00.0: EVT_LOGT:0000000021:0x00000000:1208
[ 4436.405364] iwlwifi 0000:08:00.0: EVT_LOGT:0000001002:0x00000001:0071
[ 4436.405379] iwlwifi 0000:08:00.0: EVT_LOGT:0000001078:0x00000002:0071
[ 4436.405394] iwlwifi 0000:08:00.0: EVT_LOGT:0000001084:0x00000000:0125
[ 4436.405781] iwlwifi 0000:08:00.0: Failed to run INIT ucode: -5
[ 4436.405895] iwlwifi 0000:08:00.0: Unable to initialize device.

```

Sorry for so long output. I have tried all methods in thread [http://ubuntuforums.org/showthread.php?t=2120777](http://ubuntuforums.org/showthread.php?t=2120777), which I think it's similar to me.
But I failed. Now I want to paster my ' uname -a' and ' lsb_release'.
```

nico@jacob-pc:~$ uname -a
Linux jacob-pc 3.5.0-25-generic #39~precise1-Ubuntu SMP Tue Feb 26 00:07:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
nico@jacob-pc:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
nico@jacob-pc:~$ 

```

Please take me out from this trouble, if anyone could give me a useful suggestion, I will be very very happy. Because I have struggled with 
this problem for several days.


Finally, it's my desktop, you can look into upper right corner, displaying Wireless networks device not ready.

---

### Post by 67kyj on 2013-03-05
Hello, is there anybody can help me? 
I'm so eager to solve this problem... :confused:

---

### Post by chili555 on 2013-03-06
> Microcode SW error detected.  Restarting 0x82000000.I suspect this is at least a part of the problem. Please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi fw_restart=1
```Any improvements?```
sudo iwlist wlan0 scan
```This part is very unusual:> nico@jacob-pc:~$ uname -a
Linux jacob-pc [COLOR="#FF0000"]3.5.0-25-generic[/COLOR] #39~[COLOR="#FF0000"]precise[/COLOR]1-Ubuntu SMP Tue Feb 26 00:07:14 UTC 2013 x86_64 x86_64 x86_64 GNU/LinuxIn other words, it appears you have a Quantal 12.10 kernel installed on your Precise 12.04 installation. What explains that? Can you reboot and get to the GRUB menu with the shift key and boot into an earlier kernel? If so, does the wireless work? Are there similar errors?```
dmesg | grep iwl
```There was a bug fixed in 12.10 having to do with loading and unloading iwlwifi. I wonder if you have the fix:```
cat /etc/modprobe.d/iwlwifi.conf
```For reference, here is mine:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```If you are running a 12.10 kernel without the conf file, I wonder if that is, at least, part of the issue.

Finally, are your firmware files uncorrupted?```
md5sum /lib/firmware/iwl*
```For reference, here are mine. If yours are the same, just tell us that and there is no need to flood the forum with your output:```
9f81a060ed274f76cd605295da77f7a6  /lib/firmware/iwlwifi-1000-5.ucode
d65c0dfc4c2f60ccad8614edbb39ed2b  /lib/firmware/iwlwifi-100-5.ucode
add82f1fabd4f28702382f6bafcb41b1  /lib/firmware/iwlwifi-105-6.ucode
445cb8a68e85e5b39e7fc35b5f9d03f9  /lib/firmware/iwlwifi-135-6.ucode
4132a323dd8966c43371de622db8aacc  /lib/firmware/iwlwifi-2000-6.ucode
faa4f10c56ac3c9baf9cc14b49a1ccaa  /lib/firmware/iwlwifi-2030-6.ucode
4df235482ac6c083e2b51cfb4d85c0fd  /lib/firmware/iwlwifi-3945-2.ucode
bd6c33d15822b6005079849b5f4fa4c4  /lib/firmware/iwlwifi-4965-2.ucode
d1f08911dfdbad1603b31d6f5113d852  /lib/firmware/iwlwifi-5000-5.ucode
fd5e408b84517c8c77e761d23d8ffa98  /lib/firmware/iwlwifi-5150-2.ucode
feea228ed059c3a998c12031313242b8  /lib/firmware/iwlwifi-6000-4.ucode
c66b20f9d5ac307ccae24989c5719fef  /lib/firmware/iwlwifi-6000g2a-5.ucode
4b47db024c8a0cba872c3e98e907a378  /lib/firmware/iwlwifi-6000g2a-6.ucode
1f1763dfd472a487c3d61eac0a12b766  /lib/firmware/iwlwifi-6000g2b-6.ucode
47cea8c3c90eeddf3d527685c05e5567  /lib/firmware/iwlwifi-6050-5.ucode

```[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by 67kyj on 2013-03-07
First I want to say thank you to you, I have spent lots of times on this. I'm close to reinstall the system with debian...
Because I believe debian can slove this problem better.

> **chili555 said:**
> I suspect this is at least a part of the problem. Please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi fw_restart=1
```Any improvements?```
sudo iwlist wlan0 scan
```

I did it, but no improvements. The output of ' iwlist wlan0 scan' is same
```

iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

```

> This part is very unusual:In other words, it appears you have a Quantal 12.10 kernel installed on your Precise 12.04 installation. What explains that? Can you reboot and get to the GRUB menu with the shift key and boot into an earlier kernel? If so, does the wireless work? Are there similar errors?```
dmesg | grep iwl
```


I installed the newer kernel image 3.5 manually, because I thought it could fix this problem, but failed. My original kernel image was
3.2.0-38-generic, and I have changed to it, but this process can't fix this too.
The output from 'dmesg | grep iwl' is same as before.


> There was a bug fixed in 12.10 having to do with loading and unloading iwlwifi. I wonder if you have the fix:```
cat /etc/modprobe.d/iwlwifi.conf
```For reference, here is mine:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```If you are running a 12.10 kernel without the conf file, I wonder if that is, at least, part of the issue.

I haven't that before, and when I run the command 'lsmod | grep iwl', there is no anything about iwlmvm or iwldvm in the output.
But I still tried this conf file, nothing has been changed, the problem still exist.

> Finally, are your firmware files uncorrupted?```
md5sum /lib/firmware/iwl*
```

I run that command, hash numbers are same as you.
In fact, I tried all the methods which I mentioned in the thread [http://ubuntuforums.org/showthread.php?t=2120777](http://ubuntuforums.org/showthread.php?t=2120777)
Nothing can help me...  

I believed ubuntu is better than debian on laptop, but I'm so sad to say I'd prefer to use debian again.
I have used debian for a long time, although it's not so good as ubuntu, I can always find a way to work around 
any problems everytime. I just changed system after changing my laptop...

This problem grieves me so badly...

---

### Post by chili555 on 2013-03-07
I just worked on a case using an Intel wireless card and the very same driver iwlwifi where the poster couldn't get it to work with an upgraded kernel but it did work perfectly with a clean install. Please at least try the live CD for 12.10 before you go away to Debian.

---

### Post by 67kyj on 2013-03-07
Ok, this weekend I will try it  as a last chance. I'm very appreciate of your help whether it can work out of my box or not .

I'd prefer to use a LTS version, not a version which need to upgrade frequently. That's why I always use debian stable for a long time.And I always can install a backports from unstable, or compile something from the newer source manually.

In fact, I met debian and ubuntu at almost same time, but my laptop was so old, it can't run ubuntu so fast, then I chose debian.

---

### Post by 67kyj on 2013-03-25
Well, everybody, I had tried many ways to walk around this problem.
Now I would have to say I have to install a debian stable instead of ubuntu.

I tried ubuntu LTS 12.04, and 12.10. Neither of them can drive my wifi.
But yesterday, I installed debian stable, it works on my laptop.

The wifi module under Ubuntu is called iwlwifi, it's called iwlagn under debian.
The firmware ( non-free ) for intel wireless N-1000 is called iwlwifi-1000-5.ucode 
under ubuntu, and iwlwifi-1000-3.ucode under debian.

I tried to put iwlwifi-1000-3.ucode from debian into /lib/firmware under Ubuntu,
but it can't solve this problem.

In the end, I have to install debian on my laptop.

---

### Post by 67kyj on 2013-03-27
HI, I have solved this problem occasionally.

First, I think there is something wrong with the firmware for Intel Centrino Wireless-N 1000.
That firmware which comes from the LTS 12.04 maybe has some bugs, its name is iwlwifi-1000-5.ucode.
Using this firmware can't make wlan work.

The way to resolve this is to download a new firmware from this address.
[http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-1000-ucode-128.50.3.1.tgz](http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-1000-ucode-128.50.3.1.tgz)

This firmware is only for kernel [FONT=Arial][COLOR=#000000][SIZE=2]2.6.30+, the original one is for 3.2+. Yes! You guess that !!
[/SIZE]LTS 12.04 use a latest one from the website, that's the reason. So just d[SIZE=2]elete or rename the original one, 
and put[/SIZE][SIZE=3] [SIZE=2]iwlwifi-1000-3.ucode from that tarball to /lib/firmware, and run
```

sudo modprobe -r iwlwifi
sudo modprobe iwlwifi

```

Enjoy it!

PS: In the last thread, I said I had tried all ways to solve this problem, yes I did. But I made a mistake,
I didn't delete/rename the original one under /lib/firmware, so it still loaded the original one.[/SIZE][/SIZE][/COLOR][/FONT]

---

### Post by chili555 on 2013-03-27
Thanks for the information. It will help me and, I'm sure, many searchers.

---

### Post by 67kyj on 2013-03-27
> **chili555 said:**
> Thanks for the information. It will help me and, I'm sure, many searchers.

Today when I awaken my laptop from hibernation, it still appear this problem :mad:
Then I relize that it's back again. I checked the directory /lib/firmware, 
the original firmware is still there, but the renamed one is there too. 

So I do the same routine again, now it's working very good.
I think that it's time to file a bug report to ubuntu team.

The problem is about package linux-firmware, they use a lastest intel wireless-N 1000 firmware,
the best way to solve this one is to replace it with an older one, and redistribute the package.
Perhaps this way is too hard to come true, but is there a possibility that we come out a 
suggestion and ask them to write a script to avoid loading the lastest one? This will make 
others replace it manually.

---

### Post by chili555 on 2013-03-28
> is there a possibility that we come out a
suggestion and ask them to write a script to avoid loading the lastest one? This will make
others replace it manually. Did you file the bug yet? I think they will simply remove the faulty firmware and revert to the known working firmware unless  iwlwifi-1000-5.ucode is also used successfully by another device.

---

