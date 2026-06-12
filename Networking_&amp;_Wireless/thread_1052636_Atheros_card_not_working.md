---
title: "Atheros card not working"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Evil Ninja on 2009-01-27
So in this laptop I have an Atheros 802.11 wireless LAN card and it is not working. I have the hardware driver enabled, but still nothing. Any ideas?

---

### Post by kevdog on 2009-01-27
Need more info!!

Please post
lshw -C network
lspci -nnm

Thanks.

---

### Post by Evil Ninja on 2009-01-27
> **kevdog said:**
> Need more info!!

Please post
lshw -C network
lspci -nnm

Thanks.

I figured you would.

After the first command...

```
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:6d:a0:03
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:37:c9:0d:e5:9c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

And the second one...

```
00:00.0 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP67 Memory Controller [0547]" -ra2 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:01.0 "ISA bridge [0601]" "nVidia Corporation [10de]" "MCP67 ISA Bridge [0548]" -ra2 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:01.1 "SMBus [0c05]" "nVidia Corporation [10de]" "MCP67 SMBus [0542]" -ra2 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:01.2 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP67 Memory Controller [0541]" -ra2 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:01.3 "Co-processor [0b40]" "nVidia Corporation [10de]" "MCP67 Co-processor [0543]" -ra2 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:02.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 OHCI USB 1.1 Controller [055e]" -ra2 -p10 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:02.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 EHCI USB 2.0 Controller [055f]" -ra2 -p20 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:04.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 OHCI USB 1.1 Controller [055e]" -ra2 -p10 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:04.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP67 EHCI USB 2.0 Controller [055f]" -ra2 -p20 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:06.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP67 IDE Controller [0560]" -ra1 -p8a "Unknown vendor [f03c]" "Device [30ea]"
00:07.0 "Audio device [0403]" "nVidia Corporation [10de]" "MCP67 High Definition Audio [055c]" -ra1 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:08.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Bridge [0561]" -ra2 -p01 "" ""
00:09.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP67 AHCI Controller [0550]" -ra2 -p85 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:0a.0 "Ethernet controller [0200]" "nVidia Corporation [10de]" "MCP67 Ethernet [054c]" -ra2 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:0c.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Express Bridge [0563]" -ra2 "" ""
00:0d.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP67 PCI Express Bridge [0563]" -ra2 "" ""
00:12.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "GeForce 7000M (rev a2) [0533]" -ra2 "Hewlett-Packard Company [103c]" "Device [30ea]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
02:05.0 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r22 "Hewlett-Packard Company [103c]" "Device [30ea]"
02:05.1 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r12 "Hewlett-Packard Company [103c]" "Device [30ea]"
02:05.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r12 "Hewlett-Packard Company [103c]" "Device [30ea]"
02:05.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -r12 "Hewlett-Packard Company [103c]" "Device [30ea]"
03:00.0 "Ethernet controller [0200]" "Atheros Communications Inc. [168c]" "AR242x 802.11abg Wireless PCI Express Adapter [001c]" -r01 "Hewlett-Packard Company [103c]" "Device [137a]"

