---
title: "Broadcom Linux Drivers"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by Majortopio on 2010-11-02
Hey there everyone! I'm new to Ubuntu/Linux/the whole shebang (just installed it earlier today) and apparently my wireless card doesn't like Linux, unfortunately. I've been playing around with it all day, and got it to work once with the Hardware Drivers application, but that stopped working after one restart. So I checked out Broadcom's website and hey, looks like they just recently released Linux drivers, I thought I had gotten lucky and promptly downloaded them. Now, I tried following the included readme file, with asks me to write the following in Terminal:

```
1. Create a directory and extract the files:

   tar xvzf tg3-<version>.tar.gz
```

Which I did. I extracted the downloaded file 'linux-3.110g.zip' into a directory, double checked that the tar.gz file was there, and then ran that terminal command, but all Terminal comes up with is:

```
tar: tg3-3.110.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

```

I've tried copying the .tar.gz to desktop and everything, but it just refuses to find it. Any help would be much, much appreciated!!

---

### Post by TBABill on 2010-11-02
Before using what you downloaded, please post what Broadcom card your computer has. The drivers available in the repo actually work well for many of the Broadcom cards IF you install them properly. However, without knowing what you have, what you have tried already and what you are seeing, little assistance can be offered.

In a terminal, please run ```
sudo lshw -C network
``` and post the output here. Also run ```
lspci
``` and post the output as well. 

Did you already try to go to System (top panel)>>>>Administration>>>>Hardware while connected to a hardwired connection and allow the system to install the driver?

Which distro version of Ubuntu are you using? Is it a Wubi install or a full install on its own partition?

---

### Post by Majortopio on 2010-11-02
Here are the outputs:

```
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:ad:c5:9e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0b00000-f0b03fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:14:f5:6e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 ip=192.168.1.43 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:38 memory:f1000000-f100ffff
majortopio@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 VGA compatible controller: ATI Technologies Inc Device 9488
02:00.1 Audio device: ATI Technologies Inc RV710/730
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
0b:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
0b:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
0b:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
0b:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
0d:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

And yes, I have installed the 'Broadcom STA wireless driver', but that has not worked for me.

I installed via Wubi and it is the newest version (10.10 I believe).

---

### Post by TBABill on 2010-11-02
Ok, the Wubi install may be the problem. Under a normal install (Ubuntu on its own partition), the driver works perfectly for the BCM4312. That's the same one I have in 3 separate laptops and they all work wonderfully with the driver.

I can't provide Wubi help because I do not use Ubuntu inside Windows. Hopefully someone will come along that can help. Perhaps searching Wubi and BCM4312 will help (on the forum).

---

### Post by Majortopio on 2010-11-02
Typical! Perhaps I'll have to create a seperate partition for it, I might just do that to spare me the trouble, if no one else can help. But thanks anyways!

---

### Post by chili555 on 2010-11-02
The driver tg3 is for your wired ethernet card. You have it already.

Network Manager switches to wired if you have a cable attached; you do:> driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 [COLOR="Red"]ip=192.168.1.43[/COLOR] latency=0 [COLOR="Red"]link=yes[/COLOR]Is the behavior improved if you detach the ethernet cable? It may take a few moments for NM to notice the change in state.

---

### Post by Majortopio on 2010-11-02
Nothing changes if I detach the ethernet cable, unfortunately. But I can't even enable wireless in the network dropdown on the top panel, so I'm not sure what to do now.

---

### Post by chili555 on 2010-11-02
>  *-network DISABLED      
       description: Wireless interface
One wonders why it's disabled. Please post:```
rfkill list all
```What kind of computer is it? A Dell maybe??

---

### Post by Majortopio on 2010-11-03
```
majortopio@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Yes indeed!

---

### Post by chili555 on 2010-11-03
Sometimes I can just put my hands on my screen and feel the Dell vibe; even all the way across the ocean!

Please try:```
sudo rmmod -f dell-laptop
```Now does the wireless switch work as expected? Does the wireless work after you disconnect the ethernet cable? If so, let's blacklist it permanently:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Please post back so the searchers will learn from your experience.

---

### Post by Majortopio on 2010-11-03
Sorry for being a pain in the butt, but I decided to just get it done and installed Ubuntu 10.10 on a seperate partition. So now I have a clean install, but when I try to activate the Broadcom STA driver from the Additional Drivers dialogue, it just says that it could not install the driver.

I tried the command you posted, but it obviously didn't do anything. Now, however, rfkill list all outputs this:

```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```And 
sudo lshw -C network
outputs:

```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0b00000-f0b03fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:14:f5:6e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb v2.19 ip=192.168.1.43 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:56 memory:f1000000-f100ffff

```What to do, what to do?!

EDIT: NVM! I got it to work, realised I had to install the B43 driver first. Now it works perfectly (so far)!

---

### Post by chili555 on 2010-11-03
> I got it to work, realised I had to install the B43 driver first. Now it works perfectly (so far)!Great work! Post back if we can help you further.

Glad it's working.

---

