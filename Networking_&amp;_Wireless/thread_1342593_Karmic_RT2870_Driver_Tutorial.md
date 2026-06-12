---
title: "Karmic RT2870 Driver Tutorial"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by peepingtom on 2009-11-30
[SIZE=6][COLOR="Purple"]**Update for October 2011: This guide was written in 2009, has not been supported in years, and is not a recommended way to deal with this problem.**
[/COLOR]
[/SIZE]

[SIZE=5][COLOR="Purple"] Ubuntu 11.10 "Oneiric Ocelot" no longer includes Ralink's out-of-kernel-tree drivers, instead it distributes drivers developed by the rt2x00 community project.
[/COLOR]
[/SIZE]

[SIZE=4][COLOR="Purple"]**For Those using Ubuntu 11.04 Natty and Lower:** Luckily, someone has outlined how to pass new USB Dev IDs to a compiled kernel module using udev, and it is a MUCH better solution than what I've explained below (recompiling a kernel module).
If you're having an issue with a driver not supporting your device due to a USB Dev ID issue, please see flash63's post here: [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6) [/COLOR]
[/SIZE]
**I no longer support this tutorial because I don't own any Ralink devices to test it on.** It still has some useful info, so i'll leave it up. Good luck!




[SIZE=5]**This tutorial is for USB WiFi Adapters that use the RT2870 or RT3070 chipsets by Ralink.**[/SIZE]

THE CURRENT STATE OF RALINK DRIVERS

There are currently 2 groups developing drivers for Ralink chipsets: Ralink's own team and the community-run rt2x00 project. Rt2x00 drivers work very well, and are distributed with the Linux kernel. Ralink's drivers (such as rt2870sta and rt3070sta) have some ugly code, and at this time are distributed separately from the Linux kernel. These drivers have varying levels of support for different chipsets, and in some cases they would both support a given chip


[SIZE=3]**A Common Problem:**[/SIZE]
[SIZE=2]USB devices report their USB Device IDs, which are used to determine whether a Linux kernel module (driver component) should control a device. Conflicts can occur when more than one module attempts to control a device with a given USB Dev ID. In Ubuntu 9.10, such conflicts exist between the community-written rt2x00 module, and Ralink's rt2870sta and rt3070sta modules. Furthermore, these modules do not detect many devices which they are able to control.[/SIZE]

[SIZE=3]**The Scope of This Guide:**[/SIZE]
[SIZE=2]This guide describes how to “blacklist” modules, to prevent conflicting modules from being concurrently loaded. Additionally, it describes how to modify and compile Ralink's rt2870sta and rt3070sta modules with support for new USB Dev Ids.[/SIZE]

[SIZE=3]**Determining which module you should use:**[/SIZE]
[SIZE=2]If a USB WiFi adapter is automatically detected by rt2870sta, rt3070sta or an rt2x00 module, it has likely been verified to function by that module's developers. **While the rt2x00 driver has some support for rt2870 chipsets, it seems that rt2870 and rt3070 chipsets work best when controlled by Ralink's drivers**. Only one of these modules should be loaded per network adapter.[/SIZE]

To determine which modules control your USB WiFi adapter, insert it and run the following command in terminal ```
lsmod |grep rt
``` rt2870 devices are supported by Ralink's rt2870 driver (module rt2870sta) or by the rt2x00 project's driver (modules rt2800usb, rt2x00lib, rt2x00usb). rt3070 devices are supported by Ralink's rt3070 driver (module rt3070sta)

[SIZE=3]**Blacklisting Modules:**[/SIZE]

To begin,  unplug any Ralink USB WiFi adapters and restart your computer (or unload the modules).

**To use rt2870sta and blacklist rt2800usb**, run the following commands in terminal:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```add these lines to the end of the file:
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

```Save the file, then insert your USB WiFi device.

**To use rt2800usb and blacklist rt2870sta**, run the following commands in terminal:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```add these lines to the end of the file:
```
blacklist rt2870sta
```Save the file, then insert your USB WiFii device.

**To use rt3070sta and blacklist all other modules (probably unnecessary, not recommended)**, run the following commands in terminal: 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```add these lines to the end of the file:
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist rt2870sta

```Save the file, then insert your USB WiFi device.


[SIZE=2]**If this didn't work:**[/SIZE]

Your device either doesn't function with the driver you chose, or your WiFi Adapter's USB Device ID is not detected by that driver. If you're certain of which chipset is in your WiFi Adapter, you can modify and compile a kernel module that will detect and attempt to control any adapter with its USB Dev ID.
[B]


**Determining Your Device's USB Device ID**
You can check your USB Device ID using ```
lsusb
```For example, lsusb states that a USB WiFi adapter has a device ID of 1234:7777  ```
 oo@oo:~$ lsusb
Bus 001 Device 004: ID 1234:7777 Brand
```



EDIT: PLEASE READ: [/B]Luckily, someone has outlined how to pass new USB Dev IDs to a compiled kernel module, and it is a MUCH better solution than what I've explained below (recompiling a kernel module).
If you're having an issue with a driver not supporting your device due to a USB Dev ID issue, please see flash63's post here: [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6) 
His Udev Rule is the best way to solve this problem. Good luck!



**[SIZE=2]Compiling a New Kernel Module (Driver)[/SIZE]**
You'll need a compiler and Linux headers installed
```
sudo apt-get install build-essential linux-headers-generic
```


**Modifying and Compiling RT2870STA: **

Download a copy of Ralink's rt2870 USB driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Save it to your Ubuntu computer's desktop, then extract its contents using the following commands in terminal:
```
cd ~/Desktop
tar -xvf ~/Desktop/RT2870_LinuxSTA*.tgz
cd ~/Desktop/*2870*
```Now you'll make some modifications, to add your device's USB Device ID. The following is an **EXAMPLE**. Using the lsusb command, it has been determined that an adapter has has the USB Device ID 1234:7777. **MODIFY THESE INSTRUCTIONS TO USE YOUR USB DEV ID!** You can put whatever you want for comments between */ s, they are meant to document the code.

Edit ```
gedit ~/Desktop/*2870*/common/rtusb_dev_id.c
```add to the group:
```
{USB_DEVICE(0x1234,0x7777)}, /* Example WiFi Device Name */
```Save.

You'll now configure the source to be compiled with support for NetworkManager and wext. NetworkManager is Ubuntu's default graphical method for configuring networking. It provides the icon in the "notification area" aka "system tray".

Edit ```
gedit ~/Desktop/*2870*/os/linux/config.mk
```Change ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

```to ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```Save.


In terminal:```
cd ~/Desktop/*2870*
(If you're trying to compile a second time, please note: Run "make clean" before running "make" to remove your previous attempt.)
make
sudo make install
```This installs the module rt2870sta.ko, but now you have 2 copies of it: 
one in /lib/modules/`uname -r`/kernel/drivers/net/wireless  and another at /lib/modules/`uname -r`/kernel/drivers/staging/rt2870. The one in the staging directory is the one that came with Ubuntu, which obviously doesn't work for you.  

Before you move your old driver, run the following commands to see if your newly compiled driver actually functions with your USB device.```
sudo modprobe -r rt2870sta
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
sudo /etc/init.d/networking restart
sudo restart network-manager
```If NetworkManager now works, congratulations.

Then delete the version of the rt2870sta module that came with Ubuntu (there are certainly better ways to do this [PLEASE ADVISE!], but this will allow the newly compiled one will load by default). ```
sudo mkdir ~/.rt2870.bak
sudo mv /lib/modules/`uname -r`/kernel/drivers/staging/rt2870 ~/.rt2870.bak
```Otherwise, you will have to run the above commands whenever you want to use the new driver. You will need to recompile this module every time a new Linux kernel is installed.


**Modifying and Compiling RT3070STA:**

Download a copy of Ralink's rt3070 USB driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
Save it to your Ubuntu computer's desktop, then extract its contents using the following commands in terminal:
```
cd ~/Desktop
tar -xvf ~/Desktop/RT3070_LinuxSTA*.tgz
cd ~/Desktop/*3070*
```Now you'll make some modifications, to add your device's USB Device ID. The following is an **EXAMPLE**. Using the lsusb command, it has been determined that an adapter has has the USB Device ID 1234:7777. **MODIFY THESE INSTRUCTIONS TO USE YOUR USB DEV ID!** You can put whatever you want for comments between */ s, they are meant to document the code.

Edit ```
gedit ~/Desktop/*3070*/os/linux/usb_main_dev.c
```add your device to the group:
```
{USB_DEVICE(0x1234,0x7777)}, /* Example WiFi Device Name */
```Save.

You'll now configure the source to be compiled with support for NetworkManager and wext. NetworkManager is Ubuntu's default graphical method for configuring networking. It provides the icon in the "notification area" aka "system tray".

Edit ```
gedit ~/Desktop/*3070*/os/linux/config.mk
```Change ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

```to ```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```Save.


In terminal:```
cd ~/Desktop/*3070*
(If you're trying to compile for the second time, please note: Run "make clean" before running "make" to remove your previous configuration files.)
make
sudo make install
```
If you see any garbage about “/tftpboot”, disregard it. The developers made a mistake here and "make" tries to write to "/"
The module rt3070sta.ko is now installed, but there are 2 copies of it: 
one in /lib/modules/`uname -r`/kernel/drivers/net/wireless  and another at /lib/modules/`uname -r`/kernel/drivers/staging/rt3070. The one in the staging directory is the one that came with Ubuntu, which obviously doesn't work for you.  

Before you move your old driver, run the following commands to see if your newly compiled driver actually functions with your USB device.```
sudo modprobe -r rt3070sta
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt3070sta.ko
sudo /etc/init.d/networking restart
sudo restart network-manager
```If NetworkManager now works, congratulations.

Then move the version of the rt3070sta module that came with Ubuntu (there are certainly better ways to do this [PLEASE ADVISE!], but this will allow the newly compiled one will load by default). ```
sudo mv /lib/modules/`uname -r`/kernel/drivers/staging/rt3070 ~/.rt3070.bak 
```Otherwise, you will have to run the above commands whenever you want to use the new driver. You will need to recompile this module every time a new Linux kernel is installed.


[SIZE=2]**FAILURE AND DEBUGGING:**[/SIZE]

If it failed, you should seriously reconsider whether your card has a different Ralink chipset such as the rt3070. Manufacturers often use various chipsets per model, even within a single revision. Many Ralink drivers are very similar, and seem to almost function with incompatible devices.


This driver was configured to support NetworkManager. This is an layer that abstracts control over wifi devices, and is another point of failure. Linux network interfaces are normally controllled using a configuration file at /etc/network/interfaces . Normally, we could test this driver's functionality using iwlist scan, to make sure that any problems aren't being caused by NetworkManager while the driver functions properly. iwlist's performance is very unpredictable with this driver (this may only be when it is compiled to support NetworkManager) and it may not work at all, or only for a short time after the interface is brought up. 

First we need to know: Was your device detected by the version of rt2870sta included with Karmic, or did you add your USB Device ID to the module you compiled? You must do the blacklist steps even if you compiled a module. 
Does your device show up in the NetworkManager applet (networking icon in notification area aka "system tray)? 
What is the manufacturer and model number of your WiFi adapter? 
Have you tried to use ndiswrapper? If so, add "ndiswrapper" to /etc/modprobe.d/blacklist.conf . It will conflict with any native drivers.
Are you running a new Karmic install or did you upgrade from Jaunty? This is important because if you've upgraded. some settings may not have gracefully migrated.

For debugging purposes: Turn off your computer, unplug any Ralink-based USB wifi adapters. Turn it on, log in, let it finish booting. Open a terminal and run the command ```
tail -f /var/log/messages
``` Open another terminal and run ```
tail -f /var/log/syslog
``` Maximize the terminal windows (to fit outputs on 1 line) Then plug in your rt2870 device. Observe the outputs, and save them both to a txt file. The reason for turning off the computer is to ensure the device has to reload its firmware, and also to make the messages output easier to read. Post the output in this thread along with the output of the following commands, run with your WiFi adapter still connected:
```
ifconfig
iwconfig
```

If ra0 was not listed by ifconfig, run the following commands shortly after inserting the device and post the output:
```
sudo ifconfig ra0 up
sudo iwlist ra0 scan

```


Also post the output of the following commands. 
```
cat /etc/network/interfaces | grep -v ^#
lsusb
lsmod
modinfo /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
```

The purpose of these queries is to determine: Do you have conflicting drivers loaded? Does your newly compiled module have the correct device IDs? Is your WiFi card functioning without NetworkManager?

When you run lsmod, you're looking to see which modules containing "rt" are loaded. If you have more than rt2870sta, you need to make some changes.


[B]I'm still looking for a better way to do this, I think there is 
a way to insert these IDs into a driver without compiling: using Udev. 
We should find a way to add dev ids to a binary module, and to blacklist them.
There must be a mechanism to do this, please post if you learn how to use Udev or whatever it is :D Blacklisting a specific device from use by rt2x00 is a much better solution than blacklisting rt2x00. If someone has an rt73 device and an rt2870 device for example, the current solution does not work. rt73 will load rt2x00, and rt2870sta wont work.
[/B]

---

### Post by neerajadsul on 2009-12-02
Hi,
Does this depend on the Hardware Manufacturer? I mean, do we have to do something additional for each manufacturer?

I will try today with My Siemens USB Gigaset 300 adapter (which I suppose has RT4870 chip).

Thanks a lot !!!

---

### Post by calvinwels on 2009-12-02
Thanks for the excellent and well written tutorial. However, I am still unable to get my Ralink 2870 adapter to work.  I've played with this setup under Karmic far too long already, but tried once more using your links and suggestions, but still no go (this adapter worked great under Jaunty).  As requested here is the lowdown of the settings.
First lsusb:
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0411:00e8 MelCo., Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Then the modinfo:
filename:       rt2870sta.ko
version:        2.2.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     C800221A9FC392167CBBF96
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.31-15-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)


and the dmesg:
[ 2536.189556] rtusb init --->
[ 2536.190077] 
[ 2536.190079] 
[ 2536.190080] === pAd = f87d7000, size = 471912 ===
[ 2536.190081] 
[ 2536.190084] <-- RTMPAllocAdapterBlock, Status=0
[ 2536.191054] usbcore: registered new interface driver rt2870
[ 2624.180846] wlan0: authenticate with AP 00:16:01:11:2b:8b
[ 2624.190260] wlan0: authenticated
[ 2624.190267] wlan0: associate with AP 00:16:01:11:2b:8b
[ 2624.193715] wlan0: RX ReassocResp from 00:16:01:11:2b:8b (capab=0x411 status=0 aid=2)
[ 2624.193721] wlan0: associated

I've done all the preliminary including blacklisting the wayward drivers and changing the config files for supplicant support.

I'm limping along using a Linksys 802.11(g) pci adapter rather than the Buffalo WLI-UC-G300N which uses the RT2870 drivers.  Checking the status in Network Tools, it only shows the wlan0 connection using the MAC of the Linksys.  Removing the PCI doesn't help.  Other posts here have implied there may be an issue the the WPA2 encryption I use, but because other members of the household use the WPA2 encryption with the N protocol, I don't want to dumb down the encryption just for the linux  computer.   But I sure would be a happy camper if I could run this system using the Buffalo adapter.  Any advice is welcome.

---

### Post by peepingtom on 2009-12-02
calvinwels: It looks like the driver you compiled is detecting your USB device, this is good :D We'll have to figure out what else is wrong, whether it's a driver issue or something else Is this a new Ubuntu install or an upgrade? Does the USB device just not show up in NetworkManager, or is it "disabled"?

I added a bit to the tutorial, more debugging steps and a little comment below the [B]sudo rmmod rt2870sta 
sudo insmod ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko[/B] part (for now, just run those commands when you want to play with the rt2870 device, the old driver is still loading by default)

neerajadsul: The modification is to make sure the driver identifies the USB Device ID of your device. The first 4 bits of the ID are a vendor ID, the second 4 are device specific. The stuff contained within "/* xxxxx*/" is just a comment to document the change you made. You can put whatever you want in there.


I'm still looking for a better way to do this, I think there is a way to insert these IDs into a driver without compiling using udev or modules.alias or something. I'm pretty busy currently though, so I don't know if/when i'll have a solution along those lines.

---

### Post by peepingtom on 2009-12-03
Calvinwels:

The stuff you posted last, was that with both you USB and PCI adapter inserted? It's confusing, wlan0 is your linksys adapter, no?

Don't boot your computer with the USB device inserted. Insert it into a fully booted computer. Then run:

```
sudo rmmod rt2870sta
sudo insmod ~/Desktop/2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/rt2870sta.ko 
```
and post the debug results.

---

### Post by calvinwels on 2009-12-04
Thank you for your reply.  As you suggested, I tried booting the computer without the Ralink adapter and also removed the older PCI adopter.  After plugging in the Ralink adapter after booting and starting it up, Network Manager still did not recognize there was any wireless device attached even though the adapter's light was flashing.   In running the debugs, the lsusb and modinfo appear unchanged from my earlier post. 
The ifconfig shows:
  	 	 	 	 	 	  ra0       Link encap:Ethernet  HWaddr 00:1d:73:bc:d7:dc   
           inet6 addr: fe80::21d:73ff:febc:d7dc/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:1297 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1437 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:159775 (159.7 KB)  TX bytes:115280 (115.2 KB)  
 
iwconfig:
  	 	 	 	 	 	  ra0       Ralink STA  ESSID:"lclntwk"  Nickname:"RT2870STA"  
           Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated    
           Bit Rate:1 Mb/s    
           RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 



dmesg:
   	 	 	 	 	 	  [  551.549174] === pAd = f8858000, size = 471912 ===  
 [  551.549175]  
 [  551.549179] <-- RTMPAllocAdapterBlock, Status=0  
 [  551.550059] usbcore: registered new interface driver rt2870  
 [  561.404027] <-- RTMPAllocTxRxRingMemory, Status=0  
 [  561.405821] -->RTUSBVenderReset  
 [  561.405944] <--RTUSBVenderReset  
 [  561.682852] Key1Str is Invalid key length(0) or Type(0)  
 [  561.682879] Key2Str is Invalid key length(0) or Type(0)  
 [  561.682906] Key3Str is Invalid key length(0) or Type(0)  
 [  561.682932] Key4Str is Invalid key length(0) or Type(0)  
 [  561.683390] 1. Phy Mode = 5  
 [  561.683392] 2. Phy Mode = 5  
 [  561.715417] RTMPSetPhyMode: channel is out of range, use first channel=1  
 [  561.727412] 3. Phy Mode = 9  
 [  561.736037] MCS Set = ff ff 00 00 01 
 [  561.745031] <==== rt28xx_init, Status=0  
 [  561.746532] 0x1300 = 00064300  
 [  572.256007] ra0: no IPv6 routers present  
 [  576.916107] #  
 [  591.680088] #  
 [  617.176075] #  
 [  623.216075] #  
 [  631.268079] #  
 [  646.032083] #  
 [  656.096126] #  
 [  677.568148] #  
 [  699.040063] #  
 [  705.080065] #  
 [  712.464047] #  
 

 

 and lsmod
   	 	 	 	 	 	  rt2870sta             541804  1  
 snd_mpu401_uart         6940  3 snd_wavefront,snd_cs4236,snd_mpu401  
 gameport               11368  2 ns558  
 snd_rawmidi            22208  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi  
 snd                    59204  21 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 parport                35340  2 ppdev,lp  
 agpgart                34988  3 ttm,drm,amd64_agp 



At one point, Network Manager actually saw both the pci adapter as well as the usb adapter, but now refuses to see the usb at all even when the pci is removed.  Even when it saw the usb adapter, however, it still did not connect.  I initially upgraded from Jaunty, but in an attempt to get the usb adapter to work, I ended up doing a clean install as well.  All without success.  The usb adapter worked flawlessly under Jaunty, but I have video card problems re-installing Jaunty.  Any thoughts for solving this would be appreciated.

---

### Post by peepingtom on 2009-12-05
Is your card connecting to a network with the ESSID "lclntwk"? Because the default for this driver is "11n-AP", I don't know why yours says lclntwk Is this related to some change you made?. This doesn't really seem to be a fresh install, I mean there's more changed than just the new module you compiled. It seems like your driver works fine, this is some other issue?

