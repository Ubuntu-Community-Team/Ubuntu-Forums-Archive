---
title: "Trouble installing Belkin FS06020 wireless adapter"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by hoekstbj on 2008-12-06
I'm new to Ubuntu and been trying to install my wireless Belkin FS06020 card. I've tried Ndiswrapper and no succcess. I've been searching all over the internet. I found this article on the internet. 

I have been successful with everything except for the network configuration script. I'm running Interprid and cannot find the sysconfig folder under the etc folder. 

Since I haven't added a new script for my wireless card could this be the problem? 

" The Linux networking subsystem uses configuration scripts in /etc/sysconfig/network OR /etc/sysconfig/network-scripts, (depending on your distribution) with names that start with "ifcfg-". The script for the new wireless card will be "ifcfg-wlan0". Create this file with the following contents: 

	DEVICE=wlan0
	NAME=wlan0
	BOOTPROTO=dhcp
	ONBOOT=yes

" 



The Belkin F5D6020 version 3 is a PCMCIA (32-bit CardBus) wireless 802.11b network interface card that uses the Realtek RTL8180L Chipset. As with many PC manufacturers, Belkin often makes significant changes the internal hardware of a device without changing the model number and/or outward appearance of the card. Thankfully, Belkin usually lists version numbers on the packaging (oddly as "Ver. 3000"). Note that the version 3 card described in this document uses a different chipset than other versions of this card. Version 2 uses the Atmel chipset (see atmelwlandriver.sourceforge.net). The unversioned release uses the Prism 2, 2.5 and 3 chipsets (see [www.goonda.org/wireless/prism2/](www.goonda.org/wireless/prism2/)). To find chipsets used in other cards, see this list of WLAN cards. 

Personally, I prefer ndiswrapper over linux-wlan. Although ndiswrapper does not provide rfmon support that can be used with kismet or airsnort, it does permit iwlist scans, which linux-wlan does not. Ndiswrapper also does not use cryptic specialized configuration files line linux-wlan 

Verify Card: Verify that you have the correct card. Insert the card in the PCMCIA slot. The listing from "cat /proc/pci" should contain: 

	Bus  7, device   0, function  0:
	  Ethernet controller: PCI device 1799:6020 (rev 32).
	  IRQ 11.
	  Master Capable.  No bursts.  Min Gnt=32.Max Lat=64.
	  I/O at 0x4c00 [0x4cff].
	  Non-prefetchable 32 bit memory at 0x21000000 [0x210001ff].

The listing for "/sbin/lspci - v" should contain: 

	07:00.0 Ethernet controller: Belkin: Unknown device 6020 (rev 20)
	        Subsystem: Belkin: Unknown device 6020
	        Flags: medium devsel, IRQ 11
	        I/O ports at 4c00 [size=256]
	        Memory at 21000000 (32-bit, non-prefetchable) [size=512]
	        Capabilities: [50] Power Management version 2

The listing for "/sbin/cardctl ident" should contain: 

	Socket 0:
	  product info: "Realtek", "Rtl8180"
	  manfid: 0x0000, 0x024c
	  function: 6 (network)

NDISWRAPPER: For reasons listed below, I use a Windoze driver for this card with NDISWRAPPER an open source project that implements the Network Driver Interface Specification (NDIS), a standard API that provides a standardized programming interface for network interface cards that is used by Windoze. 

Download the most current version of NDISWRAPPER from ndiswrapper.sourceforge.net, untar, make and install it. 

	tar -zxvf ndiswrapper-0.10.tar.gz
	cd ndiswrapper-0.10
	make
	make install

Network Configuration Script: The Linux networking subsystem uses configuration scripts in /etc/sysconfig/network OR /etc/sysconfig/network-scripts, (depending on your distribution) with names that start with "ifcfg-". The script for the new wireless card will be "ifcfg-wlan0". Create this file with the following contents: 

	DEVICE=wlan0
	NAME=wlan0
	BOOTPROTO=dhcp
	ONBOOT=yes

This script assumes that you are connecting to an existing wireless network that assigns IP addresses with DHCP and does not use any kind of encryption (i.e. managed mode). If you are setting up a private home network, you should consult a networking How-To (such as this) for an appropriate config script. 

