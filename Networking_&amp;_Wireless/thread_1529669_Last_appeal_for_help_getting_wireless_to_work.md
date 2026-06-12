---
title: "Last appeal for help getting wireless to work"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by phil7784 on 2010-07-12
A week ago I posted a question re the fact that my wireless home network is not recognized by my network card (RealTek RTL8190 mini PCI). The post was as follows: "I am using a new computer with Windows 7 , Athlon quad core 2.60 64 bit, 8GB RAM. Internet conection works fine with ethernet but ubuntu does not see my wireless network. card (RealTek RTL 8190 ID: 10ec:8190). Have searched this forum but unable to come up with a fix. I was looking for windows XP drivers to use Ndiswrapper but could not find a list of .inf files. My network is OK and works perfectly in windows and with my 2 laptops. Can anyone point me in the right direction? Additional info: install was done within Windows using WUBI to a separate partition on my HDD. I am new to this and thouroughly confused as to the procedure for installing the drivers if they are in fact available."
  I am very frustrated in that I would like to use Ubuntu 10.04 but it is useless without internet connectability. I am new to linux and do not understand where to get the appropriate drivers or how to install them. I wish someone would answer this post and either give me a clue what to do or just say "give up" and uninstall ubunutu.

---

### Post by wookieshaver on 2010-07-12
To help you find the wireless drivers for ndiswrapper or another method I need the info on the wireless card for your unit. You can get this info by going to a console prompt and typing iwconfig and hitting enter (within Ubuntu of course). Also an output from this command "lspci" would be handy as well.
 
If it does output as some variation of RTL 8190, try this: download the 8192E Winxp drivers and extract them. Use the inf drivers in it to install and use with ndiswrapper. ([http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E))
 
Give it a try and tell me how it goes!

---

### Post by phil7784 on 2010-07-12
Thanks for your reply

output:

phil7784@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

phil7784@ubuntu:~$ 
phil7784@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Multimedia controller: Philips Semiconductors Device 7231 (rev aa)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
05:05.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190

The only files I can find at the realtek site are USB drivers such as:
[ftp://WebUser:K4d5wHY@152.104.238.19/cn/wlan/RTL8192U_Win7_Driver_6.1372.0413.2010.zip](ftp://WebUser:K4d5wHY@152.104.238.19/cn/wlan/RTL8192U_Win7_Driver_6.1372.0413.2010.zip)

I also downloaded: [http://ud-pc.com/driver/Realtek/RTL8187SE/rtl8187se_linux_26.1023.1209.2008.tar.gz](http://ud-pc.com/driver/Realtek/RTL8187SE/rtl8187se_linux_26.1023.1209.2008.tar.gz) but I don't know how to use this file. Can't find any .inf files

---

