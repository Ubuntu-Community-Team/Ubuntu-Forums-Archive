---
title: "Dell Lattitude D600 wireless"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by woopud on 2011-05-25
I just installed Ubuntu 11.04 on my Dell Lattitude D600 with no problems except that I can't get my BCM4306 to work, I tried installing the firmware-b43-installer but keep getting the following error in synaptic:  "E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 4"

What am I doing wrong?
Bert

---

### Post by woopud on 2011-05-26
I searched all the posts about the broadcom drivers but no matter what I do, I get the same message.  I tried synaptic, software center and the terminal.

Bert

---

### Post by chili555 on 2011-05-26
In order for b43-fwcutter to go out on the internet and obtain firmware to extract and install, you need an internet connection. Have you connected an ethernet cable and obtained a connection?

---

### Post by woopud on 2011-05-26
Hi, I'm using a network cable to connect to the internet.  Internet works with cable I just can't figure out the wireless.

Bert

---

### Post by nm_geo on 2011-05-26
> **woopud said:**
> Hi, I'm using a network cable to connect to the internet.  Internet works with cable I just can't figure out the wireless.

Bert

Go to the terminal and 

```
lspci -nn | grep 14e4
```Paste results 

Don't know but you may need the legacy firmware.

**Info below added for clarification.. 07/25/2011**

CM4306 802.11b/g Wireless LAN Controller [**[COLOR=Red]14e4:4320] (rev[COLOR=Black] 03[/COLOR][/COLOR]**[COLOR=Black])  [/COLOR]use b43-fwcutter & firmware-b43-installer

CM4306 802.11b/g Wireless LAN Controller [**[COLOR=Red]14e4:4320] (rev [COLOR=Black]02[/COLOR])[/COLOR]** use b43-fwcutter & firmware-b43legacy-installer

---

### Post by chili555 on 2011-05-26
With the ethernet cable attached and an internet connection, please open a terminal and do:```
sudo apt-get install firmware-b43-installer
```Do you get the same error? Any other clues as to what's going wrong?

---

### Post by woopud on 2011-05-26
> **nm_geo said:**
> Go to the terminal and 

```
lspci -vnn | grep 14e4
```

Paste results 

Don't know but you may need the legacy firmware.

```
[CODE]woopud@woopud-Laptop:~$ lspci vnn | grep 14e4
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
woopud@woopud-Laptop:~$ 

```[/CODE]

---

### Post by woopud on 2011-05-26
> **chili555 said:**
> With the ethernet cable attached and an internet connection, please open a terminal and do:```
sudo apt-get install firmware-b43-installer
```Do you get the same error? Any other clues as to what's going wrong?

```

```woopud@woopud-Laptop:~$ sudo apt-get install firmware-b43-installer
[sudo] password for woopud: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/18.2 kB of archives.
After this operation, 131 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package b43-fwcutter.
(Reading database ... 131921 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Selecting previously deselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
--2011-05-26 12:13:02--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Resolving mirror2.openwrt.org... 0.0.32.144
Connecting to mirror2.openwrt.org|0.0.32.144|:80... failed: Invalid argument.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
woopud@woopud-Laptop:~$

---

### Post by woopud on 2011-05-26
My mistake, that should be:

```

```woopud@woopud-Laptop:~$ lspci -vnn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
woopud@woopud-Laptop:~$

---

### Post by josephmills on 2011-05-26
> **nm_geo said:**
> Go to the terminal and 

```
lspci -vnn | grep 14e4
```

Paste results 

Don't know but you may need the **legacy firmware.**

you do need the firmware-b43legacy-installer

---

### Post by woopud on 2011-05-26
```
woopud@woopud-Laptop:~$ sudo apt-get install firmware-b43legacy-installer
[sudo] password for woopud: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firmware-b43legacy-installer
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 3,478 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/multiverse firmware-b43legacy-installer all 4.178.10.4-5 [3,478 B]
Fetched 3,478 B in 0s (7,689 B/s)                 
Selecting previously deselected package firmware-b43legacy-installer.
(Reading database ... 131932 files and directories currently installed.)
Unpacking firmware-b43legacy-installer (from .../firmware-b43legacy-installer_4.178.10.4-5_all.deb) ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
--2011-05-26 18:52:40--  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Resolving mirror2.openwrt.org... 46.4.11.11
Connecting to mirror2.openwrt.org|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3888794 (3.7M) [application/x-bzip2]
Saving to: `broadcom-wl-4.150.10.5.tar.bz2'

100%[=============>] 3,888,794    371K/s   in 13s     

2011-05-26 18:52:53 (297 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794]

This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:165
14e4:4320)!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
woopud@woopud-Laptop:~$ 

