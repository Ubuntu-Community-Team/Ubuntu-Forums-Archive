---
title: "UNCLAIMED network controler"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by guliminipietro on 2012-10-15
Hi, I have recently installed ubuntu 11.04 on my laptop but my network controler device is UNCLAIMED and I dont know how to fix this issue.

---

### Post by TheFu on 2012-10-15
What do the log files say?
* **dmesg**
* /var/log/syslog
* **sudo lshw -c  network**
You'll need to be root or in the adm group to view syslog.

---

### Post by chili555 on 2012-10-15
> **TheFu said:**
> What do the log files say?
* **dmesg**
* /var/log/syslog
* **sudo lshw -c  network**
You'll need to be root or in the adm group to view syslog.With all respect to my colleague, I don't think we want to see _all_ of dmesg, nor _all_ of syslog. They are quite lengthy and it will be tedious sorting through them to see the relevant parts. Instead, let's see:```
sudo modprobe iwlagn
dmesg | grep iwl
sudo lshw -C network  [COLOR="Red"]<--that's a capital C[/COLOR]
lspci -nn | grep 0280
```

Why did you install 11.04? We have made lots of progress in drivers in 1 1/2 years!

---

### Post by guliminipietro on 2012-10-15
Thanks guys and sorry for delay, I was out for a while: This is the outcome I got on terminal from dmesg | grep iwl:

[  500.283764] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  500.283767] iwlagn: Copyright(c) 2003-2010 Intel Corporation

And this is what I got from sudo lshw -C network:
*-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 24
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f1500000-f1501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: e8:03:9a:b6:ba:da
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.20.53.178 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff

And this is the outcome of lspci -nn | grep 0280:

02:00.0 Network controller [0280]: Intel Corporation Device [8086:088e] (rev 24)

---

### Post by chili555 on 2012-10-15
> Network controller [0280]: Intel Corporation Device [8086:088e] (rev 24)Your device is covered by the driver iwlwifi in 12.04. It is too new to be covered by iwlagn in 11.04. Would you care to upgrade or resort to other, perhaps harder, methods?

---

### Post by TheFu on 2012-10-15
It appears that no driver was automatically found for the Intel NIC. Linux knows it is a NIC, but doesn't know which chip it uses, so it can't automatically load the correct driver.  In short, figure out what chip Intel is using, find the driver, build it, as needed, and add it to your /etc/modules file.  You can use **modprobe**, **lsmod**, and **rmmod** to help, AFTER you determine which module is needed.

BTW, the **lshw -c network** worked on my system.  It is shown to be the same as -C in the **lshw -h **output, but the manpage does not show it. Hummm.  I'll be using the, more correct, -C in the future myself.

---

### Post by guliminipietro on 2012-10-15
> **chili555 said:**
> Your device is covered by the driver iwlwifi in 12.04. It is too new to be covered by iwlagn in 11.04. Would you care to upgrade or resort to other, perhaps harder, methods?


Do you mean I wont have this problem on a new version?

---

### Post by ahallubuntu on 2012-10-15
Yes, 12.04 LTS is likely to install a driver automatically.

I really like Ubuntu 11.04 (using it to type this), because it was the last version of Ubuntu with Gnome 2 and it has been very smooth for me on several machines.  But, official support for 11.04 ends this month, sadly, so new updates and fixes will no longer be added for 11.04 soon.  I'm going to have to move to 12.04 too which will be some headaches (Gnome 3) for sure but in the end may be worth it...

---

### Post by chili555 on 2012-10-15
> **guliminipietro said:**
> Do you mean I wont have this problem on a new version?Correct. The driver iwlwifi covers your device in 12.04:```
$ modinfo iwlwifi | grep 088E
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]088E[/COLOR]sv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i* 
```

---

### Post by guliminipietro on 2012-10-15
> **chili555 said:**
> Correct. The driver iwlwifi covers your device in 12.04:```
$ modinfo iwlwifi | grep 088E
alias:          pci:v0000[COLOR=Red]8086[/COLOR]d0000[COLOR=Red]088E[/COLOR]sv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i* 
```

I upgraded it to 11.10, now my ethenet is also unclaimed. but my wireless interface is disabled

---

### Post by chili555 on 2012-10-15
> I upgraded it to 11.10, now my ethenet is also unclaimed.Please try:```
sudo modprobe r8169
```Did it start up?> but my wireless interface is disabled Please post:```
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by ahallubuntu on 2012-10-15
Even if 11.10 worked perfectly, it would buy you only another six months of support, anyway.  Ubuntu releases a long-term support version every two years, and it's really best to use one of those if possible for a first installation.  12.04 LTS will be supported until April 2017 and is more likely to support your networking hardware automatically.

