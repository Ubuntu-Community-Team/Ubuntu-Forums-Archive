---
title: "Wireless problems."
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by whitecrow on 2010-12-30
I am having much the same problem although mine would be better termed wireless FAILED after reboot since it has never worked again after my first reboot.  I installed the Belkin F7D2101 usb wireless adapter on Ubuntu 10.10 using ndiswrapper and the Win XP driver.  The ndiswrapper website said this was the driver to use for the adapter's chipset. The adapter was immediately recognized after installation and I was able to connect wirelessly, albeit at only 79% signal strength from two feet away from the router.  After my first reboot, it never worked again. Several additional reboots did not solve the problem. 

lshw -c network shows the network disabled as follows:

 *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 94:44:52:b6:e1:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

iwlist scan as follows:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

I uninstalled the driver and reinstalled it.  No change.  The adapter never worked again.  

I did not blacklist any drivers because I could not find any conflicts with the driver I was using.  I edited files to have ndiswrapper start at boot.  I also followed exactly the instructions for install found for this particular adapter in the formum.  No help.  

I saw something in the forum indicating that my kernal...ending in 24...might be broken.  I restarted and loaded another kernal.  No help.  Will this particular adapter just not work with 10.10?  I am updating my daughter's college computer.  She has been all the way through with Ubuntu and won't know how to use Windows XP if I have to use that...:(

---

### Post by whitecrow on 2010-12-30
I apologize if I put my post in someone else's thread.  I thought that was the way to do it. This time, out of convenience, I'll stay here, tho.

I have only two kernals available:  The default generic is 2.6.35.24.  The other generic is 2.6.35.22.  I am booted into 22.  

The results of lspci -v:

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
	Subsystem: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel modules: shpchp

00:08.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at 40000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
	Subsystem: ADMtek Device 0574
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d000 [size=256]
	Memory at ed020000 (32-bit, non-prefetchable) [size=1K]
	[virtual] Expansion ROM at 40020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: tulip
	Kernel modules: tulip

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at ed021000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
	Subsystem: VIA Technologies, Inc. VT8235 ISA Bridge
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: i2c-viapro, via-ircc

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Foxconn International, Inc. Device 0c18
	Flags: bus master, medium devsel, latency 32, IRQ 20
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at e000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: Foxconn International, Inc. Device 0c18
	Flags: medium devsel, IRQ 22
	I/O ports at e400 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
	Subsystem: Foxconn International, Inc. Device 0c18
	Flags: bus master, medium devsel, latency 32, IRQ 23
	I/O ports at e800 [size=256]
	Memory at ed022000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine

---

### Post by PatchesTheCaveman on 2010-12-30
Do you use a USB dongle for wireless?  That's not showing that you have an internal wireless card.

To get the newest working kernel and to get rid of the busted kernel, run these commands:
```
sudo apt-get remove linux-image-2.6.35-24-generic
sudo apt-get install 2.6.35-23-generic
```

Reboot to get the new kernel.  You shouldn't have to do any special but you can check the GRUB menu just in case.

After you do that, run
```
sudo lsusb
``` so I can check out your wireless.

---

### Post by whitecrow on 2010-12-30
It's a Belkin usb wireless adapter.  I suppose it's a dongle.  

I deleted the 24 kernal and replaced it with 23 and booted into 23 pae with no problem.  The results of sudo lsusb:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:845a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by PatchesTheCaveman on 2010-12-30
Do you know the model #?

---

### Post by whitecrow on 2010-12-30
Belkin F7D2101, chipset RTL8192SU. The computer itself is home made.  AMD board.

---

### Post by PatchesTheCaveman on 2010-12-30
Okay, now run:
```
lsmod
```

and copy/paste and then run:
```
dmesg | grep -i ndiswrapper
```

---

### Post by PatchesTheCaveman on 2010-12-30
Actually, I found a better solution for you.  In August they added support for your wireless adapter to the Linux kernel.  Built-in support always works much better than using ndiswrapper.

To install that driver, you must first completely disable ndiswrapper.  To do so, run this command from the terminal:
```
sudo bash -c "echo blacklist ndiswrapper >> /etc/modprobe.d/blacklist.conf"
```

Next, you must plug into an Ethernet connection to get Internet access to download the new driver.  To download and install it, run these commands:
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

After that, reboot.  Your wireless USB adapter should start working with the kernel driver.  Let me know if you have any trouble.

---

### Post by whitecrow on 2010-12-31
You have been very dedicated and helpful.  I have been an Ubuntu user since 2005 and have never found a piece of hardware that I could not eventually make work.  But lshw still shows that my wireless network connection is disabled.  

I have re-seated the adapter and moved it to another usb port.  I rebooted twice.  Even after blacklisting ndiswrapper, it showed that the adapter was using the old driver, so I removed it and rebooted again.  Still no luck. Something is wrong here and I have no idea what it is. 

I'm a computer tech in my spare time and I have installed Ubuntu countless times on all kinds of hardware.  But I always tell my paying customers that installations of this operating system are restricted to desktops with wired connections running few peripherals. Looks like I've been proven right again.  

I'm on vacation and have to move all these computers out of my workshop.  Is there one thing more I should try or should I just install an old copy of Windows XP on this machine to move it out?  As you were helping me work with this machine, I plugged the wireless usb adapter into a box running Windows Vista and even without installing the software on the disk, it picked up my wireless signal at 100%.

I'll try one more time if there's anything you know left to try...

---

### Post by PatchesTheCaveman on 2010-12-31
The r8192u_usb you installed when you installed the backported kernel drivers did not work?  That's surprising.  The drivers built into the Linux kernel generally work pretty well.

Try running this to force the kernel to load the driver:
```
sudo modprobe r8192u_usb
```

After you do that, run this command to show any errors the driver might be experiencing:
```
dmesg | grep -i r8192
```

Copy and paste them in a message here and I'll see what I can do.

Part of the problem is the Ubuntu philosophy.  While they strive for ease of use they generally get behind on the newest technology.  Distributions like Fedora follow upstream code much more closely and get newer features and hardware support faster, at the cost of usability.

---

### Post by PatchesTheCaveman on 2010-12-31
I was helping another user and I discovered what might be the problem.  I think Ubuntu only provides a updated driver package for the broken kernel.  Try doing this instead:
```
sudo apt-get install build-essentials
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-12-26.tar.bz2
tar -jxf compat-wireless-2010-12-26.tar.bz2
cd compat-wireless-2010-12-26
make
sudo make install
sudo make unload
sudo modprobe r8192u_usb
```

---

### Post by whitecrow on 2010-12-31
Here are the results (all the errors produced) of make:

jessica@jessica-linux:~/compat-wireless-2010-12-26$ make
make -C /lib/modules/2.6.35-24-generic/build M=/home/jessica/compat-wireless-2010-12-26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.o
/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.c: In function ‘_rtl_init_deferred_work’:
/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.c:229: error: implicit declaration of function ‘alloc_workqueue’
/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.c:229: warning: assignment makes pointer from integer without a cast
make[4]: *** [/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.o] Error 1
make[3]: *** [/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi] Error 2
make[2]: *** [/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/jessica/compat-wireless-2010-12-26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [modules] Error 2

Here are the results of sudo make install:

jessica@jessica-linux:~/compat-wireless-2010-12-26$ sudo make install

Your old wireless subsystem modules were left intact:

updates/compat-wireless-2.6.36/mac80211.ko
updates/compat-wireless-2.6.36/cfg80211.ko
updates/compat-wireless-2.6.36/lib80211.ko
updates/compat-wireless-2.6.36/adm8211.ko
updates/compat-wireless-2.6.36/ar9170usb.ko
updates/compat-wireless-2.6.36/at76c50x-usb.ko
updates/compat-wireless-2.6.36/ath.ko
updates/compat-wireless-2.6.36/ath5k.ko
updates/compat-wireless-2.6.36/ath9k.ko
updates/compat-wireless-2.6.36/ath9k_htc.ko
updates/compat-wireless-2.6.36/b43.ko
updates/compat-wireless-2.6.36/b43legacy.ko
updates/compat-wireless-2.6.36/b44.ko
updates/compat-wireless-2.6.36/cdc_ether.ko
updates/compat-wireless-2.6.36/eeprom_93cx6.ko
updates/compat-wireless-2.6.36/ipw2100.ko
updates/compat-wireless-2.6.36/ipw2200.ko
updates/compat-wireless-2.6.36/iwl3945.ko
updates/compat-wireless-2.6.36/iwlagn.ko
updates/compat-wireless-2.6.36/iwlcore.ko
updates/compat-wireless-2.6.36/iwmc3200wifi.ko
updates/compat-wireless-2.6.36/lib80211_crypt_ccmp.ko
updates/compat-wireless-2.6.36/lib80211_crypt_tkip.ko
updates/compat-wireless-2.6.36/lib80211_crypt_wep.ko
updates/compat-wireless-2.6.36/libertas.ko
updates/compat-wireless-2.6.36/libertas_cs.ko
updates/compat-wireless-2.6.36/libertas_sdio.ko
updates/compat-wireless-2.6.36/libertas_spi.ko
updates/compat-wireless-2.6.36/libertas_tf.ko
updates/compat-wireless-2.6.36/libertas_tf_usb.ko
updates/compat-wireless-2.6.36/libipw.ko
updates/compat-wireless-2.6.36/mac80211_hwsim.ko
updates/compat-wireless-2.6.36/mwl8k.ko
updates/compat-wireless-2.6.36/orinoco_cs.ko
updates/compat-wireless-2.6.36/orinoco_nortel.ko
updates/compat-wireless-2.6.36/orinoco_pci.ko
updates/compat-wireless-2.6.36/orinoco_plx.ko
updates/compat-wireless-2.6.36/orinoco_usb.ko
updates/compat-wireless-2.6.36/orinoco.ko
updates/compat-wireless-2.6.36/p54common.ko
updates/compat-wireless-2.6.36/p54pci.ko
updates/compat-wireless-2.6.36/p54spi.ko
updates/compat-wireless-2.6.36/p54usb.ko
updates/compat-wireless-2.6.36/rndis_host.ko
updates/compat-wireless-2.6.36/rndis_wlan.ko
updates/compat-wireless-2.6.36/rt2400pci.ko
updates/compat-wireless-2.6.36/rt2500pci.ko
updates/compat-wireless-2.6.36/rt2500usb.ko
updates/compat-wireless-2.6.36/rt2800pci.ko
updates/compat-wireless-2.6.36/rt2800usb.ko
updates/compat-wireless-2.6.36/rt2x00lib.ko
updates/compat-wireless-2.6.36/rt2x00pci.ko
updates/compat-wireless-2.6.36/rt2x00usb.ko
updates/compat-wireless-2.6.36/rt61pci.ko
updates/compat-wireless-2.6.36/rt73usb.ko
updates/compat-wireless-2.6.36/rtl8180.ko
updates/compat-wireless-2.6.36/rtl8187.ko
updates/compat-wireless-2.6.36/spectrum_cs.ko
updates/compat-wireless-2.6.36/ssb.ko
updates/compat-wireless-2.6.36/usb8xxx.ko
updates/compat-wireless-2.6.36/usbnet.ko
updates/compat-wireless-2.6.36/wl1251.ko
updates/compat-wireless-2.6.36/zd1211rw.ko

Your old ethernet subsystem modules are left intact:

updates/compat-wireless-2.6.36/atl1.ko
updates/compat-wireless-2.6.36/atl2.ko
updates/compat-wireless-2.6.36/atl1e.ko
updates/compat-wireless-2.6.36/atl1c.ko

Your old bluetooth subsystem modules were left intact:

updates/compat-wireless-2.6.36/ath3k.ko
updates/compat-wireless-2.6.36/bcm203x.ko
updates/compat-wireless-2.6.36/bluecard_cs.ko
updates/compat-wireless-2.6.36/bluetooth.ko
updates/compat-wireless-2.6.36/bnep.ko
updates/compat-wireless-2.6.36/bpa10x.ko
updates/compat-wireless-2.6.36/bt3c_cs.ko
updates/compat-wireless-2.6.36/btmrvl.ko
updates/compat-wireless-2.6.36/btmrvl_sdio.ko
updates/compat-wireless-2.6.36/btsdio.ko
updates/compat-wireless-2.6.36/btusb.ko
updates/compat-wireless-2.6.36/btuart_cs.ko
updates/compat-wireless-2.6.36/cmtp.ko
updates/compat-wireless-2.6.36/dtl1_cs.ko
updates/compat-wireless-2.6.36/hidp.ko
updates/compat-wireless-2.6.36/hci_vhci.ko
updates/compat-wireless-2.6.36/hci_uart.ko
updates/compat-wireless-2.6.36/l2cap.ko
updates/compat-wireless-2.6.36/rfcomm.ko
updates/compat-wireless-2.6.36/sco.ko

make -C /lib/modules/2.6.35-24-generic/build M=/home/jessica/compat-wireless-2010-12-26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.o
/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.c: In function ‘_rtl_init_deferred_work’:
/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.c:229: error: implicit declaration of function ‘alloc_workqueue’
/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.c:229: warning: assignment makes pointer from integer without a cast
make[4]: *** [/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi/base.o] Error 1
make[3]: *** [/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless/rtlwifi] Error 2
make[2]: *** [/home/jessica/compat-wireless-2010-12-26/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/jessica/compat-wireless-2010-12-26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [modules] Error 2

sudo make unload:

jessica@jessica-linux:~/compat-wireless-2010-12-26$ sudo make unload
Stoping bluetooth service..
 * bluetooth is not running
Unloading eeprom_93cx6...
FATAL: Module eeprom_93cx6 is in use.
jessica@jessica-linux:~/compat-wireless-2010-12-26$ 

modprobe:

jessica@jessica-linux:~/compat-wireless-2010-12-26$ sudo modprobe r8192u_usb
FATAL: Error inserting r8192u_usb (/lib/modules/2.6.35-24-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko): Device or resource busy
jessica@jessica-linux:~/compat-wireless-2010-12-26$ 

finally, I have been warned:

jessica@jessica-linux:~/compat-wireless-2010-12-26$ dmesg | grep -i r8192
[   13.595756] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  176.109649] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[  176.133255] Modules linked in: r8192u_usb(C+) binfmt_misc snd_via82xx gameport snd_ac97_codec ac97_bus nouveau snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_midi snd_rawmidi ttm snd_seq_midi_event drm_kms_helper snd_seq ppdev snd_timer i2c_viapro via_ircc r8192s_usb(C) snd_seq_device ndiswrapper drm irda via_agp parport_pc psmouse snd eeprom_93cx6 serio_raw shpchp soundcore crc_ccitt lp i2c_algo_bit agpgart parport pata_via via_rhine mii floppy tulip
[  176.133403]  [<f9b601ae>] ieee80211_debug_init+0x25/0x90 [r8192u_usb]
[  176.133420]  [<f9b6000c>] rtl8192_usb_module_init+0xc/0x110 [r8192u_usb]
[  176.133442]  [<f9b60000>] ? rtl8192_usb_module_init+0x0/0x110 [r8192u_usb]
[  176.133521] Modules linked in: r8192u_usb(C+) binfmt_misc snd_via82xx gameport snd_ac97_codec ac97_bus nouveau snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_midi snd_rawmidi ttm snd_seq_midi_event drm_kms_helper snd_seq ppdev snd_timer i2c_viapro via_ircc r8192s_usb(C) snd_seq_device ndiswrapper drm irda via_agp parport_pc psmouse snd eeprom_93cx6 serio_raw shpchp soundcore crc_ccitt lp i2c_algo_bit agpgart parport pata_via via_rhine mii floppy tulip
[  176.133620]  [<f9b1a3c9>] rtl8192_proc_module_init+0x29/0x40 [r8192u_usb]
[  176.133636]  [<f9b600f3>] rtl8192_usb_module_init+0xf3/0x110 [r8192u_usb]
[  176.133657]  [<f9b60000>] ? rtl8192_usb_module_init+0x0/0x110 [r8192u_usb]
[ 1091.294694] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 1091.343850] Modules linked in: r8192u_usb(C+) binfmt_misc snd_via82xx gameport snd_ac97_codec ac97_bus nouveau snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_midi snd_rawmidi ttm snd_seq_midi_event drm_kms_helper snd_seq ppdev snd_timer i2c_viapro via_ircc r8192s_usb(C) snd_seq_device ndiswrapper drm irda via_agp parport_pc psmouse snd eeprom_93cx6 serio_raw shpchp soundcore crc_ccitt lp i2c_algo_bit agpgart parport pata_via via_rhine mii floppy tulip
[ 1091.344001]  [<fb1a81ae>] ieee80211_debug_init+0x25/0x90 [r8192u_usb]
[ 1091.344076]  [<fb1a800c>] rtl8192_usb_module_init+0xc/0x110 [r8192u_usb]
[ 1091.344100]  [<fb1a8000>] ? rtl8192_usb_module_init+0x0/0x110 [r8192u_usb]
[ 1091.346484] Modules linked in: r8192u_usb(C+) binfmt_misc snd_via82xx gameport snd_ac97_codec ac97_bus nouveau snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_midi snd_rawmidi ttm snd_seq_midi_event drm_kms_helper snd_seq ppdev snd_timer i2c_viapro via_ircc r8192s_usb(C) snd_seq_device ndiswrapper drm irda via_agp parport_pc psmouse snd eeprom_93cx6 serio_raw shpchp soundcore crc_ccitt lp i2c_algo_bit agpgart parport pata_via via_rhine mii floppy tulip
[ 1091.346602]  [<fb1623c9>] rtl8192_proc_module_init+0x29/0x40 [r8192u_usb]
[ 1091.346619]  [<fb1a80f3>] rtl8192_usb_module_init+0xf3/0x110 [r8192u_usb]
[ 1091.346641]  [<fb1a8000>] ? rtl8192_usb_module_init+0x0/0x110 [r8192u_usb]

---

### Post by PatchesTheCaveman on 2010-12-31
cfd_man:  You're welcome!  Glad to hear everything's working now.

whitecrow:  Sorry about that! I got the first line wrong which screwed up the whole thing.  It should have been:
```
sudo apt-get install build-essential
```.

After you do that, *cd* back into the compat-wireless directory and run
```
make clean
```
and then run
```
make
``` again.

From there, follow the rest of the original instructions.

---

### Post by whitecrow on 2010-12-31
Patches, you were incredibly helpful, which is why I love this forum.  I solved my problem by exchanging the Belkin USB wireless adapter for a PCI wireless adapter known to work.  I don't want something that doesn't work with Ubuntu and I don't think the USB thing was quite right, even if it did work okay in WinXP.  

Reformatted the hard drive and reinstalled the stable Ubuntu kernal with my new PCI device and I am cooking with gas!

Thanks for all your help!

WC

---