```

---

### Post by josephmills on 2011-05-26
> **woopud said:**
> 
Setting up firmware-b43legacy-installer (4.178.10.4-5) ...
Not supported card here (PCI id 14e4:165
**14e4:4320)**!
Use b43 firmware. This is just for the b43legacy driver.
Aborting.
dpkg: error processing firmware-b43legacy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
woopud@woopud-Laptop:~$ 


then from post number #9 > My mistake, that should be:

woopud@woopud-Laptop:~$ lspci -vnn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller **[14e4:4320]** (rev 03)
woopud@woopud-Laptop:~$




I dont know whats going on here sorry

---

### Post by chili555 on 2011-05-27
Please reboot your computer and run and post:```
dmesg | grep b43
```Thanks.

I have no idea what's going on with the firmware installer. I installed it last evening and it went perfectly for me.

---

### Post by josephmills on 2011-05-27
if that wont work try to uninstall the bcmwl-kernel-source then install the firmware then the bcmwl-kernel-source again to what repos do yo have open as the firmware is a 3rd party source. Pleasee open up ubuntu software center go to edit-->sofware sources then make sure all are ticked see pics then close software sources and ubuntu software center and do a ```
sudo apt-get update && sudo apt-get upgrade

``` then try again (firmware)let us know how it is going :p

---

### Post by woopud on 2011-05-28
> **chili555 said:**
> Please reboot your computer and run and post:```
dmesg | grep b43
```Thanks.

I have no idea what's going on with the firmware installer. I installed it last evening and it went perfectly for me.

```
woopud@woopud-Laptop:~$ dmesg | grep b43
woopud@woopud-Laptop:~$ 

```

---

### Post by woopud on 2011-05-28
> **josephmills said:**
> if that wont work try to uninstall the bcmwl-kernel-source then install the firmware then the bcmwl-kernel-source again to what repos do yo have open as the firmware is a 3rd party source. Pleasee open up ubuntu software center go to edit-->sofware sources then make sure all are ticked see pics then close software sources and ubuntu software center and do a ```
sudo apt-get update && sudo apt-get upgrade