Realtek Drivers: Download the Windoze XP driver for the RTL8180L from [http://www.realtek.com.tw](http://www.realtek.com.tw). For reasons listed below, you probably won't want to try to use either the Windoze drivers provided by Belkin or the native Linux drivers provided by Realtek. Unzip the .zip file and copy the driver files into a new system directory: 

	unzip ndis5x-8180(170).zip
	mkdir /usr/local/share/belkin
	cp NET8180.INF rtl8180.sys /usr/local/share/belkin

Modify the .inf file: The driver information file NET8180.INF contains Realtek vendor and device codes that need to be replaced with the Belkin codes. Edit NET8180.INF with the text editor of your choice and replace all occurances of "VEN_10EC&DEV_8180" with "VEN_1799&DEV_6020". 

Install the driver with NDISWRAPPER: NDISWRAPPER comes with both a kernel module and an administrative tool named ndiswrapper. Install the driver information file: 

	/usr/sbin/ndiswrapper -i /usr/local/share/belkin/NET8180.INF
	/usr/sbin/ndiswrapper -l

ndiswrapper -l should list the card as installed and present. Load the module. 

	modprobe ndiswrapper

Verify Network: Assuming you are near an access point, modprobing the driver module should connect to the network and activate the wlan0 interface. You can verify this with 

	/sbin/ifconfig

Daily Operation: Although ndiswrapper -m will modify the /etc/modules.conf file to load the driver on demand, I have not had success with it. Which actually works out for the best, since wireless security is a joke and you probably don't want to be leave an open wireless connection when it is not needed. 

However, this requires you to modprobe ndiswrapper whenever you want to use the wireless connection. I have had problems with the interface not coming up, but this is solved by unloading the module (rmmod ndiswrapper) and reloading it (modprobe ndiswrapper). 

Problems With Other Drivers 

Orinoco Driver: I initially purchased the Belkin card because it was listed on the Linux PCMCIA site as supported by the orinoco_cs driver that comes with most modern distributions. However, orinoco_cs only supports version 1 of this card, not the version 3 card I purchased, so modprobe orinoco_cs does nothing. 

Belkin Drivers: The card does come with drivers on a CD (Bel6020.inf and Bel6020.sys), but these drivers caused my keyboard to behave eratically with long delays between the time a key was pressed and when it was displayed. Perhaps an interrupt conflict of some kind. 

Realtek Linux Drivers: Realtek provides Linux drivers for the RTL8180L chip used in the Belkin F5D6020 V.3. The tarball includes both C code for the interface as well as a precompiled proprietary object code file (priv_part.o). The standard Fedora Core 1 kernel is compiled with CONFIG_MODVERSIONS to restrict modules compiled for a different kernel versions from accidentally loaded. The proprietary object module was NOT compiled with modversioning, so loading (modprobe) the driver module will fail and depmod -e will give numerous unresolved symbols: 

	/lib/modules/2.4.22-1.2115.nptl/kernel/drivers/net/wireless/rtl8180_24x.o: 
		unresolved symbol info
	depmod:         eth_type_trans
	depmod:         alloc_skb
	depmod:         pci_register_driver

For more information on modversions, see the Linux Kernel Module Guide. 

For those without kernel modversion problems, you might try the linux module: 

Download the Linux driver for the RTL8180L from Realtek.com.tw. Make sure to chose the appropriate kernel version, usually Linux kernel 2.4.20 (gcc version 3.2.2). Unzip the file. 

As with the Windoze driver, you will need to modify the code to reflect the Vendor/Device number for the Belkin card rather than the Realtek card. Edit r8180_pci_init.c, find the following line and change it to this: 

	static struct pci_device_id rtl8180_pci_id_tbl[] = {
	// { 0x10EC, 0x8180 /*0x8139*/, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 },
	{ 0x1799, 0x6020 /*0x8139*/, PCI_ANY_ID, PCI_ANY_ID, 0, 0, 0 },
	{0,},

You should them be able to make install 

The Realtek driver uses scripts that are included with the driver for bringing the interface up/down: wlanup and wlandown 


Hope someone can help thanks

---

