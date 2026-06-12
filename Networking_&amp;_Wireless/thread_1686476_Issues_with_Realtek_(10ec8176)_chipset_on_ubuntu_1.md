---
title: "Issues with Realtek (10ec::8176) chipset on ubuntu 10.10 on a Toshiba NB505"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by wirednuke83 on 2011-02-12
Hey all,

I am returning to linux after a 10 year hiatus... I have forgotten most stuff, but its all familiar and it's coming back to my fast.. and i'm hoping i'll figure this out on my own.. but i'm starting to get frustrated.

After figuring out and installing the drivers my wireless comes up as disabled in ubunto 10.10. I figured out how to re-enable it, but it always says it's disconnected and wont locate any available networks.

After looking at all the below information on my own, I'm fairly certain the correct driver is installed properly... I think the radio to the wireless nic isn't getting power.. and I haven't been able to figure out how to turn it on. The wireless light on my netbook is unlit. 

I'm not sure how to turn the radio on... any help? Or did I miss a bigger issue? 

I've been googling for about the last 12-15 hours on this, so I apologize if I missed an existing post. I'm probably just tired.

V/r

Phil (wirednuke83)



 All the required info....

[B]Netbook Model Number/Part Number:

[/B]Toshiba NB505-N500BL
PLL50U-01S008

The nice thing about Toshiba is they don't tell you anything about the wireless adapter other then the fact that its 802.11b/g/n... Quite annoying... 

[B]Wireless Brand, Model and Wireless Chipset:

[/B]lspci -vvn
```
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: I/O ports at 2000 [size=256]
    Region 2: Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8192CE
    Kernel modules: r8192ce_pci
```

lsusb


```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

[B]Network Interfaces:

[/B]ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 1c:75:08:77:06:c3  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fe77:6c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5723134 (5.7 MB)  TX bytes:736361 (736.3 KB)
          Interrupt:46 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 88:25:2c:ba:9d:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f8368000-f8368100 
```

iwconfig:

