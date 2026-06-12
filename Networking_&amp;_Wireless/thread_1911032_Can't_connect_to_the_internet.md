---
title: "Can't connect to the internet"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by Frank Einstein's Bride on 2012-01-18
Best preface this by mentioning I'm not the most tech savy of people.

Slight intro:

   I have a new laptop(hp pavilion dm1 4020sa), which as of last night  no longer connects to the internet. I'm relativly new to linux/ubuntu  this being only the second computer I have to run Ubuntu and the first  one I installed it on myself. It's been an uphill struggle from the  start, firstly with partitions, then when I'd reached the milestone of  installing an os myself(Ubuntu 11.10) for the first time, there was amd  unsupported hardware watermark on the screen and the wireless connecton  worked, but very slowly if at all, frequently disconnecting.  Last night  the watermark was finally removed, I then set about fixing the  wireless, my atempts at fixing may have done more harm than good  however.

MEat of the problem:
 
   I no longer can connect to the internet, I was folling the  instructions of 23senick(SAme model of compter and same problem as him)  in this thread:
 [http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)
  I got as far as blacklisting the drivers and rebooting, but having no  internet connection I can't install those three drivers/packages/things  from the software centre. 

Any help would be appreciated, am I even going about fixing this the right way?

---

### Post by Frank Einstein's Bride on 2012-01-18
briefly got a connection earlier and was able to install those three items from the software centre, however it appears to have made no change whatso ever, after installing them the internet connection was slow and prone to disconnecting. After restarting the computer the connection is gone. Wicd network manager is saying no networks detected. 


WIreless card is a broadcom 4313

---

### Post by ts3 on 2012-01-18
> **Frank Einstein's Bride said:**
> briefly got a connection earlier and was able to install those three items from the software centre, however it appears to have made no change whatso ever, after installing them the internet connection was slow and prone to disconnecting. After restarting the computer the connection is gone. Wicd network manager is saying no networks detected. 


WIreless card is a broadcom 4313

Would you mind posting the output of the following two commands?

```
lspci -k
nm-tool
```

I had a problem with the same wireless chipset (broadcom 4313) and it turned out to be conflicting drivers (solution is in fact described in the thread you linked to in your first post).

Thanks and cheers :)

---

### Post by Frank Einstein's Bride on 2012-01-19
Thanks for taking the time to help, heres the result of those commands:

>  david@Deep-Thought:~$ lspci -k  
 00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex  
 	Subsystem: Advanced Micro Devices [AMD] Family 14h Processor Root Complex  
 00:01.0 VGA compatible controller: ATI Technologies Inc Device 9806  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: radeon  
 	Kernel modules: radeon  
 00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: HDA Intel  
 	Kernel modules: snd-hda-intel  
 00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: ahci  
 	Kernel modules: ahci  
 00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: ohci_hcd  
 00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: ehci_hcd  
 00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: ohci_hcd  
 00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: ehci_hcd  
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: piix4_smbus  
 	Kernel modules: sp5100_tco, i2c-piix4  
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: HDA Intel  
 	Kernel modules: snd-hda-intel  
 00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)  
 	Subsystem: Hewlett-Packard Company Device 3387  
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)  
 00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 00:15.1 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)  
 	Kernel driver in use: pcieport  
 	Kernel modules: shpchp  
 00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: ohci_hcd  
 00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: ehci_hcd  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3  
 	Kernel driver in use: k10temp  
 	Kernel modules: k10temp  
 00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4  
 00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6  
 00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5  
 00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7  
 03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)  
 	Subsystem: Hewlett-Packard Company Device 1795  
 	Kernel modules: wl, bcma, brcmsmac  
 07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: r8169  
 	Kernel modules: r8169 


 

 >  
 NetworkManager Tool  
 

 State: disconnected  
 

 - Device: eth0 -----------------------------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             unavailable  
   Default:           no  
   HW Address:        10:1F:74:B7:48:FB  
 

   Capabilities:  
     Carrier Detect:  yes  
     Speed:           10 Mb/s  
 

   Wired Properties  
     Carrier:         off  
 

---

### Post by ts3 on 2012-01-20
> **Frank Einstein's Bride said:**
> Thanks for taking the time to help, heres the result of those commands
Sorry about long time without response, I didn't have access to my ubuntu stuff & I was also secretly hoping someone more experienced might step in.  I am a newbie myself but I had issues with the same chipset (BCM4313 (14e4: 4727) as you and had to spend some time figuring things out 

Basically, the output of lspci -k shows you the kernel modules/drivers.  For wireless yours is

[FONT="Courier New"]03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01) 
Subsystem: Hewlett-Packard Company Device 1795 
Kernel modules: wl, bcma, brcmsmac [/FONT]

There is no driver loaded, you need to have "kernel driver in use: wl"   

wl (this is WL) is the driver that works for this chipset.  Please uninstall all b43 drivers if you have installed any (Software Center, search for b43 and uninstall).  

Check your blacklist files in /etc/modprobe.d/blacklist.conf (open the file manager window, go to file system, then navigate to /etc/ directory etc.)  Take a look at the file (don't worry, as normal user you can't make any changes)  and make sure that wl driver is not blacklisted; take a look at the other files in the same directory, especially if there is a file called blacklist-local.conf.  

If you need to make edits to those you need to open the file from the terminal with 

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Ultimately you want the drivers bcma and brcmsmac blacklisted and wl not blacklisted.  After you've uninstalled the b43 driver, de-activated any STA drivers, made sure the blacklists/whitelists are OK please reboot then install the wl driver from Ubuntu Software Centre (type "bcm" in the search window and install the three drivers).  Disconnect from wired and reboot.  

Sorry about the hurried post, am in a rush.  Please check the thread that you linked to in your first post (all the steps I've described here are explained there in more detail).  Sorry about referring you to my own thread, I'm not that vain, just in a rush :)  

If someone else has better ideas / more experience please step in :) 

Thanks and cheers :)

---

### Post by Frank Einstein's Bride on 2012-01-21
blacklist-local.conf. Had wl blacklsited so I removed, that the sftware centre had one wl driver that was already install so I reset the computer and was recieveing full strength signal after thre restart. 

lspci -k 


Now reads 

Wireless LAN Controller (rev 01)  
 	Subsystem: Hewlett-Packard Company Device 1795  
Kernel driver in use: wl
 	Kernel modules: wl, bcma, brcmsmac  
 07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)  
 	Subsystem: Hewlett-Packard Company Device 3387  
 	Kernel driver in use: r8169  
 	Kernel modules: r8169 


Is that how it should be, does it matter that bcms and brcmsmac are listed under kernel modules?


Thanks for all the help, Finally I don't need to keep switching to windows.

---

### Post by ts3 on 2012-01-21
> **Frank Einstein's Bride said:**
> 
 	Subsystem: Hewlett-Packard Company Device 1795  
Kernel driver in use: wl
 	Kernel modules: wl, bcma, brcmsmac  
 
Is that how it should be, does it matter that bcms and brcmsmac are listed under kernel modules?


Thanks for all the help, Finally I don't need to keep switching to windows.

I am glad it worked :) Ubuntu is great, after I installed on my old laptop I stopped booting into Windows XP & then on a new laptop I ditched Windows completely & single-boot (well, multi-boot, but only other Ubuntu-flavoured stuff).

About the drivers: when I run lspci -k I also show wl, bcma, brcmsmac for some reason.  A while ago, just after I did a lot of blacklisting & rmmod-ing, it used to show only wl under kernel modules. I reckon the two other modules must have re-loaded at some point but as long as they are blacklisted and wl loads that doesn't bother me.  

Enjoy and cheers :)

---

