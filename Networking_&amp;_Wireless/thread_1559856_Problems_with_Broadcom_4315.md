---
title: "Problems with Broadcom 4315"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by manilva_garcia on 2010-08-24
Hi Guys,

I have installed Ubuntu 10.04 on my Dell Inspiron Mini which comes with a Broadcom 4315 wireless card. However, it appears that the card is not detected or the driver has not been installed correctly.

Below is the output when using the lshw -C Network command:

[COLOR=Red]WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:bc:22:15
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.4 latency=0 multicast=yes
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device multicast=yes[/COLOR]

[COLOR=Black]When using the System/Administration/Hardware Drivers software I see that Broadcom STA wireless driver is selected but then below it says "This driver is selected but not currently in use".

I have followed various threads but to no avail.

Thanks for the help!
[/COLOR]

---

### Post by JBAlaska on 2010-08-24
Put the Ubuntu LiveCD (USB?)in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM".
[COLOR="Navy"]Note: I've never tried this with a usb stick, you may have to modify the above somewhat.[/COLOR]

Then open a terminal and do:
```
sudo apt-get update

```
Then:
```
sudo apt-get install bcmwl-kernel-source

```
Now reboot and select the Broadcom STA driver. in System, Administration, Hardware Drivers

---

### Post by manilva_garcia on 2010-08-24
> **JBAlaska said:**
> Put the Ubuntu LiveCD (USB?)in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM".
[COLOR=Navy]Note: I've never tried this with a usb stick, you may have to modify the above somewhat.[/COLOR]

Then open a terminal and do:
```
sudo apt-get update

```Then:
```
sudo apt-get install bcmwl-kernel-source

```Now reboot and select the Broadcom STA driver. in System, Administration, Hardware Drivers

Hi,

I carried out your instructions above, when I tried:

sudo apt-get install bcmwl-kernel-source the output was:
[COLOR=Red]
christian@DELL:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for christian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]

Any further suggestions?

---

### Post by JBAlaska on 2010-08-24
Did you reboot after selecting the Broadcom STA driver in System, Administration, Hardware Drivers?

---

### Post by manilva_garcia on 2010-08-24
I did yes, with the ethernet all is fine but the wireless options do not appear when using the network utils GUI. Iwconfig says that no wireless extensions can be found for:
 
-lo
-eth0
-wwan0
 
Thanks

---