``` then try again (firmware)let us know how it is going :p

```
woopud@woopud-Laptop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for woopud: 
Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.canonical.com natty InRelease                    
Ign http://archive.ubuntu.com natty InRelease                        
Ign http://us.archive.ubuntu.com natty InRelease                     
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Ign http://us.archive.ubuntu.com natty-security InRelease                      
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.canonical.com natty Release.gpg                   
Hit http://archive.ubuntu.com natty Release.gpg                      
Hit http://us.archive.ubuntu.com natty Release.gpg                   
Hit http://us.archive.ubuntu.com natty-updates Release.gpg           
Hit http://extras.ubuntu.com natty Release                           
Hit http://archive.ubuntu.com natty Release                          
Hit http://archive.canonical.com natty Release                       
Hit http://us.archive.ubuntu.com natty-security Release.gpg                    
Hit http://us.archive.ubuntu.com natty Release                       
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.canonical.com natty/partner i386 Packages         
Hit http://us.archive.ubuntu.com natty-updates Release               
Hit http://us.archive.ubuntu.com natty-security Release              
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://archive.ubuntu.com natty/restricted Sources                         
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://us.archive.ubuntu.com natty/restricted Sources            
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources            
Hit http://us.archive.ubuntu.com natty/universe Sources              
Hit http://us.archive.ubuntu.com natty/main i386 Packages            
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages      
Hit http://us.archive.ubuntu.com natty/universe i386 Packages        
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com natty/main TranslationIndex         
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources    
Hit http://us.archive.ubuntu.com natty-updates/main Sources          
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources    
Hit http://us.archive.ubuntu.com natty-updates/universe Sources      
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages    
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-security/restricted Sources   
Hit http://us.archive.ubuntu.com natty-security/main Sources         
Hit http://us.archive.ubuntu.com natty-security/multiverse Sources   
Hit http://us.archive.ubuntu.com natty-security/universe Sources     
Hit http://us.archive.ubuntu.com natty-security/main i386 Packages   
Hit http://us.archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-security/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/universe TranslationIndex
Ign http://extras.ubuntu.com natty/main Translation-en_US
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com natty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/main Translation-en
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
woopud@woopud-Laptop:~$ 

