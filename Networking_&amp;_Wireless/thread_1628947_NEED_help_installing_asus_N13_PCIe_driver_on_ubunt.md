---
title: "NEED help installing asus N13 PCIe driver on ubuntu"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by alquh on 2010-11-23
Hi I'm complete ubuntu beginner and have experience with linux commmand-lines. I would need help to install the linux asus N13 PCIe Wlan driver on ubuntu 10.10. I extracted  from the provided CD but I don't know how to make the suggested changes in the installation decription ... 
thats what I have in the build instruction: "   	 	 	 	pre { font-family: "Liberation Serif"; }p { margin-bottom: 0.21cm; }  Build Instructions:   ====================  1> $tar -xvzf RT2860_Linux_STA_x.x.x.x.tgz     go to "./RT2860_Linux_STA_x.x.x.x" directory.      2> In Makefile 	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX" 	 define the linux kernel source include file path LINUX_SRC 	 modify to meet your need.  3> In os/linux/config.mk  	define the GCC and LD of the target machine 	define the compiler flags CFLAGS 	modify to meet your need. 	** Build for being controlled by NetworkManager or wpa_supplicant wext functions 	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. 	   => #>cd wpa_supplicant-x.x 	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d 	** Build for being controlled by WpaSupplicant with Ralink Driver 	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'. 	   => #>cd wpa_supplicant-0.5.7 	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d  4> $make 	# compile driver source code 	# To fix "error: too few arguments to function &#65533;&#65533;iwe_stream_add_event" 	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c  5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat      6> load driver, go to "os/linux/" directory.     #[kernel 2.4]     #    $/sbin/insmod rt2860sta.o     #    $/sbin/ifconfig ra0 inet YOUR_IP up              #[kernel 2.6]     #    $/sbin/insmod rt2860sta.ko     #    $/sbin/ifconfig ra0 inet YOUR_IP up  7> unload driver         $/sbin/ifconfig ra0 down 	$/sbin/rmmod rt2860sta"
is there someone who can explain me what to do step by step?
I would be glad for any help
alquh

ps: this is what i get with the lspci command: alquh@alquh:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
03:00.0 Network controller: RaLink RT2860
05:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
05:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

the Wlan card with the chipset RaLink RT2860 seems at least to be recognized .. but is not installed

---

### Post by uncaspi on 2010-11-23
Have you tried the native driver shipped with 10.10?
Will you please post the content of
sudo lshw -C network

---

### Post by alquh on 2010-11-23
HI uncaspi, 
I get the "Segmentation fault"

---

### Post by uncaspi on 2010-11-23
Hi.

We'll see if it listed : Please post sudu lspci -nn
and sudo lsusb

---