Only these 2 lines should be in /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```

Did you edit /etc/Wireless/RT2870STA/RT2870STA.dat for some reason? If so, restore it to its former glory.
Your wifi card doesn't show up in Networkmanager at all, or is it listed as "disabled" or "unmanaged"?


To me, a clean install means you installed clean and followed my instructions exactly, it's hard to debug when I don't know what's changed on your system. If you followed my instructions and they didn't work, my instructions are bad or you made a mistake :D
I am worried that my instructions suck, they worked for me like 5 times though :O

---

### Post by Love2MeetU on 2009-12-05
My PC isn't showing the USB, but otherwise I have everything fine until the 
                                       [I]sudo make
sudo make install[/I]
   
  
Then it says

*2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk: No such file or directory*

and also 
*Error 2*

---

### Post by peepingtom on 2009-12-05
> **Love2MeetU said:**
> My PC isn't showing the USB, but otherwise I have everything fine until the 
```
sudo make
sudo make instal
2009_0820_RT2870_Linux_STA_V2.2.0.0/os/linux/config.mk: No such file or directory
```


You mean the not showing the USB device ID, or the device is not listed using lsusb?


Are you sure you didn't make a typo?I posted more clear instructions about how to extract the .tar.bz file, it seems like you're missing something. Make sure linux-headers-generic is installed.

---

### Post by Love2MeetU on 2009-12-06
> **peepingtom said:**
> You mean the not showing the USB device ID, or the device is not listed using lsusb?


Are you sure you didn't make a typo?I posted more clear instructions about how to extract the .tar.bz file, it seems like you're missing something. Make sure linux-headers-generic is installed.

I used lsub and it wasn't listed.

I didn't make any typos, double-checked that, and besides I copied & pasted your command lines. Then double-checked again.

Is it possible the linux-headers-generic is damaged, and how would I check for that? I'm trying some other testing as well, just in case the problem is mechanical (damage to the USB plug, etc...)

Quite willing to do a fresh install again if necessary. Doesn't take long anyway, besides everything is backed-up.

---

### Post by smokeyd on 2009-12-06
Hi peepingtom and eveyone else,

Thanks peepingtom for the tutorial. It is well written, but I don't get my linksys WUSB100v2 working. I followed your tutorial to compile the driver. It seems you already added the usb id (1737:0078) of this specific networkcard to the driver (you're using the same?). 
The driver compiled fine. I removed the original staging driver and blacklisted the other drivers as directed. When i insert the wusb100v2 into my ubuntu karmic box (new installation), iwconfig directly sees the ra0 card. ifconfig doesn't show it though, and network-manager doesn't show the part for wireless networks at all (after restarting network-manager). 
After using ifconfig ra0 up, the wireless lan card is shown both with iwconfig and ifconfig, and after restarting network-manager, the part for "wireless networks" is present in the nm-applet, but it is shown as disconnected. 
The thing is this is a wireless N adapter, but only wireless G networks are present here. Could this be the problem?

To test a little, I also added ra0 to /etc/network/interfaces with the config which works for another wireless card which is a rt2500usb card. With this config the wusb100v2 card doesn't find any wireless networks either.

I added the debug info as you described in the attachment with the commands I ran (when running that stuff, i didn't have any configuration in /etc/network/interfaces yet other than the default for lo).
 I hop you ca help.
Cheers,

Dolf.

---

### Post by peepingtom on 2009-12-06
Deleted because some people were confused by it.
The tutorial has been rewritten.



Clearly, some people do need to add their USB Device IDs to the module. However, it turns out my whole idea about RT2870STA.dat was snake oil. Sorry. It isn't necessary.
RT2870STA will function without it. It can still be used to configure the driver without using NetworkManager, though. If you compile your own version of the driver, the install process will install a copy of it. I've removed those parts of the instructions from the tutorial.

---

### Post by peepingtom on 2009-12-07
> **Love2MeetU said:**
> I used lsub and it wasn't listed.


You should try booting to a liveCD and see if it shows up when you run lsusb then. If it doesn't I'd say your device is broken :(


A new version or rt2870STA has been released that does not require a patch to work with the 2.6.31 kernel.

I've posted an updated tutorial. It no longer depends on any code that has been messed with by me.

---

### Post by peepingtom on 2009-12-07
ooooo

---

### Post by Love2MeetU on 2009-12-07
> **peepingtom said:**
> You should try booting to a liveCD and see if it shows up when you run lsusb then. If it doesn't I'd say your device is broken :(


A new version or rt2870STA has been released that does not require a patch to work with the 2.6.31 kernel.

I've posted an updated tutorial. It no longer depends on any code that has been messed with by me.

I've done that now, and also done a fresh install again. This time found the USB dongle but it's not listed properly as what it is, so I didn't recognise it the first time around. Tomorrow I'll have the time to try your "fix" again. Maybe I'll be lucky. 

You've been a great help, but I'm crossing my fingers. This computer of mine is a finicky critter

---

### Post by Love2MeetU on 2009-12-08
OK, that DIDN'T work. I stuffed up somewhere, I think. Somehow damaged the HAL daemon and couldn't login, then when I fixed that sort of, I lost all sound. Also my USB mouse stopped working. The problem seemed to come up at this point (although I'm only guessing) because when I included this;
> sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870

Nothing appeared to happen.

---

### Post by peepingtom on 2009-12-08
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870 
Deletes the the folder where the old module is found, it does not provide any feedback after it's run. It only affects the rt2870sta module included with Ubuntu. I have no idea how you cane to have problems with HAL, was that while trying to follow my tutorial? 
Do you have a USB sound device? Maybe you added the USB Dev ID of your sound device to the Rt2870 driver, which messed things up. Are you sure your USB device has an rt2870 chipset?!

This tutorial can be run while using a liveCD, btw. It just won't work after restarting, obviously. Please post the debugging information outlined in the first post if you want help.


**THE TUTORIAL HAS BEEN UPDATED AS OF 19:10 8/12/09**
sudo restart network-manage and sudo /etc/init.d/networking restart

Were added to the testing section to make the compilation guide compatible with liveCD testing.

---

### Post by Love2MeetU on 2009-12-08
> **peepingtom said:**
> sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870 
Deletes the the folder where the old module is found, it does not provide any feedback after it's run. It only affects the rt2870sta module included with Ubuntu. I have no idea how you cane to have problems with HAL, was that while trying to follow my tutorial? 
Do you have a USB sound device? Maybe you added the USB Dev ID of your sound device to the Rt2870 driver, which messed things up. Are you sure your USB device has an rt2870 chipset?!

Pity there's no feedback after it's run. I don't know how it affected HAL either, but I've been having problems with Karmic Koala with sound anyway (after a fresh install, and even after updates, the sound still doesn't work with youtube videos - but it's perfect with Alien Arena). I don't have any USB sound devices.

I did another re-install after the HAL problem, so trying again right now.

> **peepingtom said:**
> Are you sure your USB device has an rt2870 chipset?!

	 	 	 	 	  Before plugging in the USB dongle, this is the result of lsusb;
 

 Bus 002 Device 002: ID 04fc:0005 Sunplus Technology Co., Ltd  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 

 After plugging in the USB dongle, this is the result of the lsusb;
 

 Bus 002 Device 002: ID 04fc:0005 Sunplus Technology Co., Ltd  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 0411:0137 MelCo., Inc.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 

 It's clear to me that the ID 0411:0137 MelCo., Inc. device is the USB dongle. Checking into this found that it uses an RT2870 chipset, as I was informed by[ em3raldxiii]("http://ubuntuforums.org/member.php?u=107225")  here;
[http://ubuntuforums.org/showthread.php?t=1346330](http://ubuntuforums.org/showthread.php?t=1346330)




 > **peepingtom said:**
> 
This tutorial can be run while using a liveCD, btw. It just won't work after restarting, obviously. Please post the debugging information outlined in the first post if you want help.


**THE TUTORIAL HAS BEEN UPDATED AS OF 19:10 8/12/09**
sudo restart network-manage and sudo /etc/init.d/networking restart

Were added to the testing section to make the compilation guide compatible with liveCD testing.

Okay, I'll try that tomorrow, and get back to you soon. I'm interested to see what happens too.

---

### Post by peepingtom on 2009-12-09
Well if you haven't gotten it working:

You never had it working under Ubuntu, right?
It might not be an rt2870 chipset. Ralink's new 802.11n chipsets use the rt3070sta driver. I actually had the same identification issue with my USB adapter, I don't even own an rt2870 device anymore.

[http://forums.ncix.com/forums/index.php?mode=showthread&msg_id=2026623&threadid=2026623&forum=105&product_id=37959&msgcount=0&overclockid=0](http://forums.ncix.com/forums/index.php?mode=showthread&msg_id=2026623&threadid=2026623&forum=105&product_id=37959&msgcount=0&overclockid=0)

Is this the same as your adapter?


If it is, I think you've miscategorized the chipset. I'll update the tutorial for all ralink chipsets soon, but i'll do it tomorrow if your card is likely 3070sta.

---

### Post by Love2MeetU on 2009-12-09
> **peepingtom said:**
> Well if you haven't gotten it working:

You never had it working under Ubuntu, right?
It might not be an rt2870 chipset. Ralink's new 802.11n chipsets use the rt3070sta driver. I actually had the same identification issue with my USB adapter, I don't even own an rt2870 device anymore.

[http://forums.ncix.com/forums/index.php?mode=showthread&msg_id=2026623&threadid=2026623&forum=105&product_id=37959&msgcount=0&overclockid=0](http://forums.ncix.com/forums/index.php?mode=showthread&msg_id=2026623&threadid=2026623&forum=105&product_id=37959&msgcount=0&overclockid=0)

Is this the same as your adapter?


If it is, I think you've miscategorized the chipset. I'll update the tutorial for all ralink chipsets soon, but i'll do it tomorrow if your card is likely 3070sta.

Maybe you're right about the miscategorization of the driver, but that's not the same as the USB dongle that I have.

This is mine
[http://buffalo.jp/products/catalog/network/wli-uc-g/](http://buffalo.jp/products/catalog/network/wli-uc-g/)
[http://www.buffalo-technology.com/products/wireless/wireless-g/wli-uc-g-wireless-g-usb-20/](http://www.buffalo-technology.com/products/wireless/wireless-g/wli-uc-g-wireless-g-usb-20/)

They're very common in Japan (and Asia in general) because they're quite cheap. Although I could "possibly" avoid the problem with ndiswrapper or similar using a Windows driver (I'll try that too this afternoon), I believe it would be better if somehow it could run natively with Linux. That would be both more elegant, and more attractive to the Asian market.

Anyway, I'm going to try again with your method, and also do a test with the live CD on both of my PCs. See if I can get it to work.

---

### Post by 2hot6ft2 on 2009-12-10
Worked for mine, at least it's working in Ubuntu Ultimate Edition 2.5 (based on Ubuntu 9.10) by adding the lines
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```
to the blacklist as per peepingtoms instructions.

Before that it would show up under available networks in network manager but it wouldn't make any attempt to connect.

Belkin N Wireless USB Dongle F5D8053 ver. 4001
Chip RT2870
lsusb shows it as
```
ID [COLOR="DarkRed"]**050d:8053**[/COLOR] Belkin Components
```
The part in red is the part to search for to find out what chip yours is.

For those that are using laptops with internal wifi cards and trying to use an external usb wifi dongle, on mine the internal must be on i.e. blue light for any external wifi dongle to work.

Once it connects I have to click on network manager and it will show both adapters are connected then click on disconnect for the internal card. My internal is a Atheros AR928X (Atheros AR5009 Mini PCI Card). The blue light stays on, don't turn it off using the button or it wont work. If I don't disconnect it that way then I can't go anywhere on the Internet.

Thanks peepingtom for the solution to this.

Now if I can get it fully functional in BackTrack 4 Pre-Final including injection and monitoring that will make it a real keeper for my collection.

---

### Post by grief -l on 2009-12-10
> A new version or rt2870STA has been released that does not require a patch to work with the 2.6.31 kernel.

I've posted an updated tutorial. It no longer depends on any code that has been messed with by me.

 
 
Where do we find this?
 
Gabe

---

### Post by Love2MeetU on 2009-12-12
update on my problems;
This time managed to get the driver to install, the USB dongle's little light came on for the first time, but when restarted...nothing worked again.

Dang it :(

Still haven't had the chance to test with Live CD yet, too busy past 2-3 days.

---

### Post by anthonyalbertyn on 2009-12-12
This was a very good tutorial. Thank you so much.

[SIZE=2]BLACKLISTING rt2x00 MODULES worked for me. I am using an Edimax USB adapter (Model number EW-7711UAn, FCC ID: NDD9577110812) with Ubuntu 9.10.

Summary of steps that I took (as per your instructions):

1. Unplug your USB WiFi adapter and restart your computer.
2. In terminal: sudo gedit /etc/modprobe.d/blacklist.conf

add these lines to the end of the file:

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

Save the file

3. Insert your USB wifi device.

And it worked! Brilliant!


[/SIZE]

---

### Post by Love2MeetU on 2009-12-12
Done that already, but didn't work for me. I wish it had. When I restarted, the USB dongle stopped working

---

### Post by calvinwels on 2009-12-13
The new version of the RT2870 driver (2.3.0.0) seems to now work under Karmic.  Before I installed the new driver, I removed the older driver as follows from your driver directory:
first go to the os/linux directory and type sudo rmmod rt2870sta
then cd ../../
sudo make uninstall
sudo make clean

install the 2.3.0.0 version as instructions for the older driver.  
Hope this helps

---

### Post by Love2MeetU on 2009-12-13
> **calvinwels said:**
> The new version of the RT2870 driver (2.3.0.0) seems to now work under Karmic.  Before I installed the new driver, I removed the older driver as follows from your driver directory:
first go to the os/linux directory and type sudo rmmod rt2870sta
then cd ../../
sudo make uninstall
sudo make clean

install the 2.3.0.0 version as instructions for the older driver.  
Hope this helps

OK, I'll try it.

---

### Post by Love2MeetU on 2009-12-13
> **calvinwels said:**
> The new version of the RT2870 driver (2.3.0.0) seems to now work under Karmic.  Before I installed the new driver, I removed the older driver as follows from your driver directory:
first go to the os/linux directory and type sudo rmmod rt2870sta
then cd ../../
sudo make uninstall
sudo make clean

install the 2.3.0.0 version as instructions for the older driver.  
Hope this helps

Forgive me for being a newbie, but when I type os/linux nothing happens, instead I get "no such file or directory".

What do I type?

---

### Post by Love2MeetU on 2009-12-13
Tried again, just after a recent update.

This time when I put the USB dongle in, after a minute the little light came on. Looks liek I'm getting somewhere.

This is the result of the check with lsusb

> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ppp0      no wireless extensions.

ra0       Ralink STA  

Maybe I'm getting somewhere...

---

### Post by Hanto on 2009-12-14
[SIZE=5]  This has worked for 9.10 Karmic on my laptop ( VGN-FZ140E ). In fact it is now working better then my 9.04 I do believe. I will report back once I determine if this also helps my 9.04 with the new drivers from Ralink. 
   Thanks MUCH guys, I had been trying to get this to work on 9.10 for months now.
[/SIZE]

---

### Post by Hanto on 2009-12-14
[SIZE=5]  Took me two times trying before I could get these new drivers to install more or less properly in 9.04 on the Sony VGN-FZ140E laptop, but finally they seem to have stuck with the plan. Presently accessing the net using two old Belkin adapters that previously I had thought were less then sufficient for the task. In other words I had considered them very close to being bad. They sit outside on a long pole with only a plastic bag over them to protect them from weather. Yes, I go to extremes!
  Tomorrow I will attempt the same procedures on my HP s3020n 9.04 box.
   What has been accomplished here tonite has meant a great deal to me.
    Thank you very much.
[/SIZE]

---

### Post by calvinwels on 2009-12-14
> **Love2MeetU said:**
> Tried again, just after a recent update.

This time when I put the USB dongle in, after a minute the little light came on. Looks liek I'm getting somewhere.

This is the result of the check with lsusb

Maybe I'm getting somewhere...

Try typing ifconfig ra0 up.  You should then be able to configure the adapter and establish your connection.

---

### Post by calvinwels on 2009-12-14
> **Love2MeetU said:**
> Tried again, just after a recent update.

This time when I put the USB dongle in, after a minute the little light came on. Looks liek I'm getting somewhere.

This is the result of the check with lsusb

Maybe I'm getting somewhere...
Try typing in the console 
ifconfig ra0 up
you then should be able to configure your wireless using  iwconfig or Network Manager

---

### Post by hieppo000 on 2009-12-16
I get this error when I attempt to make...any suggestions?

```
hiep@whois:~/Desktop/RT2870_LinuxSTA_V2.3.0.0$ sudo make
make -C tools
make[1]: Entering directory `/home/hiep/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/hiep/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools'
/home/hiep/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/hiep/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/Makefile
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/hiep/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux modules
make: *** /lib/modules/2.6.31-14-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2


```

---

### Post by Hanto on 2009-12-16
[SIZE=5]  I have recommended peepingtom's tutorial as a sticky. I also believe that other vendors besides Linksys and Belkin are affected by this 9.10 issue with the Ralink rt2870 chipset. Any future firmware updates to 9.10 hopefully would incorporate some of peepingtom's wisdom.
  The new 2.300 Ralink drivers also allow for a greater latitude with Windows drivers outside of the normal vendor limitations. In my case I could and did replace both my Linksys and my Belkin drivers with the improved Ralink rt3572 a/b/g/n wireless lan usb device. Made quite a bit of difference in my case on two different computers. One being Intel, and one being AMD. [/SIZE]

---

### Post by Love2MeetU on 2009-12-16
> **calvinwels said:**
> Try typing in the console 
ifconfig ra0 up
you then should be able to configure your wireless using  iwconfig or Network Manager

When i type in *ifconfig ra0 up*, I have this result;
*SIOCSIFFLAGS: Permission denied*

:(

---

### Post by peepingtom on 2009-12-16
That command must be preceded by sudo 

Any luck determining what chipset your device uses?


I'll add something about "make clean" to the tutorial, thanks for the reminder calvinwels
It's important for people to be able to make a fresh start ;)

---

### Post by mebinte on 2009-12-16
hey guys. i havent read all 4 pgs, but this is how i got it to work. i have airlink usb adapter n . its model is AWLL6070 and also has rt2870.inf under the winxp driver folders.

1)download x64 rt2870 drivers +ndiscommonamd64,ndiswrapperamd64,ndisgthamd64
2)save all to usb stick. disconnect usb adapter and reboot
3) let ubuntu install. then install the ndis stuff and add the driver
4)plug usb adapter back in and input the router password (it automatically recognized my wireless connection) ^^

hope it helps

---

### Post by hieppo000 on 2009-12-17
I finally got my card to light up.  with the excellent instructions..thanks...its still not connecting.  how do i configure it from here?   i do have another usb nic so i can browse.  here is the relevant information.
```

**lsusb**
Bus 001 Device 004: ID 1737:0079 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root h

**modinfo /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko**
filename:       /lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.3.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     80A74DD94FCCA18E96F5732
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.31-16-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

**dmesg**

[  972.933760] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0408 with error -19.
[  972.933766] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0408 with error -19.
[ 1051.415486] usb 1-3: USB disconnect, address 3
[ 1051.415570] Bulk In Failed. Status=-108, BIIdx=0x0, BIRIdx=0x0, actual_length= 0x0
[ 1051.415733] rtusb_disconnect: unregister usbnet usb-0000:00:12.2-3
[ 1051.415739] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
[ 1051.425519] CMDTHREAD_RESET_BULK_IN: Read Register Failed!Card must be removed!!
[ 1051.425523] 
[ 1051.494331] ---> RTMPFreeTxRxRingMemory
[ 1051.494370] <--- RTMPFreeTxRxRingMemory
[ 1051.772098]  RTUSB disconnect successfully
[ 1054.560044] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 1054.722951] usb 1-3: configuration #1 chosen from 1 choice
[ 1054.728397] 
[ 1054.728400] 
[ 1054.728401] === pAd = f8b58000, size = 482868 ===
[ 1054.728403] 
[ 1054.728538] <-- RTMPAllocAdapterBlock, Status=0
[ 1055.011638] <-- RTMPAllocTxRxRingMemory, Status=0
[ 1055.013690] -->RTUSBVenderReset
[ 1055.013799] <--RTUSBVenderReset
[ 1055.291797] Key1Str is Invalid key length(0) or Type(0)
[ 1055.291834] Key2Str is Invalid key length(0) or Type(0)
[ 1055.291874] Key3Str is Invalid key length(0) or Type(0)
[ 1055.291916] Key4Str is Invalid key length(0) or Type(0)
[ 1055.292616] 1. Phy Mode = 5
[ 1055.292619] 2. Phy Mode = 5
[ 1055.324751] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 1055.336589] 3. Phy Mode = 5
[ 1055.344571] MCS Set = ff ff 00 00 01
[ 1055.348812] <==== rt28xx_init, Status=0
[ 1055.350435] 0x1300 = 00064300
[ 1066.016008] ra0: no IPv6 routers present
[ 1069.380016] usb 2-2: new high speed USB device using ehci_hcd and address 4
[ 1069.698365] usb 2-2: configuration #1 chosen from 1 choice
[ 1069.962086] phy1: Selected rate control algorithm 'minstrel'
[ 1069.963349] Registered led device: rt73usb-phy1::radio
[ 1069.963376] Registered led device: rt73usb-phy1::assoc
[ 1069.963402] Registered led device: rt73usb-phy1::quality
[ 1069.990465] udev: renamed network interface wlan0 to wlan1
[ 1069.991576] rt73usb 2-2:1.0: firmware: requesting rt73.bin
[ 1070.084715] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1077.875737] wlan1: authenticate with AP 00:0d:0b:ae:dc:b6
[ 1077.877361] wlan1: authenticated
[ 1077.877365] wlan1: associate with AP 00:0d:0b:ae:dc:b6
[ 1077.879732] wlan1: RX AssocResp from 00:0d:0b:ae:dc:b6 (capab=0x411 status=0 aid=1)
[ 1077.879737] wlan1: associated
[ 1077.893561] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1088.709502] wlan1: no IPv6 routers present


**ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr 00:25:9c:b2:95:01  
          inet6 addr: fe80::225:9cff:feb2:9501/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:64944 (64.9 KB)

wlan1     Link encap:Ethernet  HWaddr 00:16:b6:95:e8:c1  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe95:e8c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358790 (358.7 KB)  TX bytes:75961 (75.9 KB)


**iwconfig**

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"WWJD"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:0B:AE:DC:B6   
          Bit Rate=36 Mb/s   Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



**lsmod |grep rt**

rt2870sta             554780  1 
rt73usb                26336  0 
crc_itu_t               1852  1 rt73usb
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181076  2 rt2x00usb,rt2x00lib
agpgart                34988  1 nvidia
cfg80211               93052  2 rt2x00lib,mac80211
parport                35340  2 ppdev,lp

```

---

### Post by peepingtom on 2009-12-17
You have 3 sets of drivers for Ralink cards running at the same time. My instructions say to blacklist the rt2x00 driver, but I suppose this is required for rt73 to work. Unfortunately, they conflict with rt2870sta. Can you post the dmesg output with them blacklisted as per the instructions? Unfortunately this means you'll be copy/pasting :D

Ah also: There is an option in the make file for rt2870sta for multiple device support. I believe this refers to more than one rt2870 device, but that might be another issue. 

If this blacklisting doesn't solve it, please post the output of dmesg again. 

Have you upgraded from Jaunty or is this a fresh install?
Does your card show up in nm-applet (NetworkManager icon in notfication area aka system tray)?


I'll check back > 17/12 14:00 EST

---

### Post by peepingtom on 2009-12-17
Hanto: Check the .dat configuration file at /etc/Wireless
There are things to tinker with with in there. Just make a backup first, I wonder if you could fry your card this way :D Google around for more info, I don't know much about it. At least you can modify which channels your card transmits on.

All Ralink drivers use this file

---

### Post by peepingtom on 2009-12-17
We need to learn more about udev. It sure would be nice to be able to blacklist a specific device from use by a driver, to add a USB Dev ID without compiling a module.

Consider that I just now discovered udevadm monitor, don't expect anything. Ever. I don't even have an rt2870 device any longer.

If anyone has a good link, please share it!

---

### Post by phillip2 on 2009-12-17
Just tried the information in the main article. The blacklisting got my 
D-link DWA-140 working just fine. So far, no drop outs at all. 

Many thanks for the tutorial!

---

### Post by hieppo000 on 2009-12-17
> **peepingtom said:**
> You have 3 sets of drivers for Ralink cards running at the same time. My instructions say to blacklist the rt2x00 driver, but I suppose this is required for rt73 to work. Unfortunately, they conflict with rt2870sta. Can you post the dmesg output with them blacklisted as per the instructions? Unfortunately this means you'll be copy/pasting  Ah also: There is an option in the make file for rt2870sta for multiple device support. I believe this refers to more than one rt2870 device, but that might be another issue.  If this blacklisting doesn't solve it, please post the output of dmesg again.  Have you upgraded from Jaunty or is this a fresh install? Does your card show up in nm-applet (NetworkManager icon in notfication area aka system tray)?   I'll check back > 17/12 14:00 EST

 After I rebooted i checked the  /etc/modprobe.d/blacklist.conf, and these entries were still in there from initial  blacklist rt2x00usb blacklist rt2x00lib blacklist rt2800usb  This is a fresh install of 9.10.  The card does not show up on the NM icon...here is the dmesg.  Also now the new usb nic is not lit up anymore after the reboot and plugin.  thanks for your help

```
[    0.402448] ACPI: ACPI bus type pnp unregistered
[    0.402451] PnPBIOS: Disabled by ACPI PNP
[    0.402463] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.402466] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.402477] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.402479] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.402482] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.402484] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.402487] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.402489] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.402492] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.402494] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.402496] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.402499] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.402501] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.402504] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.402506] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.402509] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.402511] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.402514] system 00:08: ioport range 0xb00-0xb0f has been reserved
[    0.402516] system 00:08: ioport range 0xb20-0xb3f has been reserved
[    0.402519] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.402521] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.402524] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.402527] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.402530] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.402534] system 00:09: ioport range 0xe00-0xe0f has been reserved
[    0.402537] system 00:09: ioport range 0xe80-0xe8f has been reserved
[    0.402539] system 00:09: ioport range 0xf40-0xf4f has been reserved
[    0.402547] system 00:09: ioport range 0xa30-0xa3f has been reserved
[    0.402551] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.402556] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.402559] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.402562] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.402564] system 00:0b: iomem range 0x100000-0xc7ffffff could not be reserved
[    0.402567] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.437201] AppArmor: AppArmor Filesystem Enabled
[    0.437225] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.437229] pci 0000:00:02.0:   IO window: 0xd000-0xdfff
[    0.437232] pci 0000:00:02.0:   MEM window: 0xfd000000-0xfeafffff
[    0.437236] pci 0000:00:02.0:   PREFETCH window: 0x000000ce000000-0x000000dfffffff
[    0.437240] pci 0000:00:07.0: PCI bridge, secondary bus 0000:02
[    0.437242] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.437245] pci 0000:00:07.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.437248] pci 0000:00:07.0:   PREFETCH window: 0x000000fbf00000-0x000000fbffffff
[    0.437252] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.437254] pci 0000:00:14.4:   IO window: disabled
[    0.437259] pci 0000:00:14.4:   MEM window: disabled
[    0.437262] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.437272]   alloc irq_desc for 18 on node -1
[    0.437274]   alloc kstat_irqs on node -1
[    0.437278] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.437282] pci 0000:00:02.0: setting latency timer to 64
[    0.437288]   alloc irq_desc for 19 on node -1
[    0.437289]   alloc kstat_irqs on node -1
[    0.437293] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.437295] pci 0000:00:07.0: setting latency timer to 64
[    0.437303] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.437305] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.437308] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.437310] pci_bus 0000:01: resource 1 mem: [0xfd000000-0xfeafffff]
[    0.437317] pci_bus 0000:01: resource 2 pref mem [0xce000000-0xdfffffff]
[    0.437320] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.437322] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.437325] pci_bus 0000:02: resource 2 pref mem [0xfbf00000-0xfbffffff]
[    0.437327] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.437329] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.437358] NET: Registered protocol family 2
[    0.437450] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.437724] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.438231] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.438489] TCP: Hash tables configured (established 131072 bind 65536)
[    0.438491] TCP reno registered
[    0.438564] NET: Registered protocol family 1
[    0.438617] Trying to unpack rootfs image as initramfs...
[    0.500479] Switched to high resolution mode on CPU 3
[    0.500537] Switched to high resolution mode on CPU 1
[    0.500558] Switched to high resolution mode on CPU 2
[    0.503749] Switched to high resolution mode on CPU 0
[    0.618932] Freeing initrd memory: 7464k freed
[    0.622086] cpufreq-nforce2: No nForce2 chipset.
[    0.622109] Scanning for low memory corruption every 60 seconds
[    0.622195] audit: initializing netlink socket (disabled)
[    0.622207] type=2000 audit(1261081317.620:1): initialized
[    0.629573] highmem bounce pool size: 64 pages
[    0.629578] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.630958] VFS: Disk quotas dquot_6.5.2
[    0.631015] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.631498] fuse init (API version 7.12)
[    0.631572] msgmni has been set to 1676
[    0.631805] alg: No test for stdrng (krng)
[    0.631815] io scheduler noop registered
[    0.631818] io scheduler anticipatory registered
[    0.631819] io scheduler deadline registered
[    0.631860] io scheduler cfq registered (default)
[    0.724057] pci 0000:01:00.0: Boot video device
[    0.724155]   alloc irq_desc for 25 on node -1
[    0.724157]   alloc kstat_irqs on node -1
[    0.724165] pcieport-driver 0000:00:02.0: irq 25 for MSI/MSI-X
[    0.724171] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.724237]   alloc irq_desc for 26 on node -1
[    0.724238]   alloc kstat_irqs on node -1
[    0.724243] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
[    0.724247] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    0.724298] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.724318] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.724416] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.724420] ACPI: Power Button [PWRF]
[    0.724473] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.724479] ACPI: Power Button [PWRB]
[    0.724780] processor LNXCPU:00: registered as cooling_device0
[    0.724783] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.724811] processor LNXCPU:01: registered as cooling_device1
[    0.724838] processor LNXCPU:02: registered as cooling_device2
[    0.724870] processor LNXCPU:03: registered as cooling_device3
[    0.726305] isapnp: Scanning for PnP cards...
[    1.080293] isapnp: No Plug & Play device found
[    1.081281] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.082402] brd: module loaded
[    1.082801] loop: module loaded
[    1.082857] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.082913] ahci 0000:00:11.0: version 3.0
[    1.082927]   alloc irq_desc for 22 on node -1
[    1.082929]   alloc kstat_irqs on node -1
[    1.082934] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.083032] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.083036] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.083356] scsi0 : ahci
[    1.083432] scsi1 : ahci
[    1.083495] scsi2 : ahci
[    1.083548] scsi3 : ahci
[    1.083636] ata1: SATA max UDMA/133 irq_stat 0x00400000 irq 22, PHY RDY changed
[    1.083639] ata2: SATA max UDMA/133 abar m1024@0xfcfff800 port 0xfcfff980 irq 22
[    1.083643] ata3: SATA max UDMA/133 abar m1024@0xfcfff800 port 0xfcfffa00 irq 22
[    1.083648] ata4: SATA max UDMA/133 abar m1024@0xfcfff800 port 0xfcfffa80 irq 22
[    1.083865]   alloc irq_desc for 16 on node -1
[    1.083867]   alloc kstat_irqs on node -1
[    1.083871] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.083893] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.083971] scsi4 : pata_atiixp
[    1.084038] scsi5 : pata_atiixp
[    1.085130] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.085133] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.085686] Fixed MDIO Bus: probed
[    1.085713] PPP generic driver version 2.4.2
[    1.085780] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.085795]   alloc irq_desc for 17 on node -1
[    1.085797]   alloc kstat_irqs on node -1
[    1.085800] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.085811] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.085847] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.085866] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.085883] ehci_hcd 0000:00:12.2: debug port 1
[    1.085897] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfcfff000
[    1.096030] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.096085] usb usb1: configuration #1 chosen from 1 choice
[    1.096108] hub 1-0:1.0: USB hub found
[    1.096115] hub 1-0:1.0: 6 ports detected
[    1.096171] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.096180] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.096201] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.096216] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.096235] ehci_hcd 0000:00:13.2: debug port 1
[    1.096247] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfcffa800
[    1.108024] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.108070] usb usb2: configuration #1 chosen from 1 choice
[    1.108091] hub 2-0:1.0: USB hub found
[    1.108100] hub 2-0:1.0: 6 ports detected
[    1.108152] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.108167] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.108175] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.108200] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.108220] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfcffe000
[    1.168058] usb usb3: configuration #1 chosen from 1 choice
[    1.168077] hub 3-0:1.0: USB hub found
[    1.168090] hub 3-0:1.0: 3 ports detected
[    1.168128] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.168136] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.168159] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.168174] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfcffd000
[    1.228061] usb usb4: configuration #1 chosen from 1 choice
[    1.228088] hub 4-0:1.0: USB hub found
[    1.228101] hub 4-0:1.0: 3 ports detected
[    1.228148] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.228158] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.228183] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.228200] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfcffc000
[    1.288062] usb usb5: configuration #1 chosen from 1 choice
[    1.288086] hub 5-0:1.0: USB hub found
[    1.288095] hub 5-0:1.0: 3 ports detected
[    1.288141] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.288149] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.288170] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.288184] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfcffb000
[    1.348058] usb usb6: configuration #1 chosen from 1 choice
[    1.348086] hub 6-0:1.0: USB hub found
[    1.348093] hub 6-0:1.0: 3 ports detected
[    1.348142] uhci_hcd: USB Universal Host Controller Interface driver
[    1.348209] PNP: No PS/2 controller found. Probing ports directly.
[    1.348527] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.348538] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.348614] mice: PS/2 mouse device common for all mice
[    1.348690] rtc_cmos 00:03: RTC can wake from S4
[    1.348718] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.348743] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.348839] device-mapper: uevent: version 1.0.3
[    1.348922] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.349051] device-mapper: multipath: version 1.1.0 loaded
[    1.349053] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.349169] EISA: Probing bus 0 at eisa.0
[    1.349200] Cannot allocate resource for EISA slot 8
[    1.349202] EISA: Detected 0 cards.
[    1.349391] cpuidle: using governor ladder
[    1.349393] cpuidle: using governor menu
[    1.349837] TCP cubic registered
[    1.349978] NET: Registered protocol family 10
[    1.350388] lo: Disabled Privacy Extensions
[    1.350690] NET: Registered protocol family 17
[    1.350704] Bluetooth: L2CAP ver 2.13
[    1.350705] Bluetooth: L2CAP socket layer initialized
[    1.350708] Bluetooth: SCO (Voice Link) ver 0.6
[    1.350709] Bluetooth: SCO socket layer initialized
[    1.350738] Bluetooth: RFCOMM TTY layer initialized
[    1.350740] Bluetooth: RFCOMM socket layer initialized
[    1.350742] Bluetooth: RFCOMM ver 1.11
[    1.350763] powernow-k8: Found 1 AMD Phenom(tm) 9650 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    1.350791] powernow-k8:    0 : pstate 0 (2300 MHz)
[    1.350793] powernow-k8:    1 : pstate 1 (1150 MHz)
[    1.351432] Using IPI No-Shortcut mode
[    1.351479] PM: Resume from disk failed.
[    1.351488] registered taskstats version 1
[    1.351598]   Magic number: 5:260:397
[    1.351619] mem random: hash matches
[    1.351671] rtc_cmos 00:03: setting system clock to 2009-12-17 20:21:58 UTC (1261081318)
[    1.351673] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.351675] EDD information not available.
[    1.400550] ata3: SATA link down (SStatus 0 SControl 300)
[    1.564016] ata2: softreset failed (device not ready)
[    1.564020] ata2: applying SB600 PMP SRST workaround and retrying
[    1.568506] ata4: softreset failed (device not ready)
[    1.568509] ata4: applying SB600 PMP SRST workaround and retrying
[    1.660006] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    1.728021] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.728857] ata2.00: ATAPI: HL-DT-ST DVD-ROM DH20N, A102, max UDMA/100, ATAPI AN
[    1.730222] ata2.00: configured for UDMA/100
[    1.732517] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.734686] ata4.00: ATAPI: PLDS DVD+/-RW DH-16AAS, JD11, max UDMA/100, ATAPI AN
[    1.735757] ata4.00: configured for UDMA/100
[    1.828657] usb 4-1: configuration #1 chosen from 1 choice
[    1.964016] usb 5-1: new low speed USB device using ohci_hcd and address 2
[    1.968017] ata1: softreset failed (device not ready)
[    1.968020] ata1: applying SB600 PMP SRST workaround and retrying
[    2.132025] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.149045] usb 5-1: configuration #1 chosen from 1 choice
[    2.158865] ata1.00: ATA-8: ST3320418AS, CC44, max UDMA/133
[    2.158868] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.198220] ata1.00: configured for UDMA/133
[    2.212108] scsi 0:0:0:0: Direct-Access     ATA      ST3320418AS      CC44 PQ: 0 ANSI: 5
[    2.212208] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.212237] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.212272] sd 0:0:0:0: [sda] Write Protect is off
[    2.212275] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.212290] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.212384]  sda:
[    2.217267] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM DH20N    A102 PQ: 0 ANSI: 5
[    2.223374] sr0: scsi3-mmc drive: 12x/48x cd/rw xa/form2 cdda tray
[    2.223377] Uniform CD-ROM driver Revision: 3.20
[    2.223440] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.223471] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.225930] scsi 3:0:0:0: CD-ROM            PLDS     DVD+-RW DH-16AAS JD11 PQ: 0 ANSI: 5
[    2.231465] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.231523] sr 3:0:0:0: Attached scsi CD-ROM sr1
[    2.231553] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    2.234637]  sda1 sda2 < sda5 >
[    2.265964] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.395690] Freeing unused kernel memory: 540k freed
[    2.395965] Write protecting the kernel text: 4568k
[    2.396002] Write protecting the kernel read-only data: 1836k
[    2.413530] usb 5-3: new full speed USB device using ohci_hcd and address 3
[    2.502077] usbcore: registered new interface driver hiddev
[    2.511809] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input3
[    2.511887] generic-usb 0003:045E:0047.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.1-1/input0
[    2.511956] usbcore: registered new interface driver usbhid
[    2.511959] usbhid: v2.6:USB HID core driver
[    2.514572] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.514591] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.514621] r8169 0000:02:00.0: setting latency timer to 64
[    2.514655]   alloc irq_desc for 27 on node -1
[    2.514657]   alloc kstat_irqs on node -1
[    2.514669] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    2.515195] eth0: RTL8102e at 0xf8044000, 00:25:64:df:91:98, XID 24a00000 IRQ 27
[    2.532319] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input4
[    2.532378] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:13.0-1/input0
[    2.547191] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input5
[    2.547237] microsoft 0003:045E:00DB.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:13.0-1/input1
[    2.582045] usb 5-3: configuration #1 chosen from 1 choice
[    2.593199] Initializing USB Mass Storage driver...
[    2.593461] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.593526] usb-storage: device found at 3
[    2.593528] usb-storage: waiting for device to settle before scanning
[    2.593537] usbcore: registered new interface driver usb-storage
[    2.593540] USB Mass Storage support registered.
[    3.386747] PM: Starting manual resume from disk
[    3.386750] PM: Resume from partition 8:5
[    3.386752] PM: Checking hibernation image.
[    3.386903] PM: Resume from disk failed.
[    3.419971] EXT4-fs (sda1): barriers enabled
[    3.438277] kjournald2 starting: pid 413, dev sda1:8, commit interval 5 seconds
[    3.438284] EXT4-fs (sda1): delayed allocation enabled
[    3.438287] EXT4-fs: file extents enabled
[    3.478427] EXT4-fs: mballoc enabled
[    3.478440] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.960799] type=1505 audit(1261081321.108:2): operation="profile_load" pid=436 name=/usr/share/gdm/guest-session/Xsession
[    3.962817] type=1505 audit(1261081321.108:3): operation="profile_load" pid=437 name=/sbin/dhclient3
[    3.963078] type=1505 audit(1261081321.108:4): operation="profile_load" pid=437 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.963223] type=1505 audit(1261081321.108:5): operation="profile_load" pid=437 name=/usr/lib/connman/scripts/dhclient-script
[    3.998027] type=1505 audit(1261081321.145:6): operation="profile_load" pid=438 name=/usr/bin/evince
[    4.002449] type=1505 audit(1261081321.148:7): operation="profile_load" pid=438 name=/usr/bin/evince-previewer
[    4.004840] type=1505 audit(1261081321.152:8): operation="profile_load" pid=438 name=/usr/bin/evince-thumbnailer
[    4.016533] type=1505 audit(1261081321.161:9): operation="profile_load" pid=440 name=/usr/lib/cups/backend/cups-pdf
[    4.016850] type=1505 audit(1261081321.161:10): operation="profile_load" pid=440 name=/usr/sbin/cupsd
[    7.598127] usb-storage: device scan complete
[    7.673927] scsi 6:0:0:0: Direct-Access     Motorola RAZRV3xx         2.31 PQ: 0 ANSI: 2
[    7.674323] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    7.693855] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    8.102614] udev: starting version 147
[    8.118193] Adding 9446180k swap on /dev/sda5.  Priority:-1 extents:1 across:9446180k 
[    8.129797] lp: driver loaded but no devices found
[    8.145425] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    8.158228] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.158773] dell-wmi: No known WMI GUID found
[    8.187477] ip_tables: (C) 2000-2006 Netfilter Core Team
[    8.251003] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.257645] Linux agpgart interface v0.103
[    8.402430] EXT4-fs (sda1): internal journal on sda1:8
[    8.695029] __ratelimit: 3 callbacks suppressed
[    8.695032] type=1505 audit(1261102925.840:12): operation="profile_replace" pid=916 name=/usr/share/gdm/guest-session/Xsession
[    8.696234] type=1505 audit(1261102925.840:13): operation="profile_replace" pid=917 name=/sbin/dhclient3
[    8.696488] type=1505 audit(1261102925.840:14): operation="profile_replace" pid=917 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.696632] type=1505 audit(1261102925.844:15): operation="profile_replace" pid=917 name=/usr/lib/connman/scripts/dhclient-script
[    8.699386] type=1505 audit(1261102925.844:16): operation="profile_replace" pid=918 name=/usr/bin/evince
[    8.703549] type=1505 audit(1261102925.848:17): operation="profile_replace" pid=918 name=/usr/bin/evince-previewer
[    8.705972] type=1505 audit(1261102925.852:18): operation="profile_replace" pid=918 name=/usr/bin/evince-thumbnailer
[    8.710655] type=1505 audit(1261102925.856:19): operation="profile_replace" pid=920 name=/usr/lib/cups/backend/cups-pdf
[    8.710975] type=1505 audit(1261102925.856:20): operation="profile_replace" pid=920 name=/usr/sbin/cupsd
[    8.712486] type=1505 audit(1261102925.856:21): operation="profile_replace" pid=921 name=/usr/sbin/tcpdump
[    8.716549] r8169: eth0: link down
[    8.716744] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.167983] nvidia: module license 'NVIDIA' taints kernel.
[    9.167988] Disabling lock debugging due to kernel taint
[    9.214804] ppdev: user-space parallel port driver
[    9.420500] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.420515] nvidia 0000:01:00.0: setting latency timer to 64
[    9.420669] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.42  Tue Oct 20 20:18:32 PDT 2009
[  210.824036] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  210.987059] usb 1-3: configuration #1 chosen from 1 choice
[  211.003743] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  211.038926] usbcore: registered new interface driver ndiswrapper
[  452.125303] usb 1-3: USB disconnect, address 3
[  457.528020] usb 1-3: new high speed USB device using ehci_hcd and address 4
[  457.691181] usb 1-3: configuration #1 chosen from 1 choice