---

### Post by guliminipietro on 2012-10-15
> **chili555 said:**
> Please try:```
sudo modprobe r8169
```Did it start up?Please post:```
rfkill list all
dmesg | grep iwl
```Thanks.

modprobe r8169 waked my ethernet up. now I have wired connection.
and this is the outcome of rfkill list all:
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

And after dmesg I got:

[   14.262616] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.262618] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   14.262698] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.262726] iwlagn 0000:02:00.0: setting latency timer to 64
[   14.262792] iwlagn 0000:02:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
[   14.278499] iwlagn 0000:02:00.0: device EEPROM VER=0x756, CALIB=0x6
[   14.278501] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   14.278502] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   14.278521] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.278680] iwlagn 0000:02:00.0: irq 43 for MSI/MSI-X
[   16.192624] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.1 build 33993
[   16.956529] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.097559] Modules linked in: snd_timer snd_seq_device arc4 i915(+) drm_kms_helper drm snd uvcvideo soundcore mxm_wmi videodev wmi snd_page_alloc i2c_algo_bit mei(C) iwlagn psmouse btusb ndiswrapper(+) bluetooth serio_raw video ath9k mac80211 ath9k_common ath9k_hw ath cfg80211 lp parport ahci libahci xhci_hcd
[   17.097828] Modules linked in: snd_timer snd_seq_device arc4 i915(+) drm_kms_helper drm snd uvcvideo soundcore mxm_wmi videodev wmi snd_page_alloc i2c_algo_bit mei(C) iwlagn psmouse btusb ndiswrapper(+) bluetooth serio_raw video ath9k mac80211 ath9k_common ath9k_hw ath cfg80211 lp parport ahci libahci xhci_hcd
[   35.021688] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   35.021693] iwlagn 0000:02:00.0: Loaded firmware version: 17.168.5.1 build 33993
[   35.021973] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
[   35.021975] iwlagn 0000:02:00.0: Status: 0x00040225, count: 6
[   35.021977] iwlagn 0000:02:00.0: 0x000019B6 | ADVANCED_SYSASSERT          
[   35.021979] iwlagn 0000:02:00.0: 0x00014D88 | uPc
[   35.021980] iwlagn 0000:02:00.0: 0x00014D7A | branchlink1
[   35.021982] iwlagn 0000:02:00.0: 0x00014D7A | branchlink2
[   35.021983] iwlagn 0000:02:00.0: 0x0000CFCE | interruptlink1
[   35.021985] iwlagn 0000:02:00.0: 0x00000000 | interruptlink2
[   35.021986] iwlagn 0000:02:00.0: 0x00000001 | data1
[   35.021988] iwlagn 0000:02:00.0: 0x0000008C | data2
[   35.021989] iwlagn 0000:02:00.0: 0x000002E2 | line
[   35.021990] iwlagn 0000:02:00.0: 0x0000A2C0 | beacon time
[   35.021992] iwlagn 0000:02:00.0: 0x0000ED40 | tsf low
[   35.021993] iwlagn 0000:02:00.0: 0x00000000 | tsf hi
[   35.021995] iwlagn 0000:02:00.0: 0x00000000 | time gp1
[   35.021996] iwlagn 0000:02:00.0: 0x0000ED44 | time gp2
[   35.021997] iwlagn 0000:02:00.0: 0x00000000 | time gp3
[   35.021999] iwlagn 0000:02:00.0: 0x000111A8 | uCode version
[   35.022000] iwlagn 0000:02:00.0: 0x000000B0 | hw version
[   35.022002] iwlagn 0000:02:00.0: 0x00480303 | board version
[   35.022003] iwlagn 0000:02:00.0: 0x0900005A | hcmd
[   35.022005] iwlagn 0000:02:00.0: CSR values:
[   35.022006] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   35.022035] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[   35.022060] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   35.022086] iwlagn 0000:02:00.0:                     CSR_INT: 0X00000000
[   35.022112] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   35.022138] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   35.022171] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X00000030
[   35.022200] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
[   35.022226] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   35.022251] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X000000b0
[   35.022277] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0X969d0ffd
[   35.022303] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000801
[   35.022328] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00030001
[   35.022354] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
[   35.022380] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000007
[   35.022406] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   35.022431] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   35.022457] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   35.022483] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[   35.022508] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   35.022534] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   35.022559] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   35.022585] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   35.022611] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   35.022612] iwlagn 0000:02:00.0: FH register values:
[   35.022666] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X02dbc200
[   35.022715] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X002dbc00
[   35.022769] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000000
[   35.022818] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   35.022872] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   35.022927] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   35.022982] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   35.023036] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   35.023091] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   35.023258] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 3 entries
[   35.023317] iwlagn 0000:02:00.0: EVT_LOGT:0000000000:0x000002c7:0117
[   35.023362] iwlagn 0000:02:00.0: EVT_LOGT:0000060626:0x0900005a:0401
[   35.023406] iwlagn 0000:02:00.0: EVT_LOGT:0000060753:0x00000000:0125
[   35.521949] iwlagn 0000:02:00.0: Error sending REPLY_BT_COEX_PROT_ENV: time out after 500ms.
[   35.521956] iwlagn 0000:02:00.0: failed to send BT env command
[   35.522748] iwlagn 0000:02:00.0: Failed to run INIT ucode: -110
[   35.522873] iwlagn 0000:02:00.0: Unable to initialize device.
[   36.109016] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   36.109020] iwlagn 0000:02:00.0: Loaded firmware version: 17.168.5.1 build 33993
[   36.109275] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
[   36.109277] iwlagn 0000:02:00.0: Status: 0x00040225, count: 6
[   36.109279] iwlagn 0000:02:00.0: 0x000019B6 | ADVANCED_SYSASSERT          
[   36.109281] iwlagn 0000:02:00.0: 0x000168D4 | uPc
[   36.109283] iwlagn 0000:02:00.0: 0x000168C4 | branchlink1
[   36.109284] iwlagn 0000:02:00.0: 0x000168C4 | branchlink2
[   36.109286] iwlagn 0000:02:00.0: 0x0000DC6E | interruptlink1
[   36.109288] iwlagn 0000:02:00.0: 0x00000000 | interruptlink2
[   36.109289] iwlagn 0000:02:00.0: 0x00000001 | data1
[   36.109291] iwlagn 0000:02:00.0: 0x0000008C | data2
[   36.109292] iwlagn 0000:02:00.0: 0x000002E2 | line
[   36.109294] iwlagn 0000:02:00.0: 0x00009449 | beacon time
[   36.109296] iwlagn 0000:02:00.0: 0x0000FBB7 | tsf low
[   36.109297] iwlagn 0000:02:00.0: 0x00000000 | tsf hi
[   36.109299] iwlagn 0000:02:00.0: 0x00000000 | time gp1
[   36.109300] iwlagn 0000:02:00.0: 0x0000FBBB | time gp2
[   36.109302] iwlagn 0000:02:00.0: 0x00000000 | time gp3
[   36.109303] iwlagn 0000:02:00.0: 0x000111A8 | uCode version
[   36.109305] iwlagn 0000:02:00.0: 0x000000B0 | hw version
[   36.109307] iwlagn 0000:02:00.0: 0x00480303 | board version
[   36.109308] iwlagn 0000:02:00.0: 0x0900005A | hcmd
[   36.109310] iwlagn 0000:02:00.0: CSR values:
[   36.109312] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   36.109341] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[   36.109367] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   36.109393] iwlagn 0000:02:00.0:                     CSR_INT: 0X00000000
[   36.109418] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   36.109444] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   36.109470] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X00000030
[   36.109496] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
[   36.109522] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   36.109547] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X000000b0
[   36.109573] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0X969d0ffd
[   36.109615] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000801
[   36.109643] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00030001
[   36.109680] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
[   36.109707] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000008
[   36.109733] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   36.109758] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   36.109785] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   36.109810] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[   36.109836] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   36.109862] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   36.109888] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   36.109914] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   36.109939] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   36.109940] iwlagn 0000:02:00.0: FH register values:
[   36.109994] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X02dbc200
[   36.110049] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X002dbc00
[   36.110103] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000000
[   36.110158] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   36.110212] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   36.110267] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   36.110321] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   36.110376] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   36.110431] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   36.110598] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 3 entries
[   36.110650] iwlagn 0000:02:00.0: EVT_LOGT:0000000000:0x000002c7:0117
[   36.110695] iwlagn 0000:02:00.0: EVT_LOGT:0000064329:0x0900005a:0401
[   36.110734] iwlagn 0000:02:00.0: EVT_LOGT:0000064463:0x00000000:0125
[   36.609381] iwlagn 0000:02:00.0: Error sending REPLY_BT_CONFIG: time out after 500ms.
[   36.609388] iwlagn 0000:02:00.0: failed to send BT Coex Config
[   37.109120] iwlagn 0000:02:00.0: Error sending REPLY_BT_COEX_PRIO_TABLE: time out after 500ms.
[   37.109128] iwlagn 0000:02:00.0: failed to send BT prio tbl command
[   37.608859] iwlagn 0000:02:00.0: Error sending REPLY_BT_COEX_PROT_ENV: time out after 500ms.
[   37.608867] iwlagn 0000:02:00.0: failed to send BT env command
[   37.608999] iwlagn 0000:02:00.0: Unable to initialize device.
[   37.688235] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x2000000.
[   37.688239] iwlagn 0000:02:00.0: Loaded firmware version: 17.168.5.1 build 33993
[   37.688486] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
[   37.688489] iwlagn 0000:02:00.0: Status: 0x00040225, count: 6
[   37.688491] iwlagn 0000:02:00.0: 0x000019B6 | ADVANCED_SYSASSERT          
[   37.688493] iwlagn 0000:02:00.0: 0x000168D4 | uPc
[   37.688494] iwlagn 0000:02:00.0: 0x000168C4 | branchlink1
[   37.688496] iwlagn 0000:02:00.0: 0x000168C4 | branchlink2
[   37.688497] iwlagn 0000:02:00.0: 0x0000DC6E | interruptlink1
[   37.688499] iwlagn 0000:02:00.0: 0x00000000 | interruptlink2
[   37.688500] iwlagn 0000:02:00.0: 0x00000001 | data1
[   37.688502] iwlagn 0000:02:00.0: 0x0000008C | data2
[   37.688504] iwlagn 0000:02:00.0: 0x000002E2 | line
[   37.688505] iwlagn 0000:02:00.0: 0x000092CA | beacon time
[   37.688507] iwlagn 0000:02:00.0: 0x0000FD36 | tsf low
[   37.688508] iwlagn 0000:02:00.0: 0x00000000 | tsf hi
[   37.688510] iwlagn 0000:02:00.0: 0x00000000 | time gp1
[   37.688511] iwlagn 0000:02:00.0: 0x0000FD3A | time gp2
[   37.688513] iwlagn 0000:02:00.0: 0x00000000 | time gp3
[   37.688514] iwlagn 0000:02:00.0: 0x000111A8 | uCode version
[   37.688516] iwlagn 0000:02:00.0: 0x000000B0 | hw version
[   37.688517] iwlagn 0000:02:00.0: 0x00480303 | board version
[   37.688519] iwlagn 0000:02:00.0: 0x0900005A | hcmd
[   37.688521] iwlagn 0000:02:00.0: CSR values:
[   37.688522] iwlagn 0000:02:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[   37.688550] iwlagn 0000:02:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480303
[   37.688588] iwlagn 0000:02:00.0:          CSR_INT_COALESCING: 0X0000ff40
[   37.688617] iwlagn 0000:02:00.0:                     CSR_INT: 0X00000000
[   37.688642] iwlagn 0000:02:00.0:                CSR_INT_MASK: 0X00000000
[   37.688668] iwlagn 0000:02:00.0:           CSR_FH_INT_STATUS: 0X00000000
[   37.688694] iwlagn 0000:02:00.0:                 CSR_GPIO_IN: 0X00000030
[   37.688719] iwlagn 0000:02:00.0:                   CSR_RESET: 0X00000000
[   37.688745] iwlagn 0000:02:00.0:                CSR_GP_CNTRL: 0X080403c5
[   37.688771] iwlagn 0000:02:00.0:                  CSR_HW_REV: 0X000000b0
[   37.688797] iwlagn 0000:02:00.0:              CSR_EEPROM_REG: 0X969d0ffd
[   37.688822] iwlagn 0000:02:00.0:               CSR_EEPROM_GP: 0X90000801
[   37.688848] iwlagn 0000:02:00.0:              CSR_OTP_GP_REG: 0X00030001
[   37.688873] iwlagn 0000:02:00.0:                 CSR_GIO_REG: 0X00080042
[   37.688899] iwlagn 0000:02:00.0:            CSR_GP_UCODE_REG: 0X00000008
[   37.688925] iwlagn 0000:02:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[   37.688950] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[   37.688976] iwlagn 0000:02:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[   37.689002] iwlagn 0000:02:00.0:                 CSR_LED_REG: 0X00000018
[   37.689027] iwlagn 0000:02:00.0:        CSR_DRAM_INT_TBL_REG: 0X00000000
[   37.689053] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[   37.689078] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[   37.689104] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[   37.689130] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[   37.689131] iwlagn 0000:02:00.0: FH register values:
[   37.689185] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X02dbc200
[   37.689240] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X002dbc00
[   37.689288] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000000
[   37.689342] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[   37.689397] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[   37.689445] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[   37.689500] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[   37.689555] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[   37.689609] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[   37.689776] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 3 entries
[   37.689841] iwlagn 0000:02:00.0: EVT_LOGT:0000000000:0x000002c7:0117
[   37.689880] iwlagn 0000:02:00.0: EVT_LOGT:0000064712:0x0900005a:0401
[   37.689924] iwlagn 0000:02:00.0: EVT_LOGT:0000064828:0x00000000:0125
[   38.188564] iwlagn 0000:02:00.0: Error sending REPLY_BT_CONFIG: time out after 500ms.
[   38.188570] iwlagn 0000:02:00.0: failed to send BT Coex Config
[   38.688301] iwlagn 0000:02:00.0: Error sending REPLY_BT_COEX_PRIO_TABLE: time out after 500ms.
[   38.688308] iwlagn 0000:02:00.0: failed to send BT prio tbl command
[   39.188047] iwlagn 0000:02:00.0: Error sending REPLY_BT_COEX_PROT_ENV: time out after 500ms.
[   39.188055] iwlagn 0000:02:00.0: failed to send BT env command
[   39.188189] iwlagn 0000:02:00.0: Unable to initialize device.