```

---

### Post by woopud on 2011-05-28
```
woopud@woopud-Laptop:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/18.2 kB of archives.
After this operation, 131 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package b43-fwcutter.
(Reading database ... 132414 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Selecting previously deselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
--2011-05-28 03:14:19--  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Resolving mirror2.openwrt.org... 46.4.11.11
Connecting to mirror2.openwrt.org|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3888794 (3.7M) [application/x-bzip2]
Saving to: `broadcom-wl-4.150.10.5.tar.bz2'

100%[======================================>] 3,888,794    827K/s   in 5.7s    

2011-05-28 03:14:25 (661 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794]

This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
woopud@woopud-Laptop:~$ 

```

Seems like it installed without problems now.

---

### Post by woopud on 2011-05-28
```
woopud@woopud-Laptop:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for woopud: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,202 kB of archives.
After this operation, 3,367 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/restricted bcmwl-kernel-source i386 5.100.82.38+bdcom-0ubuntu3 [1,202 kB]
Fetched 1,202 kB in 3s (329 kB/s)                
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 132425 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-8-generic
Building for architecture i686
Building initial module for 2.6.38-8-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic/updates/dkms/

depmod.......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
woopud@woopud-Laptop:~$ 

```

---

### Post by woopud on 2011-05-28
So, both files installed without errors now but now what?  How do I enable my wireless?

Bert

---

### Post by woopud on 2011-05-28
```
woopud@woopud-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

woopud@woopud-Laptop:~$ sudo lshw -C network
[sudo] password for woopud: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:cb:8d:26
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5705-v3.16 ip=192.168.1.8 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32
       resources: memory:fafee000-fafeffff
woopud@woopud-Laptop:~$ 

```

---

### Post by chili555 on 2011-05-28
Joseph is away fixing an iced tea. He wishes he could see the line corresponding to the Broadcom from:```
lspci -nn
```

---

### Post by woopud on 2011-05-28
```
woopud@woopud-Laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
woopud@woopud-Laptop:~$ 
```

---

### Post by chili555 on 2011-05-28
Now Joseph wants to see:```
rfkill list all
sudo modprobe b43
dmesg | grep b43
```Something's haywire and dmesg will tell us.

---

### Post by woopud on 2011-05-28
Now Bert will show:

```
woopud@woopud-Laptop:~$ rfkill list all
woopud@woopud-Laptop:~$ sudo modprobe b43
[sudo] password for woopud: 
woopud@woopud-Laptop:~$ dmesg | grep b43
[ 1821.526466] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[ 1821.594204] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[ 1821.684167] Registered led device: b43-phy0::tx
[ 1821.684250] Registered led device: b43-phy0::rx
[ 1821.684314] Registered led device: b43-phy0::radio
[ 1822.128084] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
woopud@woopud-Laptop:~$ 

```

---

### Post by chili555 on 2011-05-28
It looks marvelous! Now do you have a wireless interface?```
iwconfig
sudo iwlist wlan0 scan
```Perhaps the only difficulty is that b43 and ssb are not loading automagically, eh, Joseph?

---

### Post by josephmills on 2011-05-28
This is what joseph wants you to do!!!!!!!!!!!!!!
Hi there click on this link it will download you firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move to your ubuntu box then move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``````

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```
then 
```
sudo reboot 
``` tell us how it works out

but I still think that there is something funny going on here that has to do with the 4320 part

---

### Post by woopud on 2011-05-28
> **chili555 said:**
> It looks marvelous! Now do you have a wireless interface?```
iwconfig
sudo iwlist wlan0 scan
```Perhaps the only difficulty is that b43 and ssb are not loading automagically, eh, Joseph?

```
woopud@woopud-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"DUTCH"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
woopud@woopud-Laptop:~$ sudo iwlist wlan0 scan
[sudo] password for woopud: 
wlan0     Scan completed :
          Cell 01 - Address: 00:15:05:C5:85:44
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"myqwest4705"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000161aeeb8249
                    Extra: Last beacon: 1036ms ago
                    IE: Unknown: 000B6D79717765737434373035
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:24:B2:86:12:3E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Loveshack"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c2a715d200
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 00094C6F7665736861636B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8A0050F204104A00011010440001021041000100103B00010310470010F04894FF6F5AA00A3CD81142F33D7E321021000D4E4554474541522C20496E632E1023000857475236313476381024000857475236313476381042000538333235381054000800060050F20400011011001657475236313476382028576972656C65737320415029100800020084
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:20:ED:08:FB:0F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"DUTCH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017ee4ff037
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 00054455544348
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0103
                    IE: Unknown: 32041224606C
          Cell 04 - Address: 00:24:7B:A0:B9:AE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"brian623"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000806ee0324a
                    Extra: Last beacon: 968ms ago
                    IE: Unknown: 0008627269616E363233
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A0001101044000102103B0001031047001010B3B375EBDBDDDDBCC15836105FA2B3102100025449102300064150444B3731102400043731303010420007313233343332311054000800060050F20400011011001A416374696F6E7465632052656769737472617220504B3530303010080002008C
          Cell 05 - Address: 00:24:7B:FE:04:C8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"myqwest1885"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002970bb776dd
                    Extra: Last beacon: 4032ms ago
                    IE: Unknown: 000B6D79717765737431383835
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
          Cell 06 - Address: 00:24:01:F6:2E:24
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Bear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cbb952180
                    Extra: Last beacon: 708ms ago
                    IE: Unknown: 000442656172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051900000000000000000000000000000000000000
                    IE: Unknown: 3D1606051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
                    IE: Unknown: DD050050F20500
          Cell 07 - Address: 00:1F:33:2D:D5:EC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001591e64183
                    Extra: Last beacon: 456ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7C0050F204104A00011010440001011041000100103B00010310470010BABC558152448F21377D001C46B389491021000D4E4554474541522C20496E632E10230009574E5238333442763210240009574E523833344276321042000230311054000800060050F204000110110009574E52383334427632100800020084
                    IE: Unknown: DD090010180201F0010000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 08 - Address: 00:22:10:B4:53:30
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"qwest1296"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002970c744236
                    Extra: Last beacon: 1124ms ago
                    IE: Unknown: 0009717765737431323936
                    IE: Unknown: 010582848B960C
                    IE: Unknown: 030101
                    IE: Unknown: 050C010200000000000000000000
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:22:6B:49:A0:DC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Patricia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017cb364b17e
                    Extra: Last beacon: 448ms ago

woopud@woopud-Laptop:~$ 

```

---

### Post by woopud on 2011-05-28
I can see the wireless networks now!  It won
t let me choose any of them (including my own "DuTCH").

Bert

---

### Post by woopud on 2011-05-28
And now all the wireless is gone again.....

---

### Post by chili555 on 2011-05-28
> **woopud said:**
> And now all the wireless is gone again.....What did you do between the two posts?

---

### Post by woopud on 2011-05-28
I rebooted the laptop...my mistake

---

### Post by chili555 on 2011-05-28
Well, let's get b43 to load from the git-go. (That's South Carolina-speak for "on boot.")```
sudo su
echo b43 >> /etc/modules
exit
```Now reboot and tell us if your wireless is working as expected.

---

### Post by woopud on 2011-05-28
Okay, that did the trick, wireless is back up!
Sorry for the long pauses, been running around all day and every time I got home I checked this forum and tried the laptop again after you suggestions.  Seems like it won't connect though...

Bert

---

### Post by woopud on 2011-05-28
So, the adapter will load now and I can see several wireless networks including my own, if I select it it will think for a bit and then asks for the WEP key, after typing the key it will think again for a while and the window asking for the key pops up again and it will just keep doing this over and over.

Bert

---

### Post by woopud on 2011-05-28
Brainfart...LOL
I kept switching two digits in my  WEP key....duh
It's working!
Thanks for all the help, especially Joseph!

---

### Post by lazer_knezer on 2011-05-30
Hey guys...

I just wanted to say THANK YOU!!! :D I just spent the better part of a day (or two) trying to get the same wireless card working on my Dell Inspiron 1150. I had been jumping through hoops trying to get 'ndiswrapper' to work to no avail, when I came across this thread.

I was able to follow all the tips (I didn't have any of the errors that Bert had) and was able to get my wireless up and running! If only I could have found this right away this morning (well yesterday morning now). Thanks again!

Jake

---

### Post by ghee22 on 2011-06-03
Would someone please summarize the solution?

---

### Post by chili555 on 2011-06-03
> **ghee22 said:**
> Would someone please summarize the solution?Do what it says in post #26 and reboot. Enjoy.

---

### Post by lear64 on 2011-06-06
> **chili555 said:**
> With the ethernet cable attached and an internet connection, please open a terminal and do:```
sudo apt-get install firmware-b43-installer
```Do you get the same error? Any other clues as to what's going wrong?


I just loaded a D600 w/ 11.04 and found myself to this forum for this very purpose. 
I ran the line above and everything just worked.

---

### Post by swopiv on 2011-07-25
Thank you guys!!  After several hours of fruitless headbanging I found this.  Worked first time.  No fuss, no hassle.  Brill!  I'd been wrestling with b43 legacy and fwcutter but it kept throwing up errors.  I now have a *useful* Dell D600.  :)

---

### Post by wiley.coyote on 2011-10-03
> **chili555 said:**
> Do what it says in post #26 and reboot. Enjoy.
Yes yes yes.  Do what is says to in post #26, reboot and enjoy.  Thank you so much Joseph.  I also now have a working & useful Latitude D600.  After 2 days of wrestling with this wireless adapter, I finally have a garage laptop.

---

### Post by homeuser1 on 2012-01-09
I have fought this issue for days and finally a solution that is easy to follow and WORKS!  Thanks all!

---

### Post by CanuckinOttawa on 2012-06-06
> **josephmills said:**
> This is what joseph wants you to do!!!!!!!!!!!!!!
Hi there click on this link it will download you firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move to your ubuntu box then move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``````

cd /lib/firmware

```then 
```

sudo -s 

```then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```then 
```
sudo reboot 
``` tell us how it works out

but I still think that there is something funny going on here that has to do with the 4320 part

That whole process was f'n A++++ It worked like a charm! I have tried everything, spent countless hours trying to get the damn wireless to work and this has been the ultimate solution for my DELL Latitude D600! There are countless posts on this subject I have read and this one is the cat's meooooooooooow LOL!

---