```

---

### Post by tanago on 2009-12-18
ok i have compiled & installed but i get no networks found.why is this,i ran modinfo rt2870sta and my driver is aliased but why i can't find networks.In fact i can find with the 1.4.0.0 driver and why i can't install the firmware (rt2870.bin)

---

### Post by peepingtom on 2009-12-19
hieppo000: Are you now trying to use Ndiswrapper? Either use it or use rt2870sta, not both. Uninstall it. It has taken over as the driver for your rt2870 device. Add ndiswrapper to /etc/modprobe.d/blacklist.conf for good measure.

Beside that, I think this will help:
Have you tried booting without your rt73 device plugged it? Your rt73 device causes the rt73 module, which depends on rt2x00. When rt2x00 loads, rt2870sta doesn't work. 
This means that your rt73 device is preventing your rt2870 device from working.
You need to do this debugging without your rt73 device plugged in :( Save you stuff to a txt file and post it to the net when you're done. Sorry, this will be strenuous :D





Tanago: Post all info requested in the debug section of first post, except modinfo. make sure to do it after plugging in your USB device, don't boot with it plugged in. This makes dmesg way easier to read. Is this a new install or did you upgrade from Jaunty?

About firmware: Karmic comes with the firmware, no need to install it. It's in /lib/firmware

---

### Post by mtxcoll on 2009-12-20
> **smokeyd said:**
> Hi peepingtom and eveyone else,

Thanks peepingtom for the tutorial. It is well written, but I don't get my linksys WUSB100v2 working. I followed your tutorial to compile the driver. It seems you already added the usb id (1737:0078) of this specific networkcard to the driver (you're using the same?). 
The driver compiled fine. I removed the original staging driver and blacklisted the other drivers as directed. When i insert the wusb100v2 into my ubuntu karmic box (new installation), iwconfig directly sees the ra0 card. ifconfig doesn't show it though, and network-manager doesn't show the part for wireless networks at all (after restarting network-manager). 
After using ifconfig ra0 up, the wireless lan card is shown both with iwconfig and ifconfig, and after restarting network-manager, the part for "wireless networks" is present in the nm-applet, but it is shown as disconnected. 
The thing is this is a wireless N adapter, but only wireless G networks are present here. Could this be the problem?

To test a little, I also added ra0 to /etc/network/interfaces with the config which works for another wireless card which is a rt2500usb card. With this config the wusb100v2 card doesn't find any wireless networks either.

I added the debug info as you described in the attachment with the commands I ran (when running that stuff, i didn't have any configuration in /etc/network/interfaces yet other than the default for lo).
 I hop you ca help.
Cheers,

Dolf.

I have the same issue with my Linksys WUSB100 card; while ra0 shows up and I can configure the ESSID manually using the *.dat file, performing '/sbin/iwlist scan' turns up no scan results.

---

### Post by Nadler on 2009-12-20
Thanks for nice tutorial.  
 I have installed latest Ralink drivers but the connection is not stable. Maybe it has something to do with this issue.  
 

 *lala@lapc:~$ **dmesg |grep rt28***
 *[ 17.370376] usbcore: registered new interface driver rt2870*
 *[ 17.375157] Error: Driver 'rt2870' is already registered, aborting...*
 *[ 17.375160] usbcore: error -17 registering interface driver rt2870*
 *lala@lapc:~$ **dmesg |grep rt30***
 *[ 17.366061] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.*
 


 In system log I can see something like this
 *rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1781*
 


 Was the installation of new drivers unsuccessful?  
 Thanks for any help in advance.

---

### Post by peepingtom on 2009-12-20
Nadler: Staging means that it's a very unstable kernel module that can have radical changes at any time. Since you're stuck with that one until Lucid Lynx is released, you'd have to compile your own version to experience it.

Are you using rt3070sta or rt2870? Are you loading rt3070sta manually? If it loads by default, forget about using rt2870sta. The 2 drivers aren't always interchangeable, and you should certainly only have one loaded when they both detect your device.

I need context for your dmesg output, did that happen the first time you plugged in the card after booting? That's the info I want.the whole purpose of asking you to post lsmod |grep rt  was to find out if you have more than one module loaded at the same time after booting. I won't try to help unless you post debug info as outlined in the first post. Follow the procedure re: not booting with the device plugged in, then posting the relevant parts of dmesg.


mtxcoll: Same! Did you upgrade from jaunty? You haven't given much info :( Context!
Try doing what I suggested for tanago below, it might be totally wrong though.

---

### Post by tanago on 2009-12-20
hey peepingtom thanks for the reply here is my code.Oh at first i removed the original "staging" driver because my device wasn't listed when i issue "modinfo rt2870sta" and i copied only the important info in dmesg because it was two pages.:KS

```
nasko@nasko-desktop:~$ cd '/media/Media/web/rt2870/rt2870sta-2300' 
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/media/Media/web/rt2870/rt2870sta-2300/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -fr ../../os/linux/Module.markers
rm -fr ../../os/linux/Module.symvers
rm -fr ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/media/Media/web/rt2870/rt2870sta-2300/os/linux'
rm -rf os/linux/Makefile
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ make
make -C tools
make[1]: Entering directory `/media/Media/web/rt2870/rt2870sta-2300/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/media/Media/web/rt2870/rt2870sta-2300/tools'
/media/Media/web/rt2870/rt2870sta-2300/tools/bin2h
cp -f os/linux/Makefile.6 /media/Media/web/rt2870/rt2870sta-2300/os/linux/Makefile
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/media/Media/web/rt2870/rt2870sta-2300/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/crypt_md5.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/crypt_sha2.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/crypt_hmac.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/crypt_aes.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/crypt_arc4.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/mlme.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_wep.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/action.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_data.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rtmp_init.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_tkip.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_aes.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_sync.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/eeprom.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_sanity.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_info.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_cfg.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_wpa.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/dfs.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/spectrum.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rtmp_timer.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rt_channel.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_profile.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_asic.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_cmd.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/assoc.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/auth.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/auth_rsp.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/sync.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/sanity.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/rtmp_data.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/connect.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/wpa.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../sta/sta_cfg.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/ba_action.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rtusb_io.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rtusb_bulk.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rtusb_data.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/cmm_data_usb.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/ee_prom.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rtmp_mcu.o
  CC [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/../../common/rtusb_dev_id.o
  LD [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /media/Media/web/rt2870/rt2870sta-2300/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ sudo make install
make -C /media/Media/web/rt2870/rt2870sta-2300/os/linux -f Makefile.6 install
make[1]: Entering directory `/media/Media/web/rt2870/rt2870sta-2300/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /media/Media/web/rt2870/rt2870sta-2300/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.28-11-generic
make[1]: Leaving directory `/media/Media/web/rt2870/rt2870sta-2300/os/linux'
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ sudo modprobe rt2870sta
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

ra0       No scan results

nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ lsusb
Bus 002 Device 003: ID 10d6:1101 Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player
Bus 002 Device 002: ID 1737:0078 Linksys 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 15d9:0a33  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:dd:5e:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:248 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5104 (5.1 KB)  TX bytes:5104 (5.1 KB)

ra0       Link encap:Ethernet  HWaddr 00:1e:e5:ed:f1:ad  
          inet6 addr: fe80::21e:e5ff:feed:f1ad/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2952 (2.9 KB)

nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ lsmod
Module                  Size  Used by
rt2870sta             557676  1 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  15620  0 
pcspkr                 10496  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usb_storage            82880  1 
usbhid                 42336  0 
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ dmesg
[  767.960020] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  768.122792] usb 2-2: configuration #1 chosen from 1 choice
[  768.123882] 
[  768.123884] 
[  768.123885] === pAd = f8175000, size = 482916 ===
[  768.123887] 
[  768.124016] <-- RTMPAllocAdapterBlock, Status=0
[  772.646903] <-- RTMPAllocTxRxRingMemory, Status=0
[  772.648822] -->RTUSBVenderReset
[  772.648990] <--RTUSBVenderReset
[  772.930974] Key1Str is Invalid key length(0) or Type(0)
[  772.931008] Key2Str is Invalid key length(0) or Type(0)
[  772.931041] Key3Str is Invalid key length(0) or Type(0)
[  772.931074] Key4Str is Invalid key length(0) or Type(0)
[  772.931626] 1. Phy Mode = 5
[  772.931629] 2. Phy Mode = 5
[  772.954734] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  772.964478] 3. Phy Mode = 9
[  772.975105] MCS Set = ff 00 00 00 01
[  772.979353] <==== rt28xx_init, Status=0
[  772.980853] 0x1300 = 00064300
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:19:66:dd:5e:94
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:29:ae:68:8e:fc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 00:1e:e5:ed:f1:ad
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.0.0 multicast=yes wireless=Ralink STA
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

ra0       No scan results

nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ lsb_release -d
Description:    Ubuntu 9.04
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ uname -mr
2.6.28-11-generic i686
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                    [ OK ] 
nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

ra0       No scan results

nasko@nasko-desktop:/media/Media/web/rt2870/rt2870sta-2300$ 
```

---

### Post by peepingtom on 2009-12-20
I see no obvious problems, does your adapter show in NetworkManager with no networks, or is it not displayed there at all?


Try this after restarting your computer with your adapter unplugged.
Plug in your USB adapter and QUICKLY run the following commands:

sudo ifconfig ra0 up
sudo iwlist ra0 scan

If it works, I suspect that there is some sort of power-saving feature that's putting the card down. 


If iwlist works but it doesn't show up in Networkmanager, post the output of 
```
cat /etc/network/interfaces | grep -v ^#
```


I normally don't use NetworkManager, and the latest version of rt3070sta breaks my ability to use iwlist after a while, unless NetworkManager is running. I'm still testing this, I barely use wireless though so i'm not putting a lot of effort into it.

---

### Post by Nadler on 2009-12-20
> **peepingtom said:**
> Nadler: Staging means that it's a very unstable kernel module that can have radical changes at any time. Since you're stuck with that one until Lucid Lynx is released, you'd have to compile your own version to experience it.

Are you using rt3070sta or rt2870? Are you loading rt3070sta manually? If it loads by default, forget about using rt2870sta. The 2 drivers aren't always interchangeable, and you should certainly only have one loaded when they both detect your device.

I need context for your dmesg output, did that happen the first time you plugged in the card after booting? That's the info I want.the whole purpose of asking you to post lsmod |grep rt  was to find out if you have more than one module loaded at the same time after booting. I won't try to help unless you post debug info as outlined in the first post. Follow the procedure re: not booting with the device plugged in, then posting the relevant parts of dmesg.


                                 Peepingtom, sorry now I will be more specific.  
   
 I am using SMCWUSBS-N2 USB card on fresh installation of Kubuntu 9.10 . I supposed that rt2870 driver is suitable for my dongle because I have found ID 083a:b522 in your list.   
 
 **Should I delete rt2870 drivers and install RT3070USB(RT307x) drivers?**
 
 I suppose that Rt3070sta is loaded automatically.  
 
 Output without plugged dongle:  
 lala@lapc:~$ lsmod |grep rt
 parport_pc             37352  1
 parport                40528  3 lp,ppdev,parport_pc
 

 Output with plugged dongle:
 lala@lapc:~$ lsmod |grep rt
 rt3070sta             569480  1
 parport_pc             37352  1
 parport                40528  3 lp,ppdev,parport_pc
 

 Now I have unplugged dongle. Than I have boot computer and  plug-ed dongle.  
 
[php]
lala@lapc:~$ lsusb
Bus 001 Device 003: ID 083a:b522 Accton Technology Corp. EZ Connect N Draft 11n Wireless USB2.0 Adapter
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

lala@lapc:~$ modinfo /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
 filename:       /lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt2870sta.ko
 version:        2.3.0.0                                                                 
 license:        GPL                                                                     
 description:    RT2870 Wireless Lan Linux Driver                                        
 author:         Paul Lin <paul_lin@ralinktech.com>                                      
 srcversion:     5D1E952BFCFC371D31E2EFE                                                 
 alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*                                    
 alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
 alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
 depends:
 vermagic:       2.6.31-16-generic SMP mod_unload modversions
 parm:           mac:rt28xx: wireless mac addr (charp)
 

     
 lala@lapc:~$ dmesg
 …
 
[ 5241.900050] usb 1-2: new high speed USB device using ehci_hcd and address 3                                 
 [ 5242.078378] usb 1-2: configuration #1 chosen from 1 choice                                                  
 [ 5242.102061] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [ 5242.105314] rtusb init --->                                                                                 
 [ 5242.105594]                                                                                                 
 [ 5242.105595]                                                                                                 
 [ 5242.105595] === pAd = ffffc90005192000, size = 598584 ===                                                   
 [ 5242.105596]                                                                                                 
 [ 5242.105598] <-- RTMPAllocAdapterBlock, Status=0                                                             
 [ 5242.106330] usbcore: registered new interface driver rt2870                                                 
 [ 5242.113932] rtusb init --->                                                                                 
 [ 5242.113937] Error: Driver 'rt2870' is already registered, aborting...                                       
 [ 5242.113941] usbcore: error -17 registering interface         driver rt2870                                  
 [ 5242.150041] #                                                                                               
 [ 5242.291285] #                                                                                               
                                                                                          
 [ 5242.431283] #                                                                                               
 [ 5242.451283] #                                                                                               
 [ 5242.475782] <-- RTMPAllocTxRxRingMemory, Status=0                                                           
 [ 5242.477408] -->RTUSBVenderReset                                                                             
 [ 5242.477533] <--RTUSBVenderReset                                                                             
 [ 5242.491284] #                                                                                               
 [ 5242.531284] #                                                                                               
                                  
 [ 5242.821283] #                                                                                               
 [ 5242.841283] #                                                                                               
 [ 5242.860125] I/F(ra0) Key1Str is Invalid key length! KeyLen = 0!                                             
 [ 5242.860139] I/F(ra0) Key2Str is Invalid key length! KeyLen = 0!                                             
 [ 5242.860153] I/F(ra0) Key3Str is Invalid key length! KeyLen = 0!                                             
 [ 5242.860167] I/F(ra0) Key4Str is Invalid key length! KeyLen = 0!                                             
 [ 5242.860691] AntDiversity=0                                                                                  
 [ 5242.860696] 1. Phy Mode = 5                                                                                 
 [ 5242.860697] 2. Phy Mode = 5                                                                                 
 [ 5242.881283] #                                                                                               
 [ 5242.891409] #                                                                                               
 [ 5242.901409] #                                                                                               
 [ 5242.907790] RTMPSetPhyMode: channel is out of range, use first channel=1                                    
 [ 5242.920042] #                                                                                               
 [ 5242.926165] 3. Phy Mode = 9                                                                                 
 [ 5242.930093] #                                                                                               
 [ 5242.938792] MCS Set = ff ff 00 00 01                                                                        
 [ 5242.948045] <==== RTMPInitialize, Status=0                                                                  
 [ 5242.949791] 0x1300 = 00064300                                                                               
 [ 5244.861286] #                                                                                               
 [ 5247.990058] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1016                                    
 [ 5248.801289] #                                                                                               
 [ 5250.091289] #                                                                                               
 [ 5253.209105] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 865                                     
 [ 5253.501290] #                                                                                               
 [ 5253.644520] ra0: no IPv6 routers present                                                                    
 [ 5254.791415] #                                                                                               
 [ 5255.381291] #                                                                                               
  
 [ 5265.371295] #                                                                                               
 [ 5265.511293] #                                                                                               
 [ 5273.210176] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1332                                    
 [ 5273.511298] #                                                                                               
 [ 5275.511299] #                                                                                               
  
 [ 5307.531313] #                                                                                               
 [ 5308.981312] #                                                                                               
 [ 5313.212029] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1554                                    
 [ 5313.531315] #                                                                                               
 [ 5313.971314] #                                                                                               
 
 [ 5369.541337] #                                                                                               
 [ 5369.551335] #                                                                                               
 [ 5373.212166] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1332                                    
 [ 5373.591339] #                                                                                               
 [ 5374.181339] #                                                                                               
 [ 5375.591340] #                                                                                               
 [ 5377.611340] #                                                                                               
 [ 5384.376783] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1151                                    
 [ 5384.376948] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=8)                                        
 [ 5384.471343] #                                                                                               
 [ 5384.481375] #                                                                                               
 [ 5384.491341] #                                                                                               
 [ 5384.501342] #
 [ 5388.560472] __ratelimit: 9 callbacks suppressed
 [ 5388.560475] type=1503 audit(1261318667.345:26): operation="open" pid=2410 parent=886 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
 [ 5388.591861] type=1503 audit(1261318667.386:27): operation="open" pid=2412 parent=2410 profile="/usr/lib/NetworkManager/nm-dhcp-client.action" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
 [ 5388.841392] type=1503 audit(1261318667.635:28): operation="open" pid=2413 parent=2410 profile="/usr/lib/NetworkManager/nm-dhcp-client.action" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/etc/ld.so.preload"
 [ 5390.766614] Rcv Wcid(1) AddBAReq
 [ 5390.766617] Start Seq = 00000003
 [ 5422.481358] #
 [ 5449.041368] #
 [ 5453.730890] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1007
 [ 5489.911390] #
 [ 5493.733700] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 835
 [ 5544.576793] Rcv Wcid(1) AddBAReq
 [ 5544.576797] Start Seq = 00000031
 [ 5544.900158] #
 [ 5548.741284] #
 [ 5551.061170] Rcv Wcid(1) AddBAReq
 [ 5551.061174] Start Seq = 000000b9
 [ 5553.738648] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1230
 [ 5554.520168] #
 [ 5557.531288] #
 

 lala@lapc:~$ ifconfig
 

 ra0       Link encap:Ethernet  HWaddr 00:13:f7xx:xx:xx
           inet addr:192.168.xx.xx  Bcast:192.168.xx.xx  Mask:255.255.xx.xx
           inet6 addr: fe80::213:xx:xx:xx/xx Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:8823 errors:0 dropped:0 overruns:0 frame:0
           TX packets:1206 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:2353729 (2.3 MB)  TX bytes:105650 (105.6 KB)
 

 

 lala@lapc:~$ iwconfig
 

 

 ra0       RT2870 Wireless  ESSID:"wifi"  Nickname:"RT2870STA"
           Mode:Managed  Frequency=2.447 GHz  Access Point: 00:13:xx:xx:xx:xx
           Bit Rate=108 Mb/s
           RTS thr:off   Fragment thr:off
           Link Quality=94/100  Signal level:-70 dBm  Noise level:-81 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
  
 lala@lapc:~$ lsmod |grep rt
 rt3070sta             569480  1
 parport_pc             37352  1
 parport                40528  3 ppdev,lp,parport_pc
 

 lala@lapc:~$ cat /etc/network/interfaces
 auto lo
 iface lo inet loopback
 

 