---

### Post by chili555 on 2012-10-15
Let's be sure your ethernet starts every boot:```
sudo su
echo r8169 >> /etc/modules
exit
```This looks awful!> [ 35.021688] iwlagn 0000:02:00.0: Microcode SW error detected. Restarting 0x2000000.
[ 35.021693] iwlagn 0000:02:00.0: Loaded firmware version: 17.168.5.1 build 33993
[ 35.021973] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
....
[ 39.188055] iwlagn 0000:02:00.0: failed to send BT env command
[ 39.188189] iwlagn 0000:02:00.0: Unable to initialize device.
Let's be sure your firmware files are intact and uncorrupted:```
md5sum /lib/firmware/iwlwifi*
```Let's also try a driver parameter:```
sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=N
```Then check dmesg:```
dmesg | tail -n15
```

---

### Post by guliminipietro on 2012-10-15
My ethernet started again.

> **chili555 said:**
> Let's be sure your ethernet starts every boot:```
sudo su
echo r8169 >> /etc/modules
exit
```This looks awful!Let's be sure your firmware files are intact and uncorrupted:```
md5sum /lib/firmware/iwlwifi*
```Let's also try a driver parameter:```
sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=N
```Then check dmesg:```
dmesg | tail -n15
```

Outcomes of modprobes are the same:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

and after dmesg these lines showed up:

[ 4870.561049] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 4873.986381] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600

---

### Post by chili555 on 2012-10-15
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.Uh oh, we'd better examine and fix this:```
cat /etc/modprobe.d/blacklist
```My request was for the last 15 lines of dmesg (tail -n15). Wasn't there anything about iwlagn in there? How about:```
dmesg | grep iwlagn | tail -n25
```

---

### Post by guliminipietro on 2012-10-15
> **chili555 said:**
> Uh oh, we'd better examine and fix this:```
cat /etc/modprobe.d/blacklist
```My request was for the last 15 lines of dmesg (tail -n15). Wasn't there anything about iwlagn in there? How about:```
dmesg | grep iwlagn | tail -n25
```

So here is the result of blacklist:

blacklist ath_hal
blacklist ath_pci

and this is what I got from dmesg:

[ 4716.196062] iwlagn 0000:02:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 4716.196089] iwlagn 0000:02:00.0:             CSR_ANA_PLL_CFG: 0X00000000
[ 4716.196115] iwlagn 0000:02:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 4716.196142] iwlagn 0000:02:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
[ 4716.196145] iwlagn 0000:02:00.0: FH register values:
[ 4716.196183] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X0281ce00
[ 4716.196226] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X00280930
[ 4716.196262] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000000
[ 4716.196299] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
[ 4716.196336] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 4716.196372] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 4716.196428] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 4716.196472] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 4716.196509] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 4716.196594] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 3 entries
[ 4716.196635] iwlagn 0000:02:00.0: EVT_LOGT:0000000000:0x000002c7:0117
[ 4716.196668] iwlagn 0000:02:00.0: EVT_LOGT:0000060300:0x0900005a:0401
[ 4716.196701] iwlagn 0000:02:00.0: EVT_LOGT:0000060434:0x00000000:0125
[ 4716.696159] iwlagn 0000:02:00.0: Error sending REPLY_BT_CONFIG: time out after 500ms.
[ 4716.696166] iwlagn 0000:02:00.0: failed to send BT Coex Config
[ 4717.195902] iwlagn 0000:02:00.0: Error sending REPLY_BT_COEX_PRIO_TABLE: time out after 500ms.
[ 4717.195910] iwlagn 0000:02:00.0: failed to send BT prio tbl command
[ 4717.695658] iwlagn 0000:02:00.0: Error sending REPLY_BT_COEX_PROT_ENV: time out after 500ms.
[ 4717.695665] iwlagn 0000:02:00.0: failed to send BT env command
[ 4717.695750] iwlagn 0000:02:00.0: Unable to initialize device.

---

### Post by chili555 on 2012-10-15
> So here is the result of blacklist:

blacklist ath_hal
blacklist ath_pciSince you don't have an Atheros wireless device, we can eliminate the troublesome file altogether:```
sudo rm /etc/modprobe.d/blacklist
```How about this?```
md5sum /lib/firmware/iwlwifi*
```I'd like to find out if you have a corrupted firmware file.

I'd suggest you warm up your CD burner so we can try 12.04.

---

### Post by guliminipietro on 2012-10-15
> **chili555 said:**
> Since you don't have an Atheros wireless device, we can eliminate the troublesome file altogether:```
sudo rm /etc/modprobe.d/blacklist
```How about this?```
md5sum /lib/firmware/iwlwifi*
```I'd like to find out if you have a corrupted firmware file.

I'd suggest you warm up your CD burner so we can try 12.04.

So this is what happened after iwlwifi* code:

df79176a88147862c5fe2b7f81c11711  /lib/firmware/iwlwifi-1000-3.ucode
9f81a060ed274f76cd605295da77f7a6  /lib/firmware/iwlwifi-1000-5.ucode
d65c0dfc4c2f60ccad8614edbb39ed2b  /lib/firmware/iwlwifi-100-5.ucode
add82f1fabd4f28702382f6bafcb41b1  /lib/firmware/iwlwifi-105-6.ucode
445cb8a68e85e5b39e7fc35b5f9d03f9  /lib/firmware/iwlwifi-135-6.ucode
4132a323dd8966c43371de622db8aacc  /lib/firmware/iwlwifi-2000-6.ucode
faa4f10c56ac3c9baf9cc14b49a1ccaa  /lib/firmware/iwlwifi-2030-6.ucode
4df235482ac6c083e2b51cfb4d85c0fd  /lib/firmware/iwlwifi-3945-2.ucode
bd6c33d15822b6005079849b5f4fa4c4  /lib/firmware/iwlwifi-4965-2.ucode
4382e0ee86e57b9e5fdd1f77652da391  /lib/firmware/iwlwifi-5000-1.ucode
10ca882a6e16e0d79e5f4b2b1b516e4e  /lib/firmware/iwlwifi-5000-2.ucode
d1f08911dfdbad1603b31d6f5113d852  /lib/firmware/iwlwifi-5000-5.ucode
fd5e408b84517c8c77e761d23d8ffa98  /lib/firmware/iwlwifi-5150-2.ucode
feea228ed059c3a998c12031313242b8  /lib/firmware/iwlwifi-6000-4.ucode
c66b20f9d5ac307ccae24989c5719fef  /lib/firmware/iwlwifi-6000g2a-5.ucode
0117445b398883258811bfbb3852f1a8  /lib/firmware/iwlwifi-6000g2b-5.ucode
1f1763dfd472a487c3d61eac0a12b766  /lib/firmware/iwlwifi-6000g2b-6.ucode
2520eeeb638f22811e50d2d1912ef807  /lib/firmware/iwlwifi-6050-4.ucode
47cea8c3c90eeddf3d527685c05e5567  /lib/firmware/iwlwifi-6050-5.ucode

---

### Post by guliminipietro on 2012-10-15
Thanks. I upgraded it to ubuntu 12.04 and I got it to work. Apparently the only version of Ubuntu compatible with my system was the newest one.

---

