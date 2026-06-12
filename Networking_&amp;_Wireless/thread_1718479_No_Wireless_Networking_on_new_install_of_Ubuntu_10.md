---
title: "No Wireless Networking on new install of Ubuntu 10.04"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by MarcW10 on 2011-03-31
Hi All

Like the title says I have no wireless networking. The wireless chipset onboard is a Broadcom BCM4311. I went through the steps at the top of the forum and got the drivers installed using ndiswrapper with no problems. However, there is still no wireless networking on my computer. The network device wlan0 doesn't even exist! I'm losing the will to live here! I'm hoping that there's something simple that I was supposed to do but didn't. Help please!!!

---

### Post by TBABill on 2011-03-31
Why did you go for ndiswrapper for your device? Easiest way to get it going is very simple. Plug into ethernet, do updates to the system, then click System>>Administration>>Hardware (10.04) or System>>Administration>>Additional Drivers. Select STA driver, click activate, restart, enjoy.

---

### Post by MarcW10 on 2011-03-31
Because I don't have an available ethernet connection. I'm using the old lappy to get online and download packages and suchlike.

---

### Post by MarcW10 on 2011-03-31
By the way, herein lies the lshw output in case it helps?


marc@marc-laptop:~$ sudo lshw -C network
[sudo] password for marc: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:11:29:c1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5787m-v3.23 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f6000000-f600ffff
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f8000000-f8003fff

---

### Post by cbowman57 on 2011-03-31
You need b43-fwcutter & associated files.  You'll have to figure out the process for downloading from your other laptop and transferring the debs over to your other machine.  I can't help you there.

Not sure if that will remove your ndiswrapper driver, if not you should probably remove that before you install the broadcom driver.

---

### Post by TBABill on 2011-03-31
> **cbowman57 said:**
> You need b43-fwcutter & associated files. You'll have to figure out the process for downloading from your other laptop and transferring the debs over to your other machine. I can't help you there.
 
Not sure if that will remove your ndiswrapper driver, if not you should probably remove that before you install the broadcom driver.
 
Many users do not know that you can do it right from the LiveCD and without needing ndiswrapper. I was unaware you have no access to ethernet.
 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
 
> 
**STA - No Internet access**
 
 
If you do not have any other means of Internet access on your computer, you will have to install the bcmwl-kernel-source package from the [restricted]("https://help.ubuntu.com/community/Repositories/Ubuntu") folder under **../pool/restricted/b/bcmwl** on the Ubuntu install media. 
**Note:** Systems installed from CDROM can simply add the install CD as a [package source]("https://help.ubuntu.com/community/Repositories/Ubuntu") and install bcmwl-kernel-source, automatically installing the required dependencies. 
**Note:** The following instructions are for a stock Ubuntu 10.04 LTS Edition via USB install. Netbook edition, other variations and matured systems may require more/less packages be installed to satisfy dependencies of bcmwl-kernel-source. 
**Note:** The GUI front end for dpkg will automatically display required packages that need to be installed to satisfy the bcmwl-kernel-source dependencies. To use the front end, navigate the file system using the file manager and double click on the packages to install/list required dependencies. 
**Step 1.** 
Navigate the install media and install the packages listed below by double clicking **or** navigate the install media and install these packages consecutively in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**): 
../pool/main/d/dkms :/dkms/$ sudo dpkg -i dkms*
../pool/main/p/patch :/patch/$ sudo dpkg -i patch*
../pool/main/f/fakeroot :/fakeroot/$ sudo dpkg -i fakeroot*
../pool/restricted/b/bcmwl :/bcmwl/$ sudo dpkg -i bcmwl-kernel-source*
**Step 2.** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use. 
**Note:** A computer restart may be required before using the wifi card. 
**LiveCD/LiveUSB**
 
 
**Note:** The install media contents are mounted under **/cdrom** of the filesystem. 
**Step 3.** 
For temporary use with the LiveCD and LiveUSB environments, instead of a computer restart, in a terminal issue the following commands: 
~$ sudo modprobe -r b43 ssb wl~$ sudo modprobe wl**Note:** Allow several seconds for the network manager to scan for available networks before attempting a connection. 

---

### Post by cbowman57 on 2011-03-31
Better yet, no downloading & transferring required.

---

### Post by AndrewD257 on 2011-03-31
I was just having problems with the BCM4312.  I ended up just getting an Ethernet cable and doing internet sharing with another laptop connected via wifi.  That said, you should be able to get all the files manually like so,
[https://help.ubuntu.com/community/Wi...ernet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access")

---

### Post by MarcW10 on 2011-03-31
Ok, I did it all as mentioned above, but of course it didn't get sorted. When I go to System > Administration > Hardware Drivers but it tells me that "No proprietary drivers are in use on this system". Even though they're good and installed. This whole thing seems to be conspiring to annoy me!

---