[/php]

---

### Post by mtxcoll on 2009-12-20
> **peepingtom said:**
> Nadler: Staging means that it's a very unstable kernel module that can have radical changes at any time. Since you're stuck with that one until Lucid Lynx is released, you'd have to compile your own version to experience it.

Are you using rt3070sta or rt2870? Are you loading rt3070sta manually? If it loads by default, forget about using rt2870sta. The 2 drivers aren't always interchangeable, and you should certainly only have one loaded when they both detect your device.

I need context for your dmesg output, did that happen the first time you plugged in the card after booting? That's the info I want.the whole purpose of asking you to post lsmod |grep rt  was to find out if you have more than one module loaded at the same time after booting. I won't try to help unless you post debug info as outlined in the first post. Follow the procedure re: not booting with the device plugged in, then posting the relevant parts of dmesg.


mtxcoll: Same! Did you upgrade from jaunty? You haven't given much info :( Context!
Try doing what I suggested for tanago below, it might be totally wrong though.

Hi peepingtom,

Sorry I didn't provide the files you indicated earlier. I have a tarball with all the relevant outputs. These were taken when the card was inserted before bootup.

I upgraded from Intrepid, but in the process I reformatted my root partition so I don't think it's a legacy issue. 

I'll go ahead and try your suggestion to see if it does anything. **Update:** Booting without the network card, then inserting the card and immediately running "ifconfig ra0 up; iwlist scan" didn't work.

---

### Post by hieppo000 on 2009-12-20
> **peepingtom said:**
> hieppo000: Are you now trying to use Ndiswrapper? Either use it or use rt2870sta, not both. Uninstall it. It has taken over as the driver for your rt2870 device. Add ndiswrapper to /etc/modprobe.d/blacklist.conf for good measure.