```

---

### Post by ibutho on 2009-01-28
You have an Atheros AR242x wireless card which is not currently supported out of the box. Try the suggestions in this [thread]("http://ubuntuforums.org/showthread.php?t=1026770") and see if that will get it working.

---

### Post by kevdog on 2009-01-28
Ohhh the dreaded 242x or 5007 chipset -- not really. 

You have no driver currently associated with the card.  I'm assuming you can connect right now using an ethernet connection.

I'd enable the linux-backport package.

So if you were running intrepid this would be the linux-backports-modules-intrepid package.

So here is the quick way to do everything:

gksu gedit /etc/apt/sources.list

Remove # sign in front of the lines that state:
#deb http//us.archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse
#deb-src http//us.archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse


Save the file.

Then run the following at the command line:
sudo aptitude update
sudo aptitude install linux-backports-modules-intrepid

This should then install the ath5k driver for you (which is the actual name of the driver you are going to use).

sudo modprobe ath5k

Check if the driver is loaded with
lshw -C network

Let me know what you find!

---

### Post by Evil Ninja on 2009-01-28
> **ibutho said:**
> You have an Atheros AR242x wireless card which is not currently supported out of the box. Try the suggestions in this [thread]("http://ubuntuforums.org/showthread.php?t=1026770") and see if that will get it working.

That worked! Thanks. :)

> **kevdog said:**
> Ohhh the dreaded 242x or 5007 chipset -- not really. 

You have no driver currently associated with the card.  I'm assuming you can connect right now using an ethernet connection.

I'd enable the linux-backport package.

That is how I'm using the net right now, and exactly what I did.

---

### Post by fugaki on 2009-01-28
I spent forever trying to get this card to work, and I finally gave up and bought a Linksys WEC600N express cardbus adapter, and it works fine.
I think it cost me $50 or so.

---

### Post by kevdog on 2009-01-28
If you would have spent just a little bit longer than forever you would have got this card up and running! ;)

---

### Post by ibutho on 2009-01-28
> **fugaki said:**
> I spent forever trying to get this card to work, and I finally gave up and bought a Linksys WEC600N express cardbus adapter, and it works fine.
I think it cost me $50 or so.

Its a pity that you had to fork out money for a different card because the AR242x works out of the box on most distros. The main exception is Ubuntu (and derivatives). I am not sure why the Ubuntu devs didn't include proper working support for it because it seems like its a popular card and many users are struggling to get it to work. I've run Fedora 10, openSUSE 11.1 and Mandriva 2009 and the AR242x just works without any tinkering.

---

### Post by kevdog on 2009-01-28
Wait until jaunty -- then I think it will be supported out of the box!

---

### Post by ibutho on 2009-01-28
> **kevdog said:**
> Wait until jaunty -- then I think it will be supported out of the box!
So far it does not work out of the box with any of the Alphas of Jaunty I've tried, but hopefully as the development process continues, things may change for the best.

---

### Post by Ketara on 2009-01-28
I've been trying to get this card to work for several days as well. Pretty annoyed that the madwifi fix (which was very simple to do in Hardy) does not work in Intrepid.

I'm trying this backports solution as kevdog suggested, and I'm getting some errors:

> ryan@Balthazar:~$ sudo aptitude update
Writing extended state information... Done
Hit [http://apt.wicd.net](http://apt.wicd.net) intrepid Release.gpg                                    
Ign [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras Translation-en_US                       
Hit [http://apt.wicd.net](http://apt.wicd.net) intrepid Release                                        
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US                
Ign [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras Packages                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US          
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US 
Hit [http://apt.wicd.net](http://apt.wicd.net) intrepid/extras Packages                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg [189B] 
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                      
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release [44.0kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [59.5kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [287kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [1785B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [18.0kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [571B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [26.0kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [5116B]    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1330B] 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [584B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [6044B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [88.4kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1709B] 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [45.4kB] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [11.3kB]  
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [3180B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [1145B] 
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages [67.8kB]   
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages [14B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages [26.9kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages [14B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources [12.6kB]    
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources [14B] 
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources [9645B] 
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources [14B] 
Fetched 813kB in 7s (105kB/s)                                                   
Reading package lists... Done             

Current status: 47 updates [+27], 46 new [+46].
ryan@Balthazar:~$ sudo aptitude install linux-backports-modules-intrepid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-11-generic{a} 
  linux-backports-modules-intrepid linux-image-2.6.27-11-generic{a} 
The following packages will be REMOVED:
  linux-backports-modules-2.6.27-9-generic{u} 
The following packages will be upgraded:
  linux-backports-modules-intrepid-generic 
1 packages upgraded, 3 newly installed, 1 to remove and 46 not upgraded.
Need to get 24.6MB of archives. After unpacking 94.5MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main linux-image-2.6.27-11-generic 2.6.27-11.25 [23.4MB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main linux-backports-modules-2.6.27-11-generic 2.6.27-11.12 [1191kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main linux-backports-modules-intrepid-generic 2.6.27.11.14 [2936B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main linux-backports-modules-intrepid 2.6.27.11.14 [2912B]
Fetched 24.6MB in 2min43s (151kB/s)                                             
Selecting previously deselected package linux-image-2.6.27-11-generic.
(Reading database ... 125892 files and directories currently installed.)
Unpacking linux-image-2.6.27-11-generic (from .../linux-image-2.6.27-11-generic_2.6.27-11.25_i386.deb) ...
Done.
Selecting previously deselected package linux-backports-modules-2.6.27-11-generic.
Unpacking linux-backports-modules-2.6.27-11-generic (from .../linux-backports-modules-2.6.27-11-generic_2.6.27-11.12_i386.deb) ...
Preparing to replace linux-backports-modules-intrepid-generic 2.6.27.9.13 (using .../linux-backports-modules-intrepid-generic_2.6.27.11.14_i386.deb) ...
Unpacking replacement linux-backports-modules-intrepid-generic ...
(Reading database ... 128748 files and directories currently installed.)
Removing linux-backports-modules-2.6.27-9-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
Selecting previously deselected package linux-backports-modules-intrepid.
(Reading database ... 128701 files and directories currently installed.)
Unpacking linux-backports-modules-intrepid (from .../linux-backports-modules-intrepid_2.6.27.11.14_i386.deb) ...
Setting up linux-image-2.6.27-11-generic (2.6.27-11.25) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic          
 *  nvidia (177.82)...                                                          nvidia (177.82): Installing module.
  Kernel source for 2.6.27-11-generic not installed.  Cannot install this module.
                                                                         [COLOR="Red"][fail][/COLOR]
 *  vboxdrv (2.1.2)...                                                          vboxdrv (2.1.2): Installing module.
  Kernel source for 2.6.27-11-generic not installed.  Cannot install this module.
                                                                         [COLOR="Red"][fail][/COLOR]
 *  vboxnetflt (2.1.2)...                                                       vboxnetflt (2.1.2): Installing module.
  Kernel source for 2.6.27-11-generic not installed.  Cannot install this module.
                                                                         [COLOR="Red"][fail][/COLOR]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-backports-modules-2.6.27-11-generic (2.6.27-11.12) ...
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic

Setting up linux-backports-modules-intrepid-generic (2.6.27.11.14) ...
Setting up linux-backports-modules-intrepid (2.6.27.11.14) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 46 updates [-1].
ryan@Balthazar:~$ sudo modprobe ath5k
[COLOR="Red"]FATAL[/COLOR]: Module ath5k not found.
ryan@Balthazar:~$ 


Little help please.

Edit: Did some color coding to make that output easier to read =P

---

### Post by Mrandoman on 2009-01-28
> **kevdog said:**
> Ohhh the dreaded 242x or 5007 chipset -- not really. 

You have no driver currently associated with the card.  I'm assuming you can connect right now using an ethernet connection.

I'd enable the linux-backport package.

So if you were running intrepid this would be the linux-backports-modules-intrepid package.

So here is the quick way to do everything:

gksu gedit /etc/apt/sources.list

Remove # sign in front of the lines that state:
#deb http//us.archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse
#deb-src http//us.archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse


Save the file.

Then run the following at the command line:
sudo aptitude update
sudo aptitude install linux-backports-modules-intrepid

This should then install the ath5k driver for you (which is the actual name of the driver you are going to use).

sudo modprobe ath5k

Check if the driver is loaded with
lshw -C network

Let me know what you find!

After following all these instructions I get this with lshw -C network:

> *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:6a:d2:a8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:b4:13:50:13:23
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I think my problem may be at 'sudo modprobe ath5k'. After putting that in, there is no output at all.

---

### Post by llama_attack on 2009-01-29
I think I have the same problem as Mrandoman, when I enter the line "sudo modprobe ath5k" I get no output, is it possible I've done something wrong in regards to the 'backports' step?

---

### Post by 5BallJuggler on 2009-01-29
I had to use the following:-

sudo aptitude install linux-backports-modules-$(uname -r)

for the backports step, everything else was OK

---

### Post by kevdog on 2009-02-04
5-ball-juggler 

Nice tip -- thanks!

---

### Post by dca on 2009-02-04
I've found the ath5k & 9k drivers are unreliable for the Atheros AR242x series mini-PCI card in laptops.  It stays connected for about an hour and drops connection basically requiring restart and that's on openSUSE 11.1 & Fedora 10.  The best results were (in all distros) using the last MadWifi build that included the HAL and all that and blacklisting ath5k/9k modules...  You can search on forums and find the older thread explaining how to do this.  The only other problem I've found on 8.10 is connecting to hidden network, doesn't work w/ any driver.

---

### Post by jf1991999 on 2009-02-08
I have followed the instructions in this thread.  Installed the backports fine.  As with other users sudo modprobe ath5k has no output.

I tried jugglers tip but that also doesn't help.  lshw -C network shows the Atheros AR242x in network UNCLAIMED as previous users have pasted in this thread.  

Any other tips would be greatly appreciated.

---

### Post by 5BallJuggler on 2009-02-08
post a copy of the file:

/boot/grub/menu.lst

my thinking is that the latest kernel is causing an issue, if your default is set to 0 and you have the xx-xx-xx-11 kernel it wont work, if you still have xx-xx-xx-7 installed and it is 3rd in your list then change your default to 2

---

