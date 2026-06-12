---
title: "Can not get my wireless to work"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by dmies73 on 2009-05-08
I started with an install of 8.04, no joy there,, so thought maybe a new release would work better, so i installed Ubuntu 8.10 tonight still no joy on getting my network to work.. I have tried following the tech options from others post but I am so friggen lost it is not funny..  here is the answers to the  wireless problem questions and data..

I need this computer up and running before I have to take a road trip... and with my job that can be in two hours,, desperate for help PLEASE>>>

1. Machine Brand  
	HP Pavilion zv6000
2.Wireless
	lspci
	
	03:02.0 Network controller: Broadcom Corporation bcm4318 [Air Force One 54g]
	 802.11g Wireless LAN Controller (rev 02)
3. Interface
	ifconfig
		Link encap:Ethernet HWaddr 00:14:a5:63:64:bb
		BROADCAST MULTICAST  MTU: 1500 Metrid:1
		RX packets:0 errors:0 Dropped:0 overruns:0 fram:0
		TX packets:0 errors:0 Dropped:0 overruns:0 carrier:0
		collision:0 txqueuelen:1000
		RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
	iwconfig
		wlan0 IEEE 802.11bg EESID: ""
		Mode: Managed Frequency:2.412 ghz  Access Point: Not-Associated
		TX-Power= 0dBm
		Retry min limit:7  RTS thr:off  Fragment thr=2352 B
		PowerManagement:off
		Link Quality:0  Signal level:0 Noise level:0
		Rx invalid nwid:0 Rx invalid crypt:0 Rs invalid frag:0
		Tx excessive retries:0  Invalid misc:0  Missed beacon:0

4. Modules
	lsmod
		b43 		131356 	0
		rfkill 		17176	2 rfkill_input,b43
		mac80211 	216820	1 b43
		led_class	12164	1 b43
		input_polldev	11912	1 b43
		ssb		40580	1 b43

5. Kernel Boot messages
	dmesg
		[    5.288042] b43-pci-bridge 0000:03:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   27.050240] b43-phy0: Broadcom 4318 WLAN found
[   47.265554] input: b43-phy0 as /devices/virtual/input/input9
[   47.356098] firmware: requesting b43/ucode5.fw
[   47.390955] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   47.390971] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[   47.428548] input: b43-phy0 as /devices/virtual/input/input10
[   47.492060] firmware: requesting b43/ucode5.fw
[   47.496988] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   47.496998] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  635.951706] b43-phy1: Broadcom 4318 WLAN found
[  640.171729] input: b43-phy1 as /devices/virtual/input/input11
[  640.264097] firmware: requesting b43/ucode5.fw
[  640.269647] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  640.269664] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  640.310202] input: b43-phy1 as /devices/virtual/input/input12
[  640.372059] firmware: requesting b43/ucode5.fw
[  640.377696] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  640.377713] b43-phy1 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  665.949034] b43-phy2: Broadcom 4318 WLAN found
[  667.087519] b43-phy3: Broadcom 4318 WLAN found
[  671.236184] input: b43-phy3 as /devices/virtual/input/input13
[  671.328070] firmware: requesting b43/ucode5.fw
[  671.335925] b43-phy3 ERROR: Firmware file "b43/ucode5.fw" not found
[  671.335941] b43-phy3 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  671.378396] input: b43-phy3 as /devices/virtual/input/input14
[  671.440062] firmware: requesting b43/ucode5.fw
[  671.445132] b43-phy3 ERROR: Firmware file "b43/ucode5.fw" not found
[  671.445153] b43-phy3 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  681.625410] b43-phy4: Broadcom 4318 WLAN found
[  685.859637] input: b43-phy4 as /devices/virtual/input/input15
[  685.952075] firmware: requesting b43/ucode5.fw
[  685.956578] b43-phy4 ERROR: Firmware file "b43/ucode5.fw" not found
[  685.956598] b43-phy4 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  686.003752] input: b43-phy4 as /devices/virtual/input/input16
[  686.068062] firmware: requesting b43/ucode5.fw
[  686.073031] b43-phy4 ERROR: Firmware file "b43/ucode5.fw" not found
[  686.073040] b43-phy4 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  777.490865] b43-phy5: Broadcom 4318 WLAN found
[  781.717042] input: b43-phy5 as /devices/virtual/input/input17
[  781.808075] firmware: requesting b43/ucode5.fw
[  781.814870] b43-phy5 ERROR: Firmware file "b43/ucode5.fw" not found
[  781.814886] b43-phy5 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[  781.856959] input: b43-phy5 as /devices/virtual/input/input18
[  781.920062] firmware: requesting b43/ucode5.fw
[  781.925010] b43-phy5 ERROR: Firmware file "b43/ucode5.fw" not found
[  781.925019] b43-phy5 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).


6. Network config
	*-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bd:2d:2a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:cf:a2:f7:00:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:63:64:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
	

7.  Networks
	
	lo	Interface doesn't support scanning
	eth0	Interface doesn't support scanning
	wmaster0 Interface doesn't support scanning
	wlan0	no scan results

8. Ubunto Version
	Ubuntu 8.10

9. Kernel
	2.6.27-7-generic i686

10. Restarting the network
	* Reconfiguring network interfaces

---

### Post by dmies73 on 2009-05-08
After a week and a half of frustration, chatrooms, reinstalls, new systems, new cards,  pulling my hair out..... I got it to work.  this is what I did..  I followed this pages instructions to a tee..

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

and when it was all done it worked...

---

### Post by merkourio on 2009-05-08
Thnx alot for the help!
I had the same problem!

---

### Post by newbuntuxx on 2012-05-29
If you came here from google having the same problem with 12.04, see this:
[http://clusterbleep.net/blog/2012/05/09/ubuntu-12-04-splash-screen-lockup-with-livecd/](http://clusterbleep.net/blog/2012/05/09/ubuntu-12-04-splash-screen-lockup-with-livecd/)

Short version:
To get around the problem and actually install Ubuntu, you’ll have to boot from the LiveCD as before, press F6 at the Install/Memtest/Check CD screen, and add the following to the boot options: b43.blacklist=yes . Then when you continue booting, you’ll be able to login and install.

Once you’ve successfully booted in Ubuntu or Kubuntu, make sure you have a wired Internet connection and issue these commands at the terminal or konsole to install the Broadcom Wifi firmware: sudo apt-get install firmware-b43-installer . Reboot, and everything should work, including your Wifi.

---

### Post by Megaptera on 2012-05-30
Hi newbuntuxx,
Did you notice that this thread is about 3 years old?

---

### Post by nothingspecial on 2012-05-30
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