Beside that, I think this will help:
Have you tried booting without your rt73 device plugged it? Your rt73 device causes the rt73 module, which depends on rt2x00. When rt2x00 loads, rt2870sta doesn't work. 
This means that your rt73 device is preventing your rt2870 device from working.
You need to do this debugging without your rt73 device plugged in :( Save you stuff to a txt file and post it to the net when you're done. Sorry, this will be strenuous :D


Not strenous, just a little frustrating..but its ok..at least i have my backup working for a bit.  Here is all the information after booting it without the 54g card.  it doesnt seem to recognize it even though the blue light shows.  Any help is appreciated.  

I uploaded all the relevant information.  sorry the dmseg one is long.
let me know what you think...thanks in advance merry xmas

---

### Post by peepingtom on 2009-12-20
Hey I'm just some guy on the Internet, no need to apologise ;)

Nadler: 

You're currently using rt3070sta, not rt2870sta. To try using rt2870sta instead, 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
add rt3070sta to the list, save and restart (without the device plugged in please, just to make things easier). If it doesn't work, post dmesg again :( The output will be different this time since you'll be running rt2870sta not rt3070sta.


I ran modinfo rt3070sta |grep 522 and didn't see your USB Dev ID (083a:b522) listed.
It is of course listed by modinfo rt2870sta
```
modinfo rt2870sta |grep 522
 alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*      
```
In fact it's listed twice, along with a bunch of other adapters. I don't know why this is, I doubt it has any negative effects, though.


It seems that your version of rt3070sta detects your card, but mine wouldn't. I'm running the latest version of rt3070sta, v2.1.2.0. 
Here's a snippet from usb_main_dev.c```
/* module table */
struct usb_device_id rtusb_usb_id[] = {
#ifdef RT3070
	{USB_DEVICE(0x148F,0x3070)}, /* Ralink 3070 */
	{USB_DEVICE(0x148F,0x3071)}, /* Ralink 3071 */
	{USB_DEVICE(0x148F,0x3072)}, /* Ralink 3072 */
	{USB_DEVICE(0x0DB0,0x3820)}, /* Ralink 3070 */
	{USB_DEVICE(0x0DF6,0x003E)}, /* Sitecom 3070 */
	{USB_DEVICE(0x0DF6,0x0042)}, /* Sitecom 3072 */
	{USB_DEVICE(0x14B2,0x3C12)}, /* AL 3070 */
	{USB_DEVICE(0x18C5,0x0012)}, /* Corega 3070 */
	{USB_DEVICE(0x083A,0x7511)}, /* Arcadyan 3070 */
	{USB_DEVICE(0x1740,0x9703)}, /* EnGenius 3070 */
	{USB_DEVICE(0x1740,0x9705)}, /* EnGenius 3071 */
	{USB_DEVICE(0x1740,0x9706)}, /* EnGenius 3072 */
	{USB_DEVICE(0x13D3,0x3273)}, /* AzureWave 3070*/
	{USB_DEVICE(0x1044,0x800D)}, /* Gigabyte GN-WB32L 3070 */
	{USB_DEVICE(0x2019,0xAB25)}, /* Planex Communications, Inc. RT3070 */
	{USB_DEVICE(0x07B8,0x3070)}, /* AboCom 3070 */
	{USB_DEVICE(0x07B8,0x3071)}, /* AboCom 3071 */
	{USB_DEVICE(0x07B8,0x3072)}, /* Abocom 3072 */
	{USB_DEVICE(0x7392,0x7711)}, /* Edimax 3070 */
	{USB_DEVICE(0x1A32,0x0304)}, /* Quanta 3070 */
	{USB_DEVICE(0x1EDA,0x2310)}, /* AirTies 3070 */
	{USB_DEVICE(0x07D1,0x3C0A)}, /* D-Link 3072 */
	{USB_DEVICE(0x07D1,0x3C0D)}, /* D-Link 3070 */
	{USB_DEVICE(0x07D1,0x3C0E)}, /* D-Link 3070 */
	{USB_DEVICE(0x07D1,0x3C0F)}, /* D-Link 3070 */
	{USB_DEVICE(0x1D4D,0x000C)}, /* Pegatron Corporation 3070 */
	{USB_DEVICE(0x1D4D,0x000E)}, /* Pegatron Corporation 3070 */
	{USB_DEVICE(0x5A57,0x5257)}, /* Zinwell 3070 */
	{USB_DEVICE(0x5A57,0x0283)}, /* Zinwell 3072 */
	{USB_DEVICE(0x04BB,0x0945)}, /* I-O DATA 3072 */
	{USB_DEVICE(0x203D,0x1480)}, /* Encore 3070 */
#endif // RT3070 //
	{ }/* Terminating entry */
```

Your device isn't there. So I wonder how your device ID came to be detected by your version of rt3070sta. Was it added by the Ubuntu team throgh a patch, did you modify it, or is it just removed in the latest version of rt3070sta by Ralink?

Please check if your device is listed by modinfo rt3070sta
You should not have to delete either driver, the only reason I suggested you delete the old version of rt2870 was that I didn't know how to blacklist a specific version of the same driver. This is a totally different driver, blacklist will work.


CHECK OUT THE COMMAND I POSTED BELOW

---

### Post by peepingtom on 2009-12-20
hieppo000:

rt2870sta doesn't even load. Your device is listed by lsusb, but I can't seen any reference to it in dmesg. What's going on here, is this a copy of dmesg before you plugged in the device? I need it in the moments after is has been connected. Same for lsmod etc.

Your device should be detected by your modified version of rt2870sta. Without the dmesg output, I can't tell why it didn't load.

edit: Instead of dmesg, use the "tail -f" commands I posted below. They are easier to read and will allow you to see what's happening in real-time.

---

### Post by peepingtom on 2009-12-20
I've rewritten the debug section to give an explanation of what we're looking for in these outputs. 
tail -f /var/log/syslog 
and
tail -f /var/log/messages
are way easier to read than dmesg. They allow you to read the logs in real-time. You should try them. Run them in expanded terminal windows, so that outputs will fit on 1 line without wrapping.


First we need to know: Was your device detected by the version of rt2870sta included with Karmic, or did you add your USB Device ID to the module you compiled? Remember, you must do the blacklist steps even if you compiled a module. 
Does your device show up in the NetworkManager applet (networking icon in notification area aka "system tray)? 
What is the manufacturer and model number of your WiFi adapter? 
Have you tried to use ndiswrapper? If so, add "ndiswrapper" to /etc/modprobe.d/blacklist.conf . It will conflict with any native drivers.
Are you running a new Karmic install or did you upgrade from Jaunty? This is important because if you've upgraded. some settings may not have gracefully migrated.

For debugging purposes: Turn off your computer, unplug any Ralink-based USB wifi adapters. Turn it on, log in, let it finish booting. Open a terminal and run the command ```
tail -f /var/log/messages
``` Open another terminal and run ```
tail -f /var/log/syslog
```Then plug in your rt2870 device. Observe the outputs, and save them both to a txt file. The reason for turning off the computer is to ensure the device has to reload its firmware, and also to make the messages output easier to read (all messages relavent to your wifi device will occur after running this command) Post the output in this thread along with the output of the following commands, run with your WiFi adapter still connected:
```
ifconfig
iwconfig
```

If ra0 was not listed by ifconfig, run the following commands shortly after inserting the device and post the output:
```
 sudo ifconfig ra0 up
sudo iwlist ra0 scan

```


Also post the output of the following commands. 
```
cat /etc/network/interfaces | grep -v ^#
lsusb
lsmod
modinfo /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
```

The purpose of these queries is to determine: Do you have conflicting drivers loaded? Does your newly compiled module have the correct device IDs? Is your WiFi card functioning without NetworkManager?

When you run lsmod, you're looking to see which modules containing "rt" are loaded. If you have more than rt2870sta, you need to make some changes.

---

### Post by tanago on 2009-12-21
hey peepingtom my device is not working yet i tried to insert it after i have installed the drivers but no sign that any networks are around me.I have to say that i can connect and browse internet in xp.Ifconfig and iwconfig show the same info.What's wrong i can't understand??? :confused:

---

### Post by peepingtom on 2009-12-21
Old, bad advice. Stricken from this server.

---

### Post by peepingtom on 2009-12-21
oo

---

### Post by FreedomSound on 2009-12-22
I have my usb key works with your help on my Ubuntu Karmic Koala.

For those have some problems with D-Link Wireless N USB MINI ADAPTER DWA-140, please use the rt3070sta v2.1.2.0 driver.
```

$ lsusb 
Bus 001 Device 011: ID 07d1:3c0a D-Link System 

```

It works perfectly.

You just have too follow this original howto and just change rt3070 instead of rt2870.

You must to blacklist rt2800usb rt2x00usb rt2x00lib and rt2870sta modules

Test with insmod and perform this test with deleting the original karmic's module.

I made some steps to follow in the french wiki.
[http://doc.ubuntu-fr.org/dwa-140#d-link_dwa-140_b2](http://doc.ubuntu-fr.org/dwa-140#d-link_dwa-140_b2)

Thanks.

---

### Post by peepingtom on 2009-12-22
Cool, rt3070 and rt2870 devices are very similar and it's a source of great confusion.
One thing to notice, many of the text strings in the rt3070sta haven't been changed: they reference rt2870sta.

I'll be sure to put a bigger emphasis on properly identifying chipsets!

Thanks for your help, your instructions look nicer than mine

---

### Post by Sumo74 on 2009-12-23
Hey peepingtom

I have ran into same errors here also. Following all the steps on a New Install of Ubuntu 9.10, and I can get the NetworkManager to detect the Linksys card, but it won't allow it to connect to anything other than two old connections I have set to auto-connect (I have deleted them several times, but am too lazy to find the source of them and remove them completely). Here is the info I can give you on it:

Once I ran the lsusb command:
> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 1737:0078 Linksys 
Bus 002 Device 003: ID 064e:a133 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsmod:
> Module                  Size  Used by
rt2870sta             554780  1 
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
ecb                     2524  2 
joydev                 10272  0 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_realtek   203328  1 
iptable_filter          3100  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_dummy           2656  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
acer_wmi               15936  0 
psmouse                56500  0 
serio_raw               5280  0 
ath9k                 258744  0 
mac80211              181076  1 ath9k
led_class               4096  2 acer_wmi,ath9k
ath                     8060  1 ath9k
cfg80211               93052  3 ath9k,mac80211,ath
atl1c                  30880  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  2 
drm                   159584  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

modinfo:
> filename:       /lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.3.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     00C3911B1A422F39B270562
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.31-16-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

ifconfig:
> ra0       Link encap:Ethernet  HWaddr 00:25:9c:b8:00:bf  
          inet6 addr: fe80::225:9cff:feb8:bf/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:45648 (45.6 KB)
iwconfig:
> ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So, it seems as though the driver is installed and working, but something it blocking it access to any access point. When I was watching the output for the 
[FONT=monospace]tail -f command, it looks like it is trying to connect, but it just can't get past a certain point and then it deactived because of it.

Hopefully there is a fix for this, because I have ran out of ideas. 

The only other tidbit of information I can give you is that my PCI-card for my Acer Labtop, is running through the driver ath9k, so I thought it if we blocked that, we could then be able to access any network with the Linksys card, but the more I think about it, the less likely that seems.
[/FONT]

---

### Post by peepingtom on 2009-12-23
Hey,


Don't worry about your Atheros card, it won't cause a problem with rt2870sta.

I think many problems are being caused by people misidentifying their chipsets. 

Many of Ralink's drivers are very similar, and they seem to almost work with incompatible chips.

I've removed your USB device ID from the tutorial. Common wisdom isn't always right, I suppose some of those particular Linksys WUSB adapters use a different chipset, even within the same revision.

You should try using rt3070sta. Someone had success with that in this thread.
[http://ubuntuforums.org/showthread.php?t=1236955](http://ubuntuforums.org/showthread.php?t=1236955)
The process is basically the same, just the filename will be different.

A person a few posts up made a tutorial in French, as well.
[http://ubuntuforums.org/showpost.php?p=8543277&postcount=60](http://ubuntuforums.org/showpost.php?p=8543277&postcount=60)

I think understand why so many cards seem to be "missing" from Ralink's USB Dev ID lists, false positives are very irritating!

You can always verify by opening your adapter, it's just a plastic shell. The WiFi chipset will likely be under an RF shield which you can pry/peek under. Just make sure you put it back in place.

Good luck!

---

### Post by Sumo74 on 2009-12-24
> **peepingtom said:**
> Hey,


Don't worry about your Atheros card, it won't cause a problem with rt2870sta.

I think many problems are being caused by people misidentifying their chipsets. 

Many of Ralink's drivers are very similar, and they seem to almost work with incompatible chips.

I've removed your USB device ID from the tutorial. Common wisdom isn't always right, I suppose some of those particular Linksys WUSB adapters use a different chipset, even within the same revision.

You should try using rt3070sta. Someone had success with that in this thread.
[http://ubuntuforums.org/showthread.php?t=1236955](http://ubuntuforums.org/showthread.php?t=1236955)
The process is basically the same, just the filename will be different.

A person a few posts up made a tutorial in French, as well.
[http://ubuntuforums.org/showpost.php?p=8543277&postcount=60](http://ubuntuforums.org/showpost.php?p=8543277&postcount=60)

I think understand why so many cards seem to be "missing" from Ralink's USB Dev ID lists, false positives are very irritating!

You can always verify by opening your adapter, it's just a plastic shell. The WiFi chipset will likely be under an RF shield which you can pry/peek under. Just make sure you put it back in place.

Good luck!

I did all that, thought I was set, but it still does not want to connect to any network, and my internal card is only set to the g-band (Which is the start of this problems) so is there any other hope out there?

Edit: It finally worked!! A little computer restart will fix everything. So using the rt3070 driver will work with the Linksys USB100 v.2

---

### Post by Hanto on 2009-12-25
[SIZE=4]A person should never pre-suppose that a chipset is the same through-out a Vendor's model number lifetime. For example, one I know to well, the Belkin F5D-8053 currently uses two different chipsets. The earlier versions ( 1-4 ) used the Ralink RT2870 chipsets, however the later version 5 and 6 drivers use the Realtek chipsets.. There is no doubt in my mind that the devices carry different version #s on their plastic shells, but who the hell cares, as my plastic shells are located some 12 feet outside my west facing window and I don't care about opening up the window to bring the damn thing in, just to see the damn #. Plus I would have to remove the weather protection I have them covered up with. Belkin should have changed the model #s when they changed the chipsets. And they are not the only company guilty of such behavior. Any comments to them fall on deaf ears. Ubuntu and apparently Linux in general doesn't really use a good Device Manager like MS Windows does. For that reason alone, Linux will remain a primitive brother to MS for several years to come I bet. 
  The main gist of this comment folks is simply, don't assume one knows what the chipset is, simply because of any one supposed definition. There are threads devoted to the different problems with the Linksys WUSB600N version 1 and version 2 devices. Apparently I must be using the version 1 device as I don't have any problems similar to the issues with the version 2 device.
  My old and quite good D-Link DWA-130 used a Marvell chipset that gave better signal sensitivities and TXPower compared to the present Linksys device, but I stupidly allowed it to be damaged by rain. This is before I started using Ubuntu of any version. Last time I used Linux before this recent Ubuntu usage was back in 2003 Mandrake and that was only for a extremely brief period of time. 
  And the only reason I am continuing to use Ubuntu now is because it yields a better, more stable internet connection using wireless then does Win 7 and Vista especially at my extreme range to access point. Why this is so, I'm not sure, only that it possibly may be related to the bloated nature of the MS operating systems. There is one thing I wish I knew much better and that is the command line structure and commands of Linux in general and Ubuntu in particular. 
  @ peepingtom, I modifed DFS, Carrier Sense, and Multiple Card functions all to YES. That has been working for at least a week on this Belkin device. However I could not for the life of me get Txpower or the Sensitivity to modify up or down. I did the same thing with the Linksys device but for some reason it has been more erratic in its behavior then has the Belkin device. Just wish I had been aware of all this before I drowned the D-Link DWA-130. In general I was happier with the Marvell chipset then I have been with the Ralink chipsets in a MS environment I should add. 
[/SIZE]

---

### Post by amigec on 2009-12-26
I have EW-7711UAN and it works well in managed mode, but I want to put it in monitor mode so I used airmon-ng
Interface       Chipset         Driver
ra0             Ralink 2560    PCI rt2500 (monitor mode enabled). 
But when I use airodump there is nothing. So help.

---

### Post by dswiley on 2009-12-27
Thanks for this thread.  I had to compile USB ID 0e66:0009 for Hawking Technology HWUN2 network adaptor.  I did not see a survey of networks after recompile though.  I had to manually add the SSID and security information.  Then it connected.

---

### Post by mtxcoll on 2009-12-31
> **Sumo74 said:**
> I did all that, thought I was set, but it still does not want to connect to any network, and my internal card is only set to the g-band (Which is the start of this problems) so is there any other hope out there?

Edit: It finally worked!! A little computer restart will fix everything. So using the rt3070 driver will work with the Linksys USB100 v.2

Installing the rt3070 drivers fixed my problem with WUSB100v2. To anyone with a Linksys WUSB100v2, INSTALL RT3070STA, [COLOR="Gray"]NOT RT2870STA[/COLOR], I REPEAT, RT3070STA. You probably have WUSB100v2 if lsusb shows something like

> 
Bus 001 Device 002: ID 1737:0078 Linksys


Instead of modifying config/rtusb_dev_id.c I modified os/linux/usb_main_dev.c. Hopefully that will spare others from the hours of frustration I had trying to get my wireless card to work with the rt2870sta drivers.

**UPDATE: It seems that I spoke too soon. You need to install BOTH the modified RT3070STA driver AND the modified RT2870STA driver or otherwise the ra0 interface won't show up in ifconfig.**

---

### Post by peepingtom on 2010-01-02
**I do not think that is true.** Only one module can be used per device. If rt3070sta was dependent on rt2870sta, it would automatically run rt2870sta

if you run lsmod, the single number you see next to the module's name refers to how many modules a specific module is being used by.


Rt3070sta is based upon rt2870sta, and has some very poorly done string replacement. Its code and log outputs repeatedly reference rt2870sta. This is the only reason I could think for an undocumented dependency. Still, I do not think one exists. 

Mtxcoll, are you running both modules concurrently? I think you are lucky it works for you, you are experiencing favorable race conditions.

[http://en.wikipedia.org/wiki/Race_condition](http://en.wikipedia.org/wiki/Race_condition)

---

### Post by aldolat on 2010-01-02
Hi all!

in my desktop PC I use a Belkin USB Wi-Fi adapter with Ralink 2870 chipset. This adapter came in the same package with the router Belkin.

In this moment I am using Ubuntu 9.04 with a driver compiled by me, because the driver that comes with 9.04 doesn't recognize this chipset.

All works well, but I can't use this adapter on 9.10. Karmic recognizes the adapter and I see some networks around me but my own is not seen by this adapter.

On my laptop, that uses an Intel adapter, I see my own network (and others) without problems.

Can you tell me something about this strange behavior, please?
Why I do not see my network?

[edit]
I tried an adapter of a friend and this adapter is recognized out of the box by Karmic and sees my network.

---

### Post by mtxcoll on 2010-01-02
> **peepingtom said:**
> **I do not think that is true.** Only one module can be used per device. If rt3070sta was dependent on rt2870sta, it would automatically run rt2870sta

if you run lsmod, the single number you see next to the module's name refers to how many modules a specific module is being used by.


Rt3070sta is based upon rt2870sta, and has some very poorly done string replacement. Its code and log outputs repeatedly reference rt2870sta. This is the only reason I could think for an undocumented dependency. Still, I do not think one exists. 

Mtxcoll, are you running both modules concurrently? I think you are lucky it works for you, you are experiencing favorable race conditions.

[http://en.wikipedia.org/wiki/Race_condition](http://en.wikipedia.org/wiki/Race_condition)

Well, I don't want to mess with my configuration too much now that it's working, but what happened was that I made a clean install of Jaunty, and blacklisted the drivers as per your tutorial. I also physically removed the rt2870sta staging driver. I then tried to install rt3070sta alone. After restarting the networking interface and network-manager, running iwconfig showed that an ra0 wireless interface existed, but ifconfig showed no such interface. Network manager was not working at that point.

I then installed rt2870sta as per your tutorial as well; this caused ra0 to show up in ifconfig, and network-manager to successfully scan for ESSIDs and configure my network card.

I don't think both drivers are being used; there must be something that rt3070sta lacks that installing rt2870sta fixes (maybe a shared library function or something?)

I'm sorry I can't provide any more details, as the computer I got this working on is currently packed for shipping. Race condition or not, I think this is worth a shot for anyone who has been struggling to get this working for the specific case of Linksys WUSB100v2.

---

### Post by JayWeb on 2010-01-02
Hi everyone,
 
I have a Sitecom 300N Wireless USB Adapter WL-345.
 
I am unable to get it working with Ubuntu, I think this topic could really help me although I am really stumped over one thing... I cant nail down which chipset driver I should be going for.
 
When I type lsusb all I get is:
ID: 0df6:0042 Sitecom Europe B.V
 
I am trying to work out which chipset I have, I think it is either RT2870 or RT3072 but cant get any absolute information.
 
Can anyone help me out, give me any information on how I can find this out.
 
Thanks!

---

### Post by peepingtom on 2010-01-03
An alternative to this guide: You could try using rt2x00 instead of rt2870sta. This guide was written under the assumption that you already considered doing that. To try this, blacklist rt2870sta and unblacklist all the rt2x00 stuff I mentioned in the guide. I don't have high hopes for this working, but you can try.

I really don't know of a definite way of determining whether a device uses rt2870 or rt3070. I bet there's something in the /dev or /proc FS that could help us here, but i'm only a casual user. You can always open your USB device and carefully pry up the RF shield The only real difference between the 2 drivers is where the USB Device IDs are listed, so you could always try both, just blacklist one or the other. Instead of deleting Ubuntu's staging drivers, you could move them just to be safe. 

In rt2870sta, USB Device IDs are listed @ /RT2870_LinuxSTA_V2.3.0.0/common/rtusb_dev_id.c

In rt3070sta, they are listed @ /2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/usb_main_dev.c

I will this week update the tutorial, adding specific instructions for compiling both rt2870sta and rt3070sta, and mentioning that people CAN try rt2x00. I figure once we get our process ironed out, we'll be able to eliminate enough user error to get some bug reports submitted. I'm thinking about writing a script to automate the configuration/compilation process, Ralink's site uses a stupid PHP downloading system, but the GPL lets us freely redistribute stuff anyway. 


Additionally: given the amount of manhours that have gone into this, maybe some people should put together a list of sites where people can buy USB WiFi adapters with chipsets that are known to work. These things are only like $10 anyway :D

---

### Post by roninhockley on 2010-01-05
Just awesome...TY.

Ron

p.s.  I want a list of stores where these things are only $10...:)

---

### Post by sabino56 on 2010-01-07
First of all - big thanks for great info! This kind of forum/community is really fantastic.
I have a Linksys WSUB100 V2 which I just bought in Nov. I am running Ubuntu 9.10 which was upgraded from 9.04. I have a dual boot system and the wusb100 worked fine w/ WinXP.  Network mgr would not recognize the wusb100 and no wireless connections were shown. I tried running from a LiveCD but same result. 
I used the tutorial to blacklist as shown (no fix) and then load the rt2870 drivers and compile. This resulted in Network mgr showing a wireless but not finding my linksys router. lsmod showed only the rt2870 loading and ifconfig showed a ra0. I collected all the info under the debug section of the tutorial except the step of reseting network mgr to defaults as this machine only has a wireless connection. I can post if anyone interested but the net result is the 3070 drivers worked for me! I blacklisted everything and confirmed nothing was being loaded. I unblacklisted the rt2x00 stuff and rebooted - nothing was loaded, no ra0. Ditto when unblacklisting rt2800. I left rt2870 blacklisted,  moved the 3070 folder from the staging and followed the tutorial process and complied w/ rt3070. 
I added the linksys 0x1737,0x0078 usbid to the ../os/linux/usb_main_dev.c file. I also changed a reference to os_alloc_mem in ./common/rtmp_init.c which I saw in another post (changing (PUTCHAR) to (PUTCHAR *) I noted that this was already changed in same file on the rt2870 download) The make failed to write some file at the end due to not have permission so I ran sudo make and it completed without error. (There were some" bytes bigger than ".. type warnings or errors). As soon as I did the insmod rt3070sta.ko - my wireless was up and running. I rebooted and it still works. Actually - I do not have the rt2x00 or rt2800 stuff blacklisted now as I forgot to reblacklist them when installing rt3070. 

So, for me - the 3070 appears to be the answer for the WUSB100 V.2 which I bought in Nov. 
Thanks again for all the help!

---

### Post by sakuljw on 2010-01-09
[COLOR=Black]Hey peepingtom,
After two days of searching on google to figure out how to get my USB adapter operating properly with ubuntu I finally stumbled on your thread. After trying ndiswrapper, the rt2870 linux driver and having to troubleshoot my compiler after various errors and still no success I simply input the few lines of text into my blacklist, plugged the adapter back in and... "Connected to wireless network" !!! I am currently writing this using the wireless connection that you helped me establish and I can't thank you enough for your help. [SIZE=3]**Others with the Cisco Linksys WUSB100 wireless adapter follow peepingtom's tutorial on blacklisting the other ubuntu drivers!**[/SIZE]
[/COLOR]

---

### Post by lordsemaj on 2010-01-10
Thanks a lot peepingtom! This tutorial worked a treat on my USB Belkin N wireless dongle.  I was having lots of problems with Ndiswrapper before, but this works much better as it is faster and doesn't randomly disconnect!:D Only thing is I had to re-compile and reinstall after I upgraded kernel, but this is a very small inconvenience.

---

### Post by xXx8004 on 2010-01-10
Thank u very much it is working now i black listed it and it worked now:popcorn:

---

### Post by icordoba on 2010-01-12
Hi there,
I have successfully managed to configure my Sitecom USB card thanks to this great tutorial. I anyway can't make it work with my WPA2 wifi network. Is it suppoused to work? It works OK if I open my network without any securing, but I cannot make WEP or WPA2 work.

Here is my debug of wpa_supplicant. Thanks for any help:

root@cervatoh2:~/RT2870_LinuxSTA_V2.3.0.0# wpa_supplicant -ira0 -c/etc/wpa_supplicant.conf -Dwired -dd
Initializing interface 'ra0' conf '/etc/wpa_supplicant.conf' driver 'wired' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
pairwise: 0x8
group: 0x8
ssid - hexdump_ascii(len=15):
     52 65 64 20 49 6e 61 6c 61 6d 62 72 69 63 61      Red Inalambrica 
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='Red Inalambrica'
wpa_driver_wired_init: Added multicast membership with packet socket
Own MAC address: 00:0c:f6:60:e7:eb
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): a1 83 8b fa b2 0b 5b 07 96 33 ed af 26 2c 29 a6
WPS: Build Beacon and Probe Response IEs
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Response Type (2)
WPS:  * UUID-E
WPS:  * Manufacturer
WPS:  * Model Name
WPS:  * Model Number
WPS:  * Serial Number
WPS:  * Primary Device Type
WPS:  * Device Name
WPS:  * Config Methods (0)
WPS:  * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface ra0
Using wired authentication - overriding ap_scan configuration
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Already associated with a configured network - generating associated event
Association info event
State: DISCONNECTED -> ASSOCIATED
Associated to a new BSS: BSSID=01:80:c2:00:00:03
No keys have been configured - skip key clearing
Select network based on association information
Network configuration found for the current AP
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 33 50 f2 02 01 00 00 50 f2 02 01 33 00 50 f2 02
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Associated with 01:80:c2:00:00:03
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Cancelling scan request
EAPOL: startWhen --> 0
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: startWhen --> 0
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: startWhen --> 0
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
EAPOL: startWhen --> 0
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state HELD
EAPOL: enable timer tick
EAPOL authentication completed unsuccessfully
EAPOL: heldWhile --> 0
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: startWhen --> 0
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state HELD
EAPOL: enable timer tick
EAPOL authentication completed unsuccessfully

---

### Post by Royman on 2010-01-16
> **JayWeb said:**
> Hi everyone,
 
I have a Sitecom 300N Wireless USB Adapter WL-345.
 
I am unable to get it working with Ubuntu, I think this topic could really help me although I am really stumped over one thing... I cant nail down which chipset driver I should be going for.
 
When I type lsusb all I get is:
ID: 0df6:0042 Sitecom Europe B.V
 
I am trying to work out which chipset I have, I think it is either RT2870 or RT3072 but cant get any absolute information.
 
Can anyone help me out, give me any information on how I can find this out.
 
Thanks!

You might want to try the **RT3070 **driver instead.
This link saved my life:
[http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044)

---

### Post by gnitram on 2010-01-17
Hi Peeping Tom,
    
  			  	 	 	 	 		 		 			
Unfortunately I realise that what I really needed was to follow the HOwTO here: [http://art.ubuntuforums.org/showthread.php?t=1353044](http://art.ubuntuforums.org/showthread.php?t=1353044) for my Conceptronic N150 dongle, it uses the chipset Rt3070. 

Before  I start I need to find out how to delete the rt2870 driver (if you think this is necessary) which I installed through following this post.

Could you please let me know how I can do this?

Here are some of my terminal logs, I thought may be useful for you:

desktop:~$ uname -r
2.6.31-17-generic-pae
asrock@asrock-desktop:~$ sudo modprobe -r rt2870sta
[sudo] password for asrock: 
FATAL: Module rt2870sta is in use.
asrock@asrock-desktop:~$ 

asrock@asrock-desktop:~$ dmesg |grep rt28
[   15.994027] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.009942] usbcore: registered new interface driver rt2870
[   16.077563] Error: Driver 'rt2870' is already registered, aborting...
[   16.077576] usbcore: error -16 registering interface     driver rt2870

asrock@asrock-desktop:~$ sudo modprobe -r rt2870sta
[sudo] password for asrock: 
FATAL: Module rt2870sta is in use.
asrock@asrock-desktop:~$

---

### Post by leonardtm on 2010-01-17
I have a new 64 bit installation of 9.10 and an Alpha 500mW 802.11n Wireless-N USB adapter.  I had to connect via cable and run the update manager before the lsusb command would work.  Once that was done, blacklisting the rt2x00 drivers solved the problem.  I now have a very fast and stable wireless connection!  Thanks!

---

### Post by bbear1 on 2010-01-17
Hello,

first let me mention that I am using Mint8 which I understand is built on Ubuntu 9.10 Karmic Koala. I have been seeking help via the Mint forums, the Boxee, Linksys and Dlink forums, I have just about given up on Linux and wireless-n and wondered if anyone using Ubuntu 9.10 have seen he problems I have been seeing.

Note that I have tried with both Jaunty and Karmic (installed side-by side on the same PC), both have the same issues.

I am using a linksys WUSB600N V2 USB adapter. I have had it *working* for a few weeks connecting to my Dlink DIR-825 dual band wireless router using the 5ghz band using WPA2 encryption. I have installed the latest rt3572 drivers from the Ralink website. (ran 'make', 'make install', etc, I am not using ndiswrapper)

By *working* I can say that it connects at 270Mbps every time, I can surf the net, no problem. I can transfer a 3Gb file across from my Windows share - no problem. What I am having issues is playing AAC audio files from my windows share. I hear 'glitches', points while the music is playing where the sound cuts out for 2 to 3 seconds.

All I have discovered so far is that every time this happens, Wireshark reports 'TCP: Retransmission' events.

I understand this could mean there was a problem with the wireless connection but at the moment I have my Linux box and my Dlink router in the same room. network-manager reports a 100% connection and no receive and no transmit errors and no collisions. I do not have any sources of interference (e.g. microwave oven) nearby.

In terms of players, I have tries Gnome Mplayer, VLC and Boxee, all exhibit the same problem.

Interestingly, if I move the WUSB600N V2 to Windows box (XP home) and use that to play the same AAC files from my Windows share, it plays perfectly with no glitches in the audio, this is even when the signal is poor) two bars. For this reason I am beginning to think that the WUSB600N V2 and DIR-825 are probably ok and that this is an issue with:

a) Ubuntu Jaunty and Karmic
b) faulty Linux driver from Ralink
c) possible samba related problem

Any help would be very much appreciated

---

### Post by Jackson4christ on 2010-01-17
Salve,

I installed Karmic Xubuntu on a old HP Pavilion which lacked internal Wifi, I received the Linskys WUSB100 v2 for Christmas and have yet to get it to work.  I originally tried using ndiswrapper, but received driver load errors.  So I bit the bullet and compiled my own driver per this tutorial, went OK.  After going through all the instructions Network Manager said that wireless networks were disable, more acknowledgement of WiFi that I'd seen before (See attachment).  This after noon I redid Network Manager per the link given, I then proceeded with the latter part of the tutorial as far as the 

```
sudo ifconfig ra0 up
sudo iwlist ra0 scan
```

part. And somehow managed to get Network Manager to recognize my Wifi device, I tried adding my network directly via SSID, it asked several times for the right WEP key which I hadn't giver correctly.  In the end it did not connect to the network nor did it recognize any other network that should have been visible from my neighbors.  So I restarted to get the debug logs requested.  I ran through all the commands and here's the output:

```
jackson@jackson-Xubuntu:/$ tail -f /var/log/messages
Jan 17 19:02:17 jackson-Xubuntu dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jan 17 19:02:17 jackson-Xubuntu dhcpd: All rights reserved.
Jan 17 19:02:17 jackson-Xubuntu dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jan 17 19:02:18 jackson-Xubuntu dhcpd: Internet Systems Consortium DHCP Server V3.1.2
Jan 17 19:02:18 jackson-Xubuntu dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jan 17 19:02:18 jackson-Xubuntu dhcpd: All rights reserved.
Jan 17 19:02:18 jackson-Xubuntu dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jan 17 19:02:18 jackson-Xubuntu dhcpd: Wrote 0 leases to leases file.
Jan 17 19:02:18 jackson-Xubuntu dhcpd: 
Jan 17 19:02:38 jackson-Xubuntu kernel: [   64.172156] Clocksource tsc unstable (delta = -146776910 ns)
Jan 17 19:05:20 jackson-Xubuntu kernel: [  225.924131] usb 1-1: new full speed USB device using ohci_hcd and address 2
Jan 17 19:05:20 jackson-Xubuntu kernel: [  226.178852] usb 1-1: configuration #1 chosen from 1 choice
```


```
jackson@jackson-Xubuntu:/$ tail -f /var/log/syslog
Jan 17 19:02:20 jackson-Xubuntu ntpdate[1073]: adjust time server 91.189.94.4 offset 0.217656 sec
Jan 17 19:02:22 jackson-Xubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb1
Jan 17 19:02:22 jackson-Xubuntu udev-configure-printer: Failed to get parent
Jan 17 19:02:22 jackson-Xubuntu udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb1/1-0:1.0
Jan 17 19:02:22 jackson-Xubuntu udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb1
Jan 17 19:02:22 jackson-Xubuntu udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 17 19:02:22 jackson-Xubuntu udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 17 19:02:24 jackson-Xubuntu anacron[1281]: Anacron 2.3 started on 2010-01-17
Jan 17 19:02:24 jackson-Xubuntu anacron[1281]: Normal exit (0 jobs run)
Jan 17 19:02:38 jackson-Xubuntu kernel: [   64.172156] Clocksource tsc unstable (delta = -146776910 ns)
Jan 17 19:05:20 jackson-Xubuntu kernel: [  225.924131] usb 1-1: new full speed USB device using ohci_hcd and address 2
Jan 17 19:05:20 jackson-Xubuntu kernel: [  226.178852] usb 1-1: configuration #1 chosen from 1 choice
```

```
jackson@jackson-Xubuntu:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:d0:59:7b:42:bc  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe7b:42bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3445066 (3.4 MB)  TX bytes:184352 (184.3 KB)
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

jackson@jackson-Xubuntu:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jackson@jackson-Xubuntu:/$ sudo ifconfig ra0 up
[sudo] password for jackson: 
ra0: ERROR while getting interface flags: No such device
jackson@jackson-Xubuntu:/$ sudo iwlist ra0 scan
ra0       Interface doesn't support scanning.

jackson@jackson-Xubuntu:/$ cat /etc/network/interfaces | grep -v ^#
auto lo
iface lo inet loopback

jackson@jackson-Xubuntu:/$ lsusb
Bus 001 Device 002: ID 1737:0078 Linksys 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

jackson@jackson-Xubuntu:/$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_maestro3           19364  6 
snd_ac97_codec        101216  1 snd_maestro3
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75296  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9156  1 snd_pcm
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
joydev                 10240  0 
pcmcia                 36808  0 
snd_timer              22276  2 snd_pcm,snd_seq
ip_tables              11692  1 iptable_filter
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
x_tables               16544  1 ip_tables
snd                    59204  18 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  3 snd
yenta_socket           24296  2 
i2c_ali15x3             6336  0 
rsrc_nonstatic         11644  1 yenta_socket
shpchp                 32272  0 
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                   6688  0 
i2c_ali1535             5792  0 
psmouse                56500  0 
lp                      8964  0 
serio_raw               5280  0 
parport_pc             31940  1 
parport                35340  3 ppdev,lp,parport_pc
tulip                  48320  0 
video                  19380  0 
output                  2780  1 video
floppy                 54916  0 
ali_agp                 5148  1 
agpgart                34988  1 ali_agp

jackson@jackson-Xubuntu:/$ modinfo /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
filename:       /lib/modules/2.6.31-17-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.3.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     03011881C9596DEF1F53308
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.31-17-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

jackson@jackson-Xubuntu:/$ 

```

Any help you can give would be great.

Dominus Vobiscum
Jackson

---

### Post by nicholasj on 2010-01-18
Hi,  Thanks for the great tute, have learnt more on this one than anywhere else.  I was duped by a bogus site that said if I buy this ALFA AWUS050NH USB v2 then it will work with BT4 out of the box. Not  Nickname is rt2870sta but airmon-ng says PCI rt2500 driver etc etc  Installed gedit on the new BT4 final on VMware palyer v 3 etc etc  Located the gedit ~/Desktop/*2870*/common/rtusb_dev_id.c  using getit ~root/*2870* and made the necessary changes after putting the driver to the desktop. I must have aset up prolem at desktop is root.  I am not sure how to change this? My device ID was the top one listed in the file so I did not add it again.  Changed the config.mk file OK no problem.  But cannot open the blacklist file   sudo gedit /etc/modprobe.d/blacklist.conf  No matter how I change the directory it will not open.  I know I must be doing something dumb !!!  Any chance you give me a pointer here.  thanks  nick

---

### Post by 762sks on 2010-01-18
Peeps!

I am using Ultimate edition 2.5 64bit, the only thing i did to get this working was to copy the blacklist files and pasted them into the end of the conf file. saved it, closed it out. plugged in the belking usb device and it work! you might just try testing that also! 


hope that helps someone!

---

### Post by 7Hawkeye on 2010-01-18
OMG peepingtom, I'm sooo grateful for this tutorial!!!! After unsuccesfully battling with trying to  compile the drivers myself using the readme that came with the RT2870 drivers, the simple act of adding the code to the blacklist did the trick!

Many, many thanks!  :)

---

### Post by apeterh on 2010-01-18
Thanks for the tutorial - I've just gotten my Belkin F6D4050 to work using the rt3070 drivers (on karmic having updated from jaunty); the usb id from lsusb is 

ID 050d:935b Belkin Components

which i had to add to os/linux/usb_main_dev.c before compiling the driver. I also had to move the rt3070sta.ko module which came with karmic in 

/lib/modules/`uname -r`/kernel/drivers/staging/rt3070

out of the way. Wireless seems to be working fine now.

---

### Post by Glinx on 2010-01-23
Many many thanks, thank you for your time on this. D-Link dwa-160/RE (B1) now working.
Also, cheap Maplin's own brand (UK) WB 300N USB (RT2770/2870) also working after just the blacklisting (Ubuntu 9.10 on both 64bit AMD and 32bit laptop).

---

### Post by woober on 2010-01-25
hi i have followed the tutorial and complied a new driver and it gives me the smooth ride on my wireless. 
THANKS for a god tutorial for this. 
BUT.
then I restart it don't load my new driver as promised in the tutorial. and I'll have to run the commands from the "testing" part in the tutorial:

sudo modprobe -r rt2870sta
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko
sudo /etc/init.d/networking restart
sudo restart network-manager

I have deleted the old driver with 

sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870 

I'm sure there is a way to get the driver to load by default under boot as it will would have done with the original driver I have deleted. but how ?

Please help

my system is Ubuntu 9.10 x86 version.

---

### Post by smokeyd on 2010-01-26
Hey everyone, 
I am already trying for a long time (off and on for more than a month) with two different Linksys WUSB100v2 USB network adapters. I have downloaded and succesfully installed the latest Ralink driver. I have enabled wpa_supplicant and native_wpa_supplicant in the config file before compiling. The kernel module installed without incident and loads automatically when I plugin the usb network adapter. I have disabled the builtin rt2870sta module from Ubuntu (I am running Karmic with the 2.6.31-17 kernel). Ifconfig ra0 shows the interface correctly, as does iwconfig ra0. So everything seems to be ok up to here.
From this point on, I am trying to configure the wireless network using WPA supplicant. But whatever I do, the network device seems to refuse to find any available Access Point. There are several working Wireless Networks here (one unencrypted, open network even, which is from the neighbours). But the wifi card just doesn't find any. "iwlist ra0 scan" doesn't show any networks, and when I monitor wpa_supplicant when ra0 tries to go online, it does a whole bunch of things, but in the end keeps on repeating the following block:

Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
CTRL-EVENT-SCAN-RESULTS
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 5 sec 0 usec

When I use another usb wificard in the same machine (older linksys card), I can go online using wpa_supplicant quickly and without incident, and my laptop (running Ubuntu Karmic as well, but with other hardware) can go online on any of the wireless networks available at my location, so I know the wireless network works...

I tried the same with two different linksys cards, and also tested the linksys cards under windows where they do work. So they aren't broken either.

Some basic info (more in the attachment).

>lsmod|grep rt
rt2870sta             554972  1
exportfs                4412  1 nfsd
agpgart                34988  1 nvidia
parport                35340  2 ppdev,lp

>iwconfig ra0
ra0       Ralink STA  ESSID:"elcyion"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

>sudo iwlist ra0 scan
ra0       No scan results

I hope anyone can help with this problem since I am at the point where the only usefull thing I can do with these things seems to be to see how far they fly from my balcony. :D

Cheers,

Dolf.

---

### Post by alfitch0619 on 2010-01-27
Hi - I have the D-Link DWA-140 Hardware Version B1 Firmware Version 1.30.  The "blacklist" method worked like a charm for me.  However, the device does support 802.11n but is reporting a speed of 54Mb/s.  I can live with this but if I want the "N" speed, should I compile a moduleto get it?

---

### Post by beastrace91 on 2010-02-02
EDIT: Blacklisting the modules and installing the ones from ralink worked like a charm!

Regards,
~Jeff

---

### Post by peepingtom on 2010-02-02
Beastrace: For future reference, you only needed to edit the blacklist.

---

### Post by larytet on 2010-02-04
Blacklisting trick worked for me


Enable monitor mode (work as a sniffer with wireshark)
```

sudo iwconfig ra0 mode monitor channel 4

```
In the sniffer choose interface *ra0* (not USB)
Thank you

---

### Post by peepingtom on 2010-02-04
I'm glad to see this is working for people, i've had terrible experiences with tutorial writing in the past :D

The new version of this tutorial  is around 50% complete, real life stuff is slowing me down. The current version is long-winded, i'm trying to make the new version as concise as possible. It would be great to develop a method using udev so that people don't have to compile kernel modules, because this method breaks whenever a new kernel is released. DKMS would be another alternative although less elegant.

---

### Post by iClouseau88 on 2010-02-07
> **2hot6ft2 said:**
> Worked for mine, at least it's working in Ubuntu Ultimate Edition 2.5 (based on Ubuntu 9.10) by adding the lines
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```
to the blacklist as per peepingtoms instructions.

Before that it would show up under available networks in network manager but it wouldn't make any attempt to connect.

Belkin N Wireless USB Dongle F5D8053 ver. 4001
Chip RT2870
lsusb shows it as
```
ID [COLOR="DarkRed"]**050d:8053**[/COLOR] Belkin Components
```
The part in red is the part to search for to find out what chip yours is.

For those that are using laptops with internal wifi cards and trying to use an external usb wifi dongle, on mine the internal must be on i.e. blue light for any external wifi dongle to work.

Once it connects I have to click on network manager and it will show both adapters are connected then click on disconnect for the internal card. My internal is a Atheros AR928X (Atheros AR5009 Mini PCI Card). The blue light stays on, don't turn it off using the button or it wont work. If I don't disconnect it that way then I can't go anywhere on the Internet.

Thanks peepingtom for the solution to this.

Now if I can get it fully functional in BackTrack 4 Pre-Final including injection and monitoring that will make it a real keeper for my collection.
> For those that are using laptops with internal wifi cards and trying to use an external usb wifi dongle, on mine the internal must be on i.e. blue light for any external wifi dongle to work.

This is very true, even for external adapters.  I spent several hours last night trying to troubleshoot a driver reinstallation via ndiswrapper tutorial at the beginning of the Wireless sub-forum.  Later I stumbled on your suggestion to keep the internal wireless adapter on, in the case of laptops. My laptop has an internal Toshiba miniPCI wireless adapter (802.11b) so I use an external Netgear WN511TA 802.11n PCMCIA adapter card.  I originally disabled the internal adapter in Windows.  This is the major stumbling block that prevents having a wireless connection even though ndiswrapper is on, driver installed and device recognized.  Following this advice, I also went into /etc/modprobe.d/blacklist.conf to remove "blacklist orinoco" and "blacklist orinoco_cs" in order for the wireless connection to be established.  The first term "orinoco" is the driver file for internal Toshiba miniPCI wireless adapter and the second term "orinoco_cs" is the process that controls orinoco.

I would suggest checking /etc/modprobe.d/blacklist.conf to make sure you are not blacklisting the driver (& associated files/modules) of the built-in wireless adapter.

---

### Post by anducks on 2010-02-08
I'm completely new to Ubuntu, and Linux in general.

Anyways, I have a Belkin Enhanced Wireless USB Network Adapter that I'd like to get working.

When I type in lsusb in the terminal, I get:

```
Bus 001 Device 004 Id 050d:935b Belkin Components 
```

I added in the stuff to the blacklist file that the first post says to, but now what do I do?

---

### Post by zachws on 2010-02-17
Truly fantastic work,=D>=D>

Inherited a Dell E1405 with a D-Link branded rt2870.
Went from a questionable copy of Windows to native Lucid A2, 
full N wireless, not to mention compiz. :p

Thanks a ton.

---

### Post by RavanH on 2010-02-21
Just to share what - finally, after half a night trying various fixes from around these forums - worked for me with my Linksys RangePlus WUSB100v2 (ID 1737:0078 Linksys) :

[http://ubuntuforums.org/showthread.php?p=8591348#post8591348](http://ubuntuforums.org/showthread.php?p=8591348#post8591348)

The easy fix (if you have not messed up your original installation too much trying other fixes) basically uses the official kernel module that comes by default (so it should even still work after a kernel update?!) gave me *not only* a working dongle but *also* scanning ability *and* WPA. 

The best result so far! :)

---

### Post by peepingtom on 2010-02-23
Wow thanks a lot, this is the type of sysfs/udev trick I was looking for! Most people shouldn't be compiling their own modules, myself included! I'm going to get some questions answered and replace this tutorial with something simpler!

---

### Post by j2fraser on 2010-02-23
Thanks again for the tutorial. I am having problems. I have a D-Link DWA-140/B2 (which seems to possibly have rt3072 or rt2870 chipsets) and I followed your instructions. Now, mind you, I am ***not*** experienced at compiling things, and I did see some error messages when things rolled by, but it seemed to actually conclude and the insmod command seemed to resolve successfully. Now, when I insert the USB key, I see the following errors in syslog...

> Feb 23 19:54:29 kernel: [ 6740.650038] usb 1-7: new high speed USB device using ehci_hcd and address 3
Feb 23 19:54:30 kernel: [ 6740.815567] usb 1-7: configuration #1 chosen from 1 choice
Feb 23 19:54:30 kernel: [ 6740.895058] rtusb init --->
Feb 23 19:54:30 kernel: [ 6740.895246] 
Feb 23 19:54:30 kernel: [ 6740.895248] 
Feb 23 19:54:30 kernel: [ 6740.895249] === pAd = ffffc900055da000, size = 502624 ===
Feb 23 19:54:30 kernel: [ 6740.895250] 
Feb 23 19:54:30 kernel: [ 6740.895253] <-- RTMPAllocAdapterBlock, Status=0
Feb 23 19:54:30 kernel: [ 6740.896548] usbcore: registered new interface driver rt2870
Feb 23 19:54:30 kernel: [ 6740.920069] #
Feb 23 19:54:30 kernel: [ 6740.940189] #
Feb 23 19:54:30 kernel: [ 6740.970062] #
Feb 23 19:54:30 kernel: [ 6740.990060] #
Feb 23 19:54:30 kernel: [ 6741.010058] #
Feb 23 19:54:30 kernel: [ 6741.030056] #
Feb 23 19:54:30 kernel: [ 6741.050054] #
Feb 23 19:54:30 kernel: [ 6741.070054] #
Feb 23 19:54:30 kernel: [ 6741.090051] #
Feb 23 19:54:30 kernel: [ 6741.110049] #
Feb 23 19:54:30 kernel: [ 6741.130049] #
Feb 23 19:54:30 kernel: [ 6741.150046] #
Feb 23 19:54:30 kernel: [ 6741.170046] #
Feb 23 19:54:30 kernel: [ 6741.190043] #
Feb 23 19:54:30 kernel: [ 6741.210041] #
Feb 23 19:54:30 kernel: [ 6741.230039] #
Feb 23 19:54:30 kernel: [ 6741.250038] #
Feb 23 19:54:30 kernel: [ 6741.279014] <-- RTMPAllocTxRxRingMemory, Status=0
Feb 23 19:54:30 kernel: [ 6741.280785] -->RTUSBVenderReset
Feb 23 19:54:30 kernel: [ 6741.280909] <--RTUSBVenderReset
Feb 23 19:54:30 kernel: [ 6741.300034] #
Feb 23 19:54:30 kernel: [ 6741.320032] #
Feb 23 19:54:30 kernel: [ 6741.340030] #
Feb 23 19:54:30 kernel: [ 6741.360026] #
Feb 23 19:54:30 kernel: [ 6741.380151] #
Feb 23 19:54:30 kernel: [ 6741.410148] #
Feb 23 19:54:30 kernel: [ 6741.608486] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
Feb 23 19:54:30 kernel: [ 6741.608491] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
Feb 23 19:54:30 kernel: [ 6741.608495] 1. Phy Mode = 0
Feb 23 19:54:30 kernel: [ 6741.608497] ERROR!!! NICReadRegParameters failed, Status[=0x00000001]
Feb 23 19:54:30 kernel: [ 6741.614893] ---> RTMPFreeTxRxRingMemory
Feb 23 19:54:30 kernel: [ 6741.614934] <--- RTMPFreeTxRxRingMemory
Feb 23 19:54:30 kernel: [ 6741.614938] !!! rt28xx Initialized fail !!!
Feb 23 19:54:31 kernel: [ 6741.760123] #
Feb 23 19:54:31 kernel: [ 6741.780119] #
Feb 23 19:54:31 kernel: [ 6741.800117] #
Feb 23 19:54:31 kernel: [ 6741.810161] #
Feb 23 19:54:31 kernel: [ 6741.820156] #
Feb 23 19:54:31 kernel: [ 6741.830169] #
Feb 23 19:54:31 kernel: [ 6741.840204] #
Feb 23 19:54:31 kernel: [ 6741.850201] #
Feb 23 19:54:31 kernel: [ 6741.870111] #
Feb 23 19:54:31 kernel: [ 6741.880198] #
Feb 23 19:54:31 kernel: [ 6741.890196] #
Feb 23 19:54:31 kernel: [ 6741.900192] #
Feb 23 19:54:31 kernel: [ 6741.910194] #
Feb 23 19:54:31 kernel: [ 6741.920196] #
Feb 23 19:54:31 kernel: [ 6741.930195] #
Feb 23 19:54:31 kernel: [ 6741.940193] #
Feb 23 19:54:31 kernel: [ 6741.960103] #
Feb 23 19:54:31 kernel: [ 6741.970193] #
Feb 23 19:54:31 kernel: [ 6741.980193] #
Feb 23 19:54:31 kernel: [ 6741.990196] #
Feb 23 19:54:31 kernel: [ 6742.000225] #
Feb 23 19:54:31 kernel: [ 6742.010192] #
Feb 23 19:54:31 kernel: [ 6742.020189] #
Feb 23 19:54:31 kernel: [ 6742.030187] #
Feb 23 19:54:31 kernel: [ 6742.054030] <-- RTMPAllocTxRxRingMemory, Status=0
Feb 23 19:54:31 kernel: [ 6742.055721] -->RTUSBVenderReset
Feb 23 19:54:31 kernel: [ 6742.055846] <--RTUSBVenderReset
Feb 23 19:54:31 kernel: [ 6742.070095] #
Feb 23 19:54:31 kernel: [ 6742.090093] #
Feb 23 19:54:31 kernel: [ 6742.100187] #
Feb 23 19:54:31 kernel: [ 6742.120091] #
Feb 23 19:54:31 kernel: [ 6742.140088] #
Feb 23 19:54:31 kernel: [ 6742.160087] #
Feb 23 19:54:31 kernel: [ 6742.170211] #
Feb 23 19:54:31 kernel: [ 6742.190084] #
Feb 23 19:54:31 kernel: [ 6742.210082] #
Feb 23 19:54:31 kernel: [ 6742.230080] #
Feb 23 19:54:31 kernel: [ 6742.250079] #
Feb 23 19:54:31 kernel: [ 6742.270078] #
Feb 23 19:54:31 kernel: [ 6742.290076] #
Feb 23 19:54:31 kernel: [ 6742.310074] #
Feb 23 19:54:31 kernel: [ 6742.330073] #
Feb 23 19:54:31 kernel: [ 6742.350071] #
Feb 23 19:54:31 kernel: [ 6742.370069] #
Feb 23 19:54:31 kernel: [ 6742.390068] #
Feb 23 19:54:31 kernel: [ 6742.410066] #
Feb 23 19:54:31 kernel: [ 6742.430064] #
Feb 23 19:54:31 kernel: [ 6742.438204] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
Feb 23 19:54:31 kernel: [ 6742.438207] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
Feb 23 19:54:31 kernel: [ 6742.438211] 1. Phy Mode = 0
Feb 23 19:54:31 kernel: [ 6742.438212] ERROR!!! NICReadRegParameters failed, Status[=0x00000001]
Feb 23 19:54:31 kernel: [ 6742.444574] ---> RTMPFreeTxRxRingMemory
Feb 23 19:54:31 kernel: [ 6742.444616] <--- RTMPFreeTxRxRingMemory
Feb 23 19:54:31 kernel: [ 6742.444620] !!! rt28xx Initialized fail !!!

Any helpful thoughts?!?

---

### Post by GrandTheft on 2010-02-24
Same here. (!!! RT2870 Initialized fail !!!) using WUSB100V2 (Linksys)

I used the driver that comes with kernel src 2.6.31, which is reported to be working here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350695](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350695). Damn thing.
Regards, GT

---

### Post by killiekosmos on 2010-02-26
PeepingTom
 
Thanks for the tutorial.  I managed to get my Edimax USB wifi going by following your advice.
 
Regards

---

### Post by drmax on 2010-02-26
peepingtom,
 
Thank you kind sir for your tutorial, helped me to get a dwa-140n b1 going in my first attempt with ubuntu wireless, I'm a total beginner. I hope to one day contribute as meaningfully as you have.
 
drmax

---

### Post by GrandTheft on 2010-02-28
Hey guys, 

it works !

Totally different solution:

[http://ubuntuforums.org/showpost.php...48&postcount=6]("http://ubuntuforums.org/showpost.php?p=8591348&postcount=6")

solved it for me. 

Namely 

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

Finally.

Best regards,
GT

PS: No compiling of kernel or from driver source. Just added the dev ID with the above command using 2.6.32-19-generic
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8894904") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8894904")

---

### Post by RavanH on 2010-03-01
> **GrandTheft said:**
> Hey guys, 

it works !

Totally different solution:

[http://ubuntuforums.org/showpost.php...48&postcount=6]("http://ubuntuforums.org/showpost.php?p=8591348&postcount=6")

solved it for me. 

Namely 

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

Finally.

Best regards,
GT

PS: No compiling of kernel or from driver source. Just added the dev ID with the above command using 2.6.32-19-generic

Yep, that's what i reported to work too... One question: is that enough on your system to make the driver be auto-loaded upon insertion of the USB device? In my experience the fix only made the rt2870sta driver to recognize the USB device. It did not make the system auto-load that driver upon insertion, so I added the driver to be loaded at boot to have it ready when inserting the dongle. 

The original poster of that fix, flash63 , has added this to his tuto too but I wonder if there is a way to make the system auto-load the driver upon inserting and not on boot...

---

### Post by GrandTheft on 2010-03-01
Hey RavanH, 

same here: not auto-recognized.
same solution: load the driver through etc/modules at boot.

I have no idea how to fix it so that the dongle is 'dynamically' (?) modprobed and un-modprobed. I figure one could use a script-based workaround (if present -> modprobe driver), but I don't think that is what you mean..

Press on,
GT

---

### Post by peepingtom on 2010-03-01
edit: duuh I can't read
That's what I'm trying to figure out, I haven't even owned a USB wifi adapter since December though ;)

I can't figure out why you need to run the install command every time

Wouldn't it work to jut add this to /etc/modprobe.d/rt2870sta.conf:
/bin/echo "1234 5678" > /sys/bus/usb/drivers/rt2870/new_id

where the numbers in quotation marks is your USB Dev ID?

Then just add rt2870sta to /etc/modules. This module barely uses any ram anyway, unless the firmware is kept in memory (I thought it was loaded onto the card).

I asked questions about this around the forums a several times over the last couple months, never got a response and I'm too lazy to go on IRC to ask today. Let us know how it goes, please!

Also, has anyone tested this for rt3070sta (substitutng rt2870sta for rt3070sta where appropriate)?

---

### Post by Anokel on 2010-03-01
Greetings, I am having problems getting my wusb100 linksys v2 to work.

I tried this:

                     > Originally Posted by **GrandTheft**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8894911#post8894911")                 
                 [I]Hey guys, 

it works !

Totally different solution:

[http://ubuntuforums.org/showpost.php...48&postcount=6]("http://ubuntuforums.org/showpost.php?p=8591348&postcount=6")

solved it for me. 

Namely 

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

Finally.

Best regards,
GT

**PS: No compiling of kernel or from driver source. Just added the dev ID with the above command using 2.6.32-19-generic**[/I]But I don't have it, can anyone tell me how I can get that version of generic? I am able to access the web from my windows xp os. I'm running windows xp on one harddrive and Ubuntu 9.10 on another harddrive. I can duel boot from either one during startup.

I've been able to connect with a hardline "Ethernet" on Ubuntu just not with wusb100 linksys v2.

There's nothing when I check for (Lo and Eth0) 

I've posted more on the next page.

Thanks in Advance.

---

### Post by Anokel on 2010-03-01
Here's what I get when I try to do what I stated above but don't have that generic.

> anokel@Stardust:~$ echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id
anokel@Stardust:~$ sudo modprobe -rf rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
anokel@Stardust:~$ sudo modprobe rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Could not open '/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt2870/rt2870sta.ko': No such file or directory
anokel@Stardust:~$ dmesg | egrep 'rt28|usb|Phy'
[    0.001243] CPU: Physical Processor ID: 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.236111] usbcore: registered new interface driver usbfs
[    0.236111] usbcore: registered new interface driver hub
[    0.236111] usbcore: registered new device driver usb
[    0.928100] usb usb1: configuration #1 chosen from 1 choice
[    0.986065] usb usb2: configuration #1 chosen from 1 choice
[    1.297246] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.441960] usb 1-2: configuration #1 chosen from 1 choice
[    1.548255] usbcore: registered new interface driver usb-storage
[    1.548350] usb-storage: device found at 3
[    1.548351] usb-storage: waiting for device to settle before scanning
[    1.577862] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    1.740213] usb 1-7: configuration #1 chosen from 1 choice
[    2.117027] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    2.333148] usb 2-1: configuration #1 chosen from 1 choice
[    2.341773] usbcore: registered new interface driver hiddev
[    2.347358] input: HID 1267:c002 as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input4
[    2.347447] generic-usb 0003:1267:C002.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1267:c002] on usb-0000:00:02.0-1/input0
[    2.347464] usbcore: registered new interface driver usbhid
[    2.347467] usbhid: v2.6:USB HID core driver
[    2.637030] usb 2-8: new low speed USB device using ohci_hcd and address 3
[    2.850158] usb 2-8: configuration #1 chosen from 1 choice
[    2.860327] input: USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-8/2-8:1.0/input/input5
[    2.860417] generic-usb 0003:0461:4D16.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:02.0-8/input0
[    6.544171] usb-storage: device scan complete
[    7.283626] usbcore: registered new interface driver ndiswrapper
[    9.900816] rtusb init --->
[    9.900875] usbcore: registered new interface driver rt2870
anokel@Stardust:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

