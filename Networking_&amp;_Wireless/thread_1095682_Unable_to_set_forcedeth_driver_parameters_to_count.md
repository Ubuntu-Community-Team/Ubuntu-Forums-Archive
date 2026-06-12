---
title: "Unable to set forcedeth driver parameters to counter slow internet"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by Gloria81 on 2009-03-14
I have an Aus M3N78-EM motherboard. The GeForce 8200 chipset handles the wired Ethernet connection. Internet was extremely slow via the wired connection and normal via a wireless connection, also under Windows XP. By experimenting in Windows XP, using a separate network card, I found that my router, provided by my ISP, can only handle 10 MBps connections. By changing the settings in the Windows XP chipset driver to 10 MBps full duplex, I got full speed Internet via the wired connection as well.

When trying to implement the same solution in Ubuntu 8.10 (Intrepid Ibex) I got stuck and need help.

I checked following:
- Networkmanager. Does not allow changing of these settings
- Driver module, I found this is called forcedeth and has version 0.61 on Intrepid Ibex. I could find no interface to change the settings of the hardware via this driver module. According to various posts, the way to pass settings to a driver module is by changing its parameters.
- Driver module source code. I downloaded the nForce driver archive from the NVidia website ([http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)). By looking at the source code I found that the parameters of interest to me are (probably) speed_duplex and autoneg. These are set to 0 and 1 respectively and should be changed to 2 and 0.
- I tried to compile the source code to a module (using the approach from [http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html) only using the header files) but this generated a lot of errors. This blocked the way to make a modified version of the module with different default settings.
- According to various posts, parameters for modules in Ubuntu can be set in the /etc/modprobe.d/options file. I added the most likely entry, a new line with "options forcedeth speed_duplex=2 autoneg=0", but this did not result in a working internet connection
- According to other posts, parameters for modules in Ubuntu can be passed as boot options in the form module.parameter=value. I changed the entry in /boot/grub/menu.lst by adding the two parameters, but at boot they were not recognized and disregarded
- According to still other posts, parameters for modules in Ubuntu should be passed as options to the installer. Some more reading learned me that Ubuntu comes with a Ubiquity script, tying together various Debian installation tools with a nice UI. Little chance to find where to enter the options.

I would appreciate help and can think of two directions:
- How can I compile the forcedeth.c file into a module
- How can I change the default settings of forcedeth without recompiling the module

---

### Post by chili555 on 2009-03-14
Without knowing what errors you encountered, it's hard to say what you need to do to correctly compile from a tarball.

The usual way to change parameters on an ethernet card is a command line tool called *ethtool.* I suggest opening a terminal and doing:```
sudo ethtool -s eth0 speed 10 duplex full autoneg on
```If that fixes your problem, we can make it permanent.

You can learn more about *ethtool* by reading the handy manual:```
man ethtool
```

---

### Post by Gloria81 on 2009-03-15
Hi Chili555,

Great! This brings my wired internet to normal speed. Please advise how to make this permanent.

This was what "sudo ethtool eth0" returned after the command you advised:
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 3
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

---

### Post by chili555 on 2009-03-25
> Please advise how to make this permanent.Oops! I apologize for missing your request. Please do:```
sudo gedit /etc/rc.local
```Add a line above *exit 0:*```
ethtool -s eth0 speed 10 duplex full autoneg on
```Check your work twice, save and close. Upon boot, the changes will be applied automagically.

---

