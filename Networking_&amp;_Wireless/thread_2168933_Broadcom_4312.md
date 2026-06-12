---
title: "Broadcom 4312"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by bikeman4444 on 2013-08-20
I have installed Ubuntu on an HP mini 110 and cannot connect the WIFI.  I did connect Ubuntu 13.04 without the third party software since I did not have an internet connection.  After the install I could not get onto the internet.  But, had the trial version running and I said that I wanted to install the third party software I was able to connect to the WIFI at this point I did not install I canceled since I did not want to download the third party software.

This tells me that the Broadcom 4312 is on the installation or actually installed.  How do I access it so I can get WIFI?  Do I need to install Ubuntu third party just so I can get the Broadcom 4312?  Even though it did install when I had the trial running?

Thanks,

Tom

---

### Post by Bucky Ball on 2013-08-20
*Thread moved to **Networking & Wireless**.*

Welcome to the forums. No and no. Please provide the output of these two commands, paste in one after the other hitting return between (from terminal: Applications>Accessories>Terminal and cut and paste the command in):

```
sudo lshw -C network
iwconfig
```

From memory, that card should work out of the box. Broadcom are generally very well supported and it is Win-think to expect you need to install a driver for it (occasionally this is the case, newer hardware can sometimes take some fiddling). Possibly a setting you have wrong. Check in Additional Drivers. Anything there? You are looking for B43 or STA.

You could try checking in Software Centre that you have these two installed:

```
b43-fwcutter
firmware-b43-installer
```

But let's have a look at that output first.

PS: When you left click the network icon do you see any available networks?

---

### Post by bikeman4444 on 2013-08-20
Here is the output from the commands that you had suggested I run:

> 
sudo lshw -C network:
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 18:a9:05:d0:56:23
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:febc0000-febfffff ioport:ec80(size=128)


iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.


b43-fwcutter:
The program 'b43-fwcutter' is currently not installed. You can install it by typing:
sudo apt-get install b43-fwcutter

HP-Mini-110:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter

     No internet connection...

HP-Mini-110:~$ firmware-b43-fwcutter
firmware-b43-fwcutter: command not found


I know there is support since it did work when I attempted the third party install; it did connect.
How can I see packages that aren't installed but, are in my local system?

Thanks for your help.

---

### Post by bikeman4444 on 2013-08-20
No there aren't available networks when I left click on the network icon.  There should be.

---

### Post by Bucky Ball on 2013-08-20
Can you plug in a cable and run install b43-fwcutter and firmware-b43-installer, please? If you can't get a cable to the machine and get online, you could try this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

The catch 22 in all this is that you need to be online to get wireless working with some cards. If you could plug in a cable, do an update I think your problems would be over poste haste. Would make life a LOT easier if you could get online with a cable. ;)

---

### Post by bikeman4444 on 2013-08-21
No I cannot plug in with a cable. I was able to run the link below "b43 - No Internet access"

[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access"]https://help.ubuntu.com/community/Wi...nternet_access
[/URL]
And thank you very much it works!  I was able to cd onto my Ubuntu USB run the 4b43-fwcutter
then downloaded the files on another computer then copy them onto my HP 110 and run the b43-fwcutter commands.

Works fine now!  Why did it work during installation and not after install?

Tom

---

### Post by carl4926 on 2013-08-21
> [COLOR=#000000] Why did it work during installation and not after install?[/COLOR]No idea/. Because mine doesn't work from the live session, I have to copy over my b43 folder to /lib/firmware (I keep a copy on a pen drive) if I want wireless in the live session. And repeat this post install.

Then do

```
sudo modprobe -rv b43
```
```
sudo modprobe -v b43
```

---

### Post by praseodym on 2013-08-21
For this low-power chipset (LP-PHY) you need this firmware version:

```
sudo apt-get install firmware-b43-lpphy-installer 
```
Check:
```

lspci -nnk | grep -iA2 net
```
It should read the ID 14e4:4315

---

### Post by Bucky Ball on 2013-08-21
> **bikeman4444 said:**
> Works fine now!  Why did it work during installation and not after install?

Tom

Hmm. Sometimes that happens. Because you were running from the CD, perhaps? 

Anyway, great to hear all working. Please mark thread as solved by following the link in my signature. Good luck. ;)

---

