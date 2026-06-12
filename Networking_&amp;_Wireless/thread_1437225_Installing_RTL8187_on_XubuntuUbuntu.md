---
title: "Installing RTL8187 on Xubuntu/Ubuntu"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by WASasquatch on 2010-03-23
I'm trying to install my RTL8187 network adapter. It comes with the necessary installation files for Linux Kernal 2.6.x but I am so new to Linux I don't know how to install.

[This thread has the Readme file listed at the bottom.]("http://ubuntuforums.org/showthread.php?t=339314")

Can someone translate the installation part for a newbie? :popcorn:

---

### Post by chili555 on 2010-03-23
The modules rtl8187 and rtl8187se are built in to your kernel. If it's not loading and creating a wireless interface, then something else is wrong. It won't be corrected by installing an ancient 2007 vintage driver. How about posting:```
dmesg | grep 818
lsusb
lspci -nn
```Thanks.

---

### Post by BrianIsNew on 2010-04-17
Hey guys,

I see that this thread has stuck here for a while, but I believe I'm having a similar issue and it seemed a better idea adding to this post than creating a new one.

My issue is not that my computer doesn't seem to be recognizing my wireless adapter, but rather that It doesn't produce any available networks. I know the network is up and usable since my mates can attach to it, and my phone picks it up brilliantly. I'm running a Toshiba laptop with Ubuntu 9.10, if that helps anyone.

To simply post my output to chili555's request:

**brian@olympia:~$ dmesg | grep 818**
[    0.688084] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.741818] pci 0000:00:14.4: PCI bridge, secondary bus 0000:80
[    1.502602] ata2: SATA max UDMA/133 abar m1024@0xd6408000 port 0xd6408180 irq 22
[    1.648183] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.708183] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[   15.899606] rtl8187se: module is from the staging directory, the quality is unknown, you have been warned.
[   15.902763] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[   15.902766] r8180: Initializing module
[   15.902769] r8180: Wireless extensions version 22
[   15.902771] r8180: Initializing proc filesystem
[   15.902816] r8180: Configuring chip resources
[   15.902832] r8180 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.902839] r8180 0000:02:00.0: setting latency timer to 64
[   15.907393] rtl8180_init:Error channel plan! Set to default.
[   15.907397] r8180: Channel plan is 0
[   15.907406] r8180: MAC controller is a RTL8187SE b/g
[   15.907408] r8180: This is a PCI NIC
[   15.909831] r8180: usValue is 0x104
[   15.964370] r8180: EEPROM version 104
[   15.969123] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[   16.051360] r8180: IRQ 16
[   16.052096] r8180: Driver probe completed
[   17.222172] r8180: Bringing up iface
[   17.420710] r8180: Card successfully reset
[   18.157830] r8180: WIRELESS_MODE_G

**brian@olympia:~$ lsusb**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[B]
brian@olympia:~$ lspci -nn[/B]
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics] [1002:9613]
[B]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
[/B]03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

[B]brian@olympia:~$ iwconfig
[/B]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry: on   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
brian@olympia:~$ iwlist scan[/B]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results




Please keep in mind that I am *very* new to Linux in general. Conceptually, I get it, but practically, I'm dead. :?

Let me know if I should provide further information, or please direct me if this has been solved elsewhere.

Thanks!

---