```
wlan0     802.11bgn  Nickname:"rtl8192CE"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

[B]Modules:

[/B]lsmod | grep r8192ce_pci

```
r8192ce_pci           457666  0 
```

[B]Dmesg:

[/B]dmesg |grep 8192

```
[   83.471894] Linux kernel driver for RTL8192 based WLAN cards
[   83.471996] rtl8192CE 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   83.472011] rtl8192CE 0000:07:00.0: setting latency timer to 64
[   83.485126] =========>rtl8192ce_ReadBluetoothCoexistInfoFromHWPG(): EEPROMBluetoothCoexist:0, EEPROMBluetoothType:3
[   83.509108] ################>rtl8192ce_InitMAC()Reg0xEC:18051d59:11
[   83.509171] ################>rtl8192ce_InitMAC()Reg0xEC:98053f15:10
[   83.720956] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   84.615541] ================>r8192_wx_set_scan(): hwradio off
[   95.529953] ################>rtl8192ce_InitMAC()Reg0xEC:10051d59:11
[   95.530015] ################>rtl8192ce_InitMAC()Reg0xEC:90053f15:10
[   95.741944] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   95.757927] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[   95.777325] ################>rtl8192ce_InitMAC()Reg0xEC:10051d59:11
[   95.777391] ################>rtl8192ce_InitMAC()Reg0xEC:90053f15:10
[   95.989413] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   97.010627] ################>rtl8192ce_InitMAC()Reg0xEC:10051d59:11
[   97.010693] ################>rtl8192ce_InitMAC()Reg0xEC:90053f15:10
[   97.222698] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   97.231385] ================>r8192_wx_set_scan(): hwradio off
[  117.134732] ================>r8192_wx_set_scan(): hwradio off
[  147.134573] ================>r8192_wx_set_scan(): hwradio off
[  187.134097] ================>r8192_wx_set_scan(): hwradio off
[  237.135674] ================>r8192_wx_set_scan(): hwradio off
[  297.135297] ================>r8192_wx_set_scan(): hwradio off
[  357.134484] ================>r8192_wx_set_scan(): hwradio off
[  417.135476] ================>r8192_wx_set_scan(): hwradio off
[  454.119551] rtl8192CE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[  455.605696] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  456.311343] ============> r8192E suspend call.
[  456.311356] r8192E support WOL call??????????????????????
[  456.311447] rtl8192CE 0000:07:00.0: PCI INT A disabled
[  457.206354] rtl8192CE 0000:07:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[  457.206381] rtl8192CE 0000:07:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xf0100004)
[  457.206395] rtl8192CE 0000:07:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x2001)
[  457.206406] rtl8192CE 0000:07:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[  457.206419] rtl8192CE 0000:07:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  457.208499] ================>r8192E resume call.
[  457.208517] rtl8192CE 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  458.877140] ################>rtl8192ce_InitMAC()Reg0xEC:98053f15:1
[  458.877206] ################>rtl8192ce_InitMAC()Reg0xEC:98053f15:0
[  459.089425] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  459.125658] ################>rtl8192ce_InitMAC()Reg0xEC:90053f15:11
[  459.125724] ################>rtl8192ce_InitMAC()Reg0xEC:90053f15:10
[  459.338320] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  459.359673] ================>r8192_wx_set_scan(): hwradio off
[  460.965877] rtl8192CE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[  479.319262] ================>r8192_wx_set_scan(): hwradio off
[  510.061653] ================>r8192_wx_set_scan(): hwradio off
[  550.068089] ================>r8192_wx_set_scan(): hwradio off
[  600.064063] ================>r8192_wx_set_scan(): hwradio off
[  660.062561] ================>r8192_wx_set_scan(): hwradio off
[  720.063793] ================>r8192_wx_set_scan(): hwradio off
[  780.064744] ================>r8192_wx_set_scan(): hwradio off
[  840.063933] ================>r8192_wx_set_scan(): hwradio off
[  900.062644] ================>r8192_wx_set_scan(): hwradio off
[  960.063972] ================>r8192_wx_set_scan(): hwradio off
[ 1020.063777] ================>r8192_wx_set_scan(): hwradio off
[ 1080.063814] ================>r8192_wx_set_scan(): hwradio off
[ 1140.064388] ================>r8192_wx_set_scan(): hwradio off
[ 1200.064857] ================>r8192_wx_set_scan(): hwradio off
[ 1260.064307] ================>r8192_wx_set_scan(): hwradio off
[ 1320.063723] ================>r8192_wx_set_scan(): hwradio off
[ 1380.062360] ================>r8192_wx_set_scan(): hwradio off
[ 1440.063486] ================>r8192_wx_set_scan(): hwradio off
[ 1500.063774] ================>r8192_wx_set_scan(): hwradio off
[ 1560.063987] ================>r8192_wx_set_scan(): hwradio off
[ 1620.063697] ================>r8192_wx_set_scan(): hwradio off
[ 1680.065405] ================>r8192_wx_set_scan(): hwradio off
[ 1740.063992] ================>r8192_wx_set_scan(): hwradio off
[ 1800.063749] ================>r8192_wx_set_scan(): hwradio off
[ 1860.064070] ================>r8192_wx_set_scan(): hwradio off
[ 1920.063796] ================>r8192_wx_set_scan(): hwradio off
[ 1980.064028] ================>r8192_wx_set_scan(): hwradio off
[ 2040.064291] ================>r8192_wx_set_scan(): hwradio off
[ 2100.063921] ================>r8192_wx_set_scan(): hwradio off
[ 2160.064691] ================>r8192_wx_set_scan(): hwradio off
[ 2220.062924] ================>r8192_wx_set_scan(): hwradio off
[ 2280.063981] ================>r8192_wx_set_scan(): hwradio off
[ 2340.063782] ================>r8192_wx_set_scan(): hwradio off
[ 2400.064110] ================>r8192_wx_set_scan(): hwradio off
[ 2460.064231] ================>r8192_wx_set_scan(): hwradio off
[ 2520.064659] ================>r8192_wx_set_scan(): hwradio off
[ 2580.062650] ================>r8192_wx_set_scan(): hwradio off
[ 2640.063742] ================>r8192_wx_set_scan(): hwradio off
[ 2700.064302] ================>r8192_wx_set_scan(): hwradio off
[ 2760.064097] ================>r8192_wx_set_scan(): hwradio off
[ 2820.064449] ================>r8192_wx_set_scan(): hwradio off
[ 2880.063981] ================>r8192_wx_set_scan(): hwradio off
[ 2940.064317] ================>r8192_wx_set_scan(): hwradio off
[ 3000.064499] ================>r8192_wx_set_scan(): hwradio off
[ 3060.063758] ================>r8192_wx_set_scan(): hwradio off
[ 3120.062454] ================>r8192_wx_set_scan(): hwradio off
[ 3180.062301] ================>r8192_wx_set_scan(): hwradio off
[ 3240.064745] ================>r8192_wx_set_scan(): hwradio off
[ 3300.063956] ================>r8192_wx_set_scan(): hwradio off
[ 3360.063893] ================>r8192_wx_set_scan(): hwradio off
```

[B]Network Configuration:
[/B]
sudo lshw -C network

```
*-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 88:25:2c:ba:9d:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192CE driverversion=0005.1116.2010 firmware=56 latency=0 link=no multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0100000-f0103fff
 
