---
title: "wifi not working on toshiba m645 using ubuntu 11.04"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by gititdone on 2011-05-12
Just bought this toshiba laptop m645-s4114 today @ bestbuy and I installed the ubuntu 11.04 successfully erasing the MS OS on it but later realized my wireless network doesn't work. I have tried and followed everything that was given on some linux ubuntu forums with no avail. Any suggestions pls..

---

### Post by chili555 on 2011-05-12
Details! We need details! Please open a terminal and run and post:```
lspci -nn
```What have you tried so far?

---

### Post by gititdone on 2011-05-12
@chili555 
lspci -nn- this is the output:

cynthia-Satellite-M645:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
06:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0087] (rev 5f)
15:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382] (rev 20)
15:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (rev 20)
15:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383] (rev 20)
15:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384] (rev 20)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
cynthia-Satellite-M645:~$ 

thanks

---

### Post by chili555 on 2011-05-12
> 06:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0087] (rev 5f)Your device works with the module iwlagn. Let's load it and see if there are nay interesting messages:```
sudo modporbe iwlagn
dmesg | grep iwl
```Firmware, I'm guessing.

---

### Post by gititdone on 2011-05-12
@chili555: sorry for the delay 

output for sudo modporbe iwlagn
dmesg | grep iwl

cynthia-Satellite-M645:~$ sudo modporbe iwlagn
[sudo] password for cynthia: 
Sorry, try again.
[sudo] password for cynthia: 
sudo: modporbe: command not found
cynthia-Satellite-M645:~$

---

### Post by chili555 on 2011-05-12
> **gititdone said:**
> @chili555: sorry for the delay 

output for sudo modporbe iwlagn
dmesg | grep iwl

cynthia-Satellite-M645:~$ sudo modporbe iwlagn
[sudo] password for cynthia: 
Sorry, try again.
[sudo] password for cynthia: 
sudo: modporbe: command not found
cynthia-Satellite-M645:~$I'm getting a better grind on these old trifocals! Sorry about that.```
sudo modprobe iwlagn
dmesg | grep iwl
```

---

### Post by gititdone on 2011-05-12
> **chili555 said:**
> I'm getting a better grind on these old trifocals! Sorry about that.```
sudo modprobe iwlagn
dmesg | grep iwl
```

but isn't it the same as the above command i just ran :confused:

---

### Post by gititdone on 2011-05-12
> **chili555 said:**
> I'm getting a better grind on these old trifocals! Sorry about that.```
sudo modprobe iwlagn
dmesg | grep iwl
```

this is the output 

cynthia-Satellite-M645:~$ sudo modprobe iwlagn
[sudo] password for cynthia: 
Sorry, try again.
[sudo] password for cynthia: 
cynthia-Satellite-M645:~$ 

:confused:

---

### Post by gititdone on 2011-05-12
@ chili555

let me check the bios to see if my pci or whatever that is has been disabled and i'll get back to you again sorry to bother

---

### Post by chili555 on 2011-05-12
No need for  :confused:

That simply means the command was executed as requested with no errors or warnings. What we are really interest in is the results of the next command:```
dmesg | grep iwl
```Please.

---

### Post by gititdone on 2011-05-12
> **chili555 said:**
> No need for  :confused:

That simply means the command was executed as requested with no errors or warnings. What we are really interest in is the results of the next command:```
dmesg | grep iwl
```Please.

this is the output:

cynthia-Satellite-M645:~$ dmesg | grep iwl
[   12.174232] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.174235] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.174346] iwlagn 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.174376] iwlagn 0000:06:00.0: setting latency timer to 64
[   12.174449] iwlagn 0000:06:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[   12.182815] iwlagn 0000:06:00.0: device EEPROM VER=0x554, CALIB=0x6
[   12.182818] iwlagn 0000:06:00.0: Device SKU: 0Xb
[   12.182871] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.183104] iwlagn 0000:06:00.0: irq 42 for MSI/MSI-X
[   12.233429] iwlagn 0000:06:00.0: loaded firmware version 41.28.5.1 build 33926
[   12.255874] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
cynthia-Satellite-M645:~$

---

### Post by chili555 on 2011-05-12
dmesg looks perfect. Now, how about:```
rfkill list all
dmesg | grep wlan
```Thanks.

---

### Post by gititdone on 2011-05-12
cynthia-Satellite-M645:~$ rfkill list all
0: i2400m-usb:1-1.6:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
cynthia-Satellite-M645:~$ dmesg | grep wlan

thank you

---

### Post by chili555 on 2011-05-12
> 1: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]This suggests that the hardware switch or key combination has the wireless switched off. Is this possible? Can you manipulate the switch and see if you can re-run rfkill list all and get Hard blocked to 'no'? Then your wireless ought to work.

---

### Post by gititdone on 2011-05-12
thanks i'll try will let you know

---

### Post by gititdone on 2011-05-12
@chili555 

DID YOU DO SOMETHING ON MY COMPUTER are you kidding me sleepless nights and i'm worried how could i drive to pick up my kids because i'm tired of this computer since yesterday. THANK YOU SO MUCH my wireless is working and i can't even remember if i did touch or press on something thank you again chili555

---

### Post by gititdone on 2011-05-12
@ chili555

thank you again for not letting this go. i was thinking of sending this back to bestbuy but then how about the warranty coz i messed up with the window 7.

---

### Post by gititdone on 2011-05-12
Solved

---