anokel@Stardust:~$


Thanks again.

---

### Post by Anokel on 2010-03-02
Any help would be apprecaited, Any ideas? Comments, Suggestions? Let me know.

Thanks again!:D:popcorn:

---

### Post by Anokel on 2010-03-02
See Below

---

### Post by Anokel on 2010-03-02
Hey guys, I found something out. I must have messed something up while trying to get my wireless to work. When I tried the above code while running a live CD of Ubuntu 9.10 but not installing it, it worked. This is what I got.

> lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now I only have one problem, when I try to access the internet it's asking me for a password to get onto the net. Thing is I don't have a password, I don't need a password to logon when I'm using the same wusb100 right now on windows xp.

So anyone know what it's talking about and how I can fix it, so I can log on without it asking me for a password?

Thanks again.
Anokel

---

### Post by Anokel on 2010-03-02
Arghh, Ok now when I restart my computer I get this when I use iwconfg

> lo        no wireless extensions.

eth0      no wireless extensions

I have to put those codes in the terminal all over again.

Anyone know what could be wrong?

Thanks.

---

### Post by Anokel on 2010-03-02
Ok guys, I followed what Peepingtom suggested after putting all the above code in the terminal.

>  					Originally Posted by **GrandTheft** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8894911#post8894911") 				
 				[I]Hey guys, 