```

[B]Scanning for networks:

[/B]iwlist wlan0 scan


```
wlan0     Scan completed :

```

[B]Ubuntu Version:

[/B]Description:    Ubuntu 10.10

[B]Kernel:
[/B]
2.6.35-22-generic i686[B]

Restarting the network:

[/B]sudo /etc/init.d/networking restart

```
 * Reconfiguring network interfaces...
   ...done.
```

---

### Post by bkratz on 2011-02-12
Dr. Chili comes through again--see post 2 of this thread

[http://ubuntuforums.org/showthread.php?t=1618554](http://ubuntuforums.org/showthread.php?t=1618554)

---

### Post by wirednuke83 on 2011-02-12
I appreciate your prompt reply:

That was the post that got me this far. I have already read through it. I feel the drivers are installed properly. I just can't figure out how to turn on the radio on the NIC, and this netbook has no wireless button on it, it's a software related key combination that doesn't seem to be recognized by ubuntu. 

So I have drivers installed... with no wifi indicating light and dmesg is full of spam about the radio being off.

I just don't know where to go from here?

V/r

Phil

---

### Post by bkratz on 2011-02-12
This is what I found in the manual--is this how you are trying to turn on the wifi?


To enable or disable wireless 
communication, use the Hot Key Fn + F8

By the way this is where I found the manual-should you need it

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2861101&rpn=PLL50U&modelFilter=NB505-N508GN&selCategory=2756709&selFamily=2336267](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=2861101&rpn=PLL50U&modelFilter=NB505-N508GN&selCategory=2756709&selFamily=2336267)

---

### Post by wirednuke83 on 2011-02-12
Yes, that is the prescribed method for enabling/disabling the wireless NIC from the keyboard. However, it's the function keyboard shortcuts are not recognized by ubuntu. The LED is off, dmesg says the radio is off. 
 
I checked the bios and there's no function to leave it "always on". 
 
I guess i'm looking for a software means to force it on?

---

### Post by wirednuke83 on 2011-02-15
Bump... sorry to bring this back up, but i'm still at a total loss on how to fix this issue.
 
Thanks!
 
V/R
 
Phil

---

### Post by tlcstat on 2011-02-17
Greetings
> So I have drivers installed... with no wifi indicating light and dmesg is full of spam about the radio being off.

FYI: My wifi light isn't functional with the driver installed and wifi working. I have done extensive downloads and update over the wifi with no light activity.

tlcstat
Toshiba NB505-N508

---

### Post by wirednuke83 on 2011-02-19
Interesting... in either case I haven't been able to get it to recognize any wireless networks.

---

### Post by Vansch76 on 2011-06-20
Hi tlc

did you ever find a solution to your wireless being off or on all the time?

I have a toshiba netbook also, 305 model.

I want to be able to turn off the radio when Im not using wifi.
mine also uses the fn+f8 keystroke to enable wireless.

however Ubuntu does not see the keystrokes. 

I have tried 10.04, 10.10, and now running 11.04.

Thanks

Vanessa

---

### Post by f37u5g0d on 2011-08-15
sudo rfkill list

make sure nothing is blocked.  Look at man rfkill to learn how to unblock things.

---