it works !

Totally different solution:

[http://ubuntuforums.org/showpost.php...48&postcount=6]("http://ubuntuforums.org/showpost.php?p=8591348&postcount=6")

solved it for me. 

Namely 

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf

sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig

Finally.

Best regards,
GT

PS: No compiling of kernel or from driver source. Just added the dev ID with the above command using 2.6.32-19-generic[/I]


I then followed his instructions here:

> edit: duuh I can't read
That's what I'm trying to figure out, I haven't even owned a USB wifi adapter since December though :wink:

I can't figure out why you need to run the install command every time

Wouldn't it work to jut add this to /etc/modprobe.d/rt2870sta.conf:
/bin/echo "1234 5678" > /sys/bus/usb/drivers/rt2870/new_id

where the numbers in quotation marks is your USB Dev ID?

Then just add rt2870sta to /etc/modules. This module barely uses any ram anyway, unless the firmware is kept in memory (I thought it was loaded onto the card).

I asked questions about this around the forums a several times over the last couple months, never got a response and I'm too lazy to go on IRC to ask today. Let us know how it goes, please!

Also, has anyone tested this for rt3070sta (substitutng rt2870sta for rt3070sta where appropriate)?
                                                                                                                                    *                                              Last edited by peepingtom; 1 Day Ago at 08:49 AM..                                                           *             
Now I don't have to put the code in every time I boot the computer, the wusb100 linksys v2 is automatically detected.

I just still have one problem I can't figure out. Its asking me for a password to connect to the internet. But I don't require one. So I'm not sure why it's asking me. I'm using the same wusb100 linksys v2 on winxp and I'm doing it without any passwords.

I know it's not my login password, it's asking me for some like network password.

Anyone have any ideas????

Thanks a bunch!!!!!

---

### Post by Anokel on 2010-03-03
**SOLVED**

Okay, finally I fixed it, with no help from anyone here I might add.. :P I mean no live help that is. But by searching the net and thinking with my brain I found out what was wrong.

For some weird reason I didn't need a secure password to connect when I was on windows xp.(I never enter a password for it) However when I was on linux I did need a password.

What I did was I looked up my linksys router information on the net (Because my family didn't know what they did with that information), got the default ip and username password. Logged into my router looked under wireless secure connections and found a secure password. 

I booted up the computer in Ubuntu and entered the password I found and Tada! Works! Now I'm surfing the net on my linux harddrive! Woo hooo!! Internet!!!!

Thanks for all the help!!!!

:popcorn::popcorn::p:p:D:D:KS

---

### Post by Jonah11 on 2010-03-08
This isn't working for me for the Asus N13, even though the Ralink 3070 is supported.  I followed the steps of the tutorial, but after building my ko file I get:

insmod: error inserting 'rt3070sta.ko': -1 Unknown symbol in module

Any idea whats wrong?

Also, there were some errors and warning during make install, let me know if you need info on those.

Thanks,
Jonah

---

### Post by chili555 on 2010-03-08
> **Jonah11 said:**
> This isn't working for me for the Asus N13, even though the Ralink 3070 is supported.  I followed the steps of the tutorial, but after building my ko file I get:

insmod: error inserting 'rt3070sta.ko': -1 Unknown symbol in module

Any idea whats wrong?

Also, there were some errors and warning during make install, let me know if you need info on those.

Thanks,
JonahPlease start a new thread and post, if it's a USB device:```
lsusb
```and if it's a PCI device:```
lspci -nn
```We may be able to get you going easily.

---

### Post by evut on 2010-03-09
Hi,
I have Linux Mint 8 and an Edimax EW-7711UAN 11n 150mbs Wireless High Gain USB Adapter (3070 driver).
I followed the advice in post #23/page 3 by anthonyalbertyn and it worked.
Thanks everyone for helping me to get this device to work!
Eva

---

### Post by smokeyd on 2010-03-17
Like Anokel suggested, I followed [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)
If you follow that guide you will use the standard driver which is included with Ubuntu karmic, instead of the new 2.3.0 version of Ralink. But for my linksys usb100v2 it works with a couple of seconds work!

---

### Post by shorumi on 2010-04-05
Hi, I am a Debian Squeeze user and I am here just to share the results that I´ve got with this great tutorial

I am putting the commands and the results that I got, just follow this and see what you get.

```
root@xxxx:~# lsusb
Bus 002 Device 002: ID 04b3:310c IBM Corp. Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
root@xxxxx:~# apt-cache search firmware-ra
firmware-ralink - Binary firmware for Ralink RT2561, RT2571, RT2661 and RT2671 wireless cards

``````
root@xxxx:~# aptitude install firmware-ralink

```Then I followed the tutorial tips:

To use rt2870sta and blacklist rt2800usb, run the following commands in terminal:
```
root@xxxx:~# vim /etc/modprobe.d/blacklist.conf
```add these lines to the end of the file:
```

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb

```Save the file, then insert your USB WiFi device.

```
root@xxxx:~# lsmod
usbcore                98126  5 rt2870sta,usbhid,ohci_hcd,ehci_hcd

```In my case I have a wireless built-in device and the USB WiFI device, I am using the USB device, so wlan1 

```
root@xxxxx:~# ifconfig -a
wlan0     Link encap:Ethernet  HWaddr 04:19:c7:06:a3:11
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 04:a2:b1:87:73:47
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13036 (12.7 KiB)  TX bytes:12988 (12.6 KiB)

``````
root@xxxx:~# ifconfig wlan1 10.1.1.25 netmask 255.0.0.0 up
```In my case I am using WPA.

```
root@xxxx:~# wpa_passphrase "YOUR SSID" PASSWORD > /etc/wpa_supplicant.conf

root@xxx:~# cat /etc/wpa_supplicant.conf
network={
        ssid="S"
        #psk="12345678"
        psk=438ed0249b0b50db2fe79b6a2abd3542c4fc44847c9ee1bfac67cc5b80c91264
}

```After generate the wpa_supplicant.conf, edit it and remove the commentary '#' from the "psk="12345678"" line.

```
root@xxxx:~# wpa_supplicant -i wlan1 -c /etc/wpa_supplicant.conf -Dwext
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
Trying to associate with 00:21:94:12:8g:88 (SSID='S' freq=2412 MHz)
Associated with 00:21:94:12:8g:88
WPA: Key negotiation completed with 00:21:94:12:8f:88 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:21:94:12:8f:88 completed (auth) [id=0 id_str=]
```Now that you know connection is established, we can run it on background

```
root@xxxxx:~# wpa_supplicant -i wlan1 -c /etc/wpa_supplicant.conf -Dwext -B
```Just try to ping some another machine or a valid IP in your network, if it returns a reply, you got it.


Thanks a lot for this tutorial and I hope to help someone else with my related experience with this USB WiFi device. :guitar:

---

### Post by alliance1975 on 2010-04-05
Followed all commands for compiling the rt2870 from railink. The ubuntu driver worked but only at 56k. After compile and install railink it went up to 108k. the last command," sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870" failed everything. now I am stuck in endless loop of network manager trying to load but it keeps asking for wpa pass phrase. I keep entering but it fails. more time goes by and it asks again. That last command killed it, and it was working.

---

### Post by peepingtom on 2010-04-12
Yeah that was terrible advice for me to give, I've changed the tutorial.

For your particular situation: You could hold shift right before Ubuntu starts to boot, bringing up GRUB and selecting an older version of the kernel. It'll have a working copy of that kernel object you deleted, and you can fix it from there. You could load up Synaptic and reinstall the latest version of the kernel. Sorry about that hardship!


BTW I neglected this thread, didn't make any big updates and don't really plan on it. I don't own this hardware anymore so i'm going to let this thread go fallow. 

[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)
^^ This is the best solution to the USB Device ID problem

---

### Post by adamlm on 2010-05-02
Hi there, I'm a newbie needing help with this.. I've installed Karmic and I've been trying to install ralink drivers for my Opticum GX-301 wifi dongle. No results... I've followed instructions from the first post and I got this:

```

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```ra0 is up, rt2870sta mod is running, but I can't connect to any wifi network.. Did I miss something? Please advice..

---

### Post by ip3t on 2010-05-18
i've the same problem ..
but i've been used linksys wusb54gc v3 as wireless adapter with the rt2870sta driver (v. 2.3.0.0)

I'll try to read the tutorial link above by smokeyd..
any other suggestion?

---

### Post by rencemc on 2010-05-18
I've been screwing with this for months ! I still can't get it to work. The module seems to be compiled and loaded, but if I look at the wireless networks, it list the adapter as "device not ready".

---

### Post by christ8 on 2010-05-27
I have my Belkin F5D8053 V3 (using RT2870_LinuxSTA_V2.3.0.0 driver from Ralink download), working,  using this method on the first post.  However, after reboot, no driver and no network.  Had to do insmod again.  Eventually, I found out that I need to paste rt2870rta.ko into .../staging/rt2870/ folder.  It now works after reboot.

---

### Post by thomagd on 2010-06-08
I have tried everything in this thread and a lot of other threads to try and get my Edimax EW771UTn USB 802.11n working with WPA in 10.04, it worked fine in 9.10 by just blacklisting as per the 1st post.
I have eventually found a fix in another thread, install the kernel from this link and it works perfectly.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/")

---

### Post by MIJ-VI on 2010-06-26
Hi peepingtom.

This portion of your OP...

"[SIZE=3]**Determining which module you should use:**[/SIZE]
[SIZE=2]If a USB WiFi adapter is automatically detected by  rt2870sta, rt3070sta or an rt2x00 module, it has likely been verified to  function by that module's developers. **While the rt2x00 driver has  some support for rt2870 chipsets, it seems that rt2870 and rt3070  chipsets work best when controlled by Ralink's drivers**. Only one of  these modules should be loaded per network adapter.[/SIZE]

To determine which modules control your USB WiFi adapter, insert it and  run the following command in terminal      Code:
     lsmod |grep rt 
 rt2870 devices are supported by Ralink's rt2870 driver (module  rt2870sta) or by the rt2x00 project's driver (modules rt2800usb,  rt2x00lib, rt2x00usb). rt3070 devices are supported by Ralink's rt3070  driver (module rt3070sta)

[SIZE=3]**Blacklisting Modules:**[/SIZE]

To begin,  unplug any Ralink USB WiFi adapters and restart your computer  (or unload the modules).

**To use rt2870sta and blacklist rt2800usb**, run the following  commands in terminal:
     Code:
     gksudo gedit /etc/modprobe.d/blacklist.conf 
add these lines to the end of the file:
     Code:
     blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb 
Save the file, then insert your USB WiFi device."

...*finally* enabled my AirLink101 300N Wireless USB Adaptor Model: AWLL6080 (64 bit Edubuntu 10.04) to access my neighbour's WEP encrypted router via the password he gave me in exchange for refurbishing his relative's Athlon64/Biostar MCP6P M2+ ver. 6.1 machine.

Thanks to your tutorial I can now bundle the AWLL6080 with an Edubuntu 10.04 rig I'm putting together for his family instead of trying to find an Ubuntu-compatible wi-fi adaptor at the Windows-only PC shops downtown.

Thanks again. :)

Gary

---

### Post by LeChacal on 2010-06-28
I have a Linksys WUSB600N v2 and I have the module compiled and load but network manager never finds my network. If I try and manually adding my network it just continually tries to connect but never gets anywhere and then just gives up and says Network Disconnected.
The adapter is sitting 2 feet from the access point and the access point is set to no security. The only other wireless thing I have is my cellphone and it is able to connect to the network. With the same PC and same wireless adapter I am able to connect under Win7 but not under Ubuntu 10.04, I just upgraded from 9.10 under which I had the adapter working. Does anyone have suggestions? Thank you.

---

### Post by psychok9 on 2010-08-12
The network manager show 54mb/s speed.
How can I improve to N-speed/300mb/s max?

---

### Post by shkm on 2010-08-29
Just installed 10.04 and I've been trying to get my Edimax EW-7711UAn working.

Out of the box a wireless interface was detected, but was not given a name and could not find any local networks. After some blacklisting, now running on rt2870sta, it's sort of working. The card picks up local networks now and *attempts* connections, however connections always time out and I'm left with a "disconnected" message. I even tried momentarily disabling WPA2 on the network, so that's definitely not the problem, nor is anything regarding MAC security settings. Additionally, the dongle works fine in a Windows 7 partition.

Details follow.

**lsusb**
```
Bus 001 Device 004: ID 7392:7711 
```

[B]Relevant blacklist.conf
[/B]```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

Edit: Ultimately gave up and switched to another card.

---

### Post by Toast2120 on 2010-09-06
Have an installation of 10.04 with the medialink wireless N adapter (MWN USB 150N). Been reading many of these threads to get this working, hopefully it will. 

iwconfig

wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on



lsusb

Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lsmod | grep rt

rt2870sta             461811  0 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205146  2 rt2x00usb,rt2x00lib
parport_pc             25962  1 
cfg80211              126517  2 rt2x00lib,mac80211
crc_ccitt               1339  2 rt2800usb,irda
agpgart                31724  3 ttm,drm,intel_agp
parport                32635  3 ppdev,parport_pc,lp


My /etc/modprobe.d/blacklist.conf

#rt2800usb
#rt2870sta


Now disabled...I've been switching both of them out for a while, perhaps I'm unlucky?

Annnd... dmesg | grep rt28

[    3.493542] Registered led device: rt2800usb-phy0::radio
[    3.493565] Registered led device: rt2800usb-phy0::assoc
[    3.493585] Registered led device: rt2800usb-phy0::quality
[    3.498903] usbcore: registered new interface driver rt2800usb
[    3.511512] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    3.537863] usbcore: registered new interface driver rt2870
[ 1423.515794] Registered led device: rt2800usb-phy1::radio
[ 1423.515815] Registered led device: rt2800usb-phy1::assoc
[ 1423.515835] Registered led device: rt2800usb-phy1::quality
[ 1850.946944] rt2800usb 1-3:1.0: firmware: requesting rt2870.bin


Hope this is enough information to get my wireless moving.

---

### Post by fhgshfdg on 2010-09-24
I'm having trouble configuring RT2870STA so that it loads the newer, installed module over the old one that came with Ubuntu. When I try to run the following, I get an error informing me .rt2870.bak is not a directory and therefore I cannot move a folder there.

```
sudo mv /lib/modules/`uname -r`/kernel/drivers/staging/rt2870 ~/.rt2870.bak
```

Anyone mind elaborating on this part for me? What exactly are we doing here. Moving the entire ~/rt2870 folder to the "~/.rt2870.bak" folder? Where exactly would this "~/.rt2870.bak" folder be located?

Is there possibly and easier, more straight forward way of deleting the old module we are trying to avoid loading? Thanks!

---

### Post by Jeffreylb94 on 2010-10-08
> **neerajadsul said:**
> Hi,
Does this depend on the Hardware Manufacturer? I mean, do we have to do something additional for each manufacturer?

I will try today with My Siemens USB Gigaset 300 adapter (which I suppose has RT4870 chip).

Thanks a lot !!!

Thanks so much!!!!

---

### Post by aguilla1 on 2011-09-03
I bought an external adapter because my light often does not turn blue.  If it is true it needs to be on, I wasted my $$.
 
AG
 
> **iClouseau88 said:**
> This is very true, even for external adapters. I spent several hours last night trying to troubleshoot a driver reinstallation via ndiswrapper tutorial at the beginning of the Wireless sub-forum. Later I stumbled on your suggestion to keep the internal wireless adapter on, in the case of laptops. My laptop has an internal Toshiba miniPCI wireless adapter (802.11b) so I use an external Netgear WN511TA 802.11n PCMCIA adapter card. I originally disabled the internal adapter in Windows. This is the major stumbling block that prevents having a wireless connection even though ndiswrapper is on, driver installed and device recognized. Following this advice, I also went into /etc/modprobe.d/blacklist.conf to remove "blacklist orinoco" and "blacklist orinoco_cs" in order for the wireless connection to be established. The first term "orinoco" is the driver file for internal Toshiba miniPCI wireless adapter and the second term "orinoco_cs" is the process that controls orinoco.
 
I would suggest checking /etc/modprobe.d/blacklist.conf to make sure you are not blacklisting the driver (& associated files/modules) of the built-in wireless adapter.

---

