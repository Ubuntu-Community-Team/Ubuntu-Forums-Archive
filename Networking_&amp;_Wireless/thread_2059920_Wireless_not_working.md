---
title: "Wireless not working"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by jiaweihuo on 2012-09-19
I have installed the windows driver by ndiswrapper in Ubuntu 12.04. But the wireless is still not working. How to solved it? Thanks.

---

### Post by Bucky Ball on 2012-09-19
*Thread moved to **Networking & Wireless***


ndiswrapper definitely last resort, not generally recommended and problematic. It can also prevent other drivers loading automatically and needs to be manually uninstalled if not required. Please post the outputs of these two commands:

```
sudo lshw -C network
iwconfig
```Have you plugged in an ethernet cable, gotten online and updated, then checked 'Additional Drivers' or seen if any drivers are offered or installed by the update? That is the 'rule of thumb' first step if wireless is not already working out-of-the-box.

---

### Post by jiaweihuo on 2012-09-19
Thanks. This is what I get after running the command:

```

jiaweihuo@jiaweihuo-laptop:~$ sudo lshw -C network
[sudo] password for jiaweihuo: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: 2c:d4:44:b6:ee:dc
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=147.8.166.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1d10000-f1d1ffff
jiaweihuo@jiaweihuo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jiaweihuo@jiaweihuo-laptop:~$

```

And I have checked 'Additional Drivers' and see nothing.

---

### Post by Bucky Ball on 2012-09-19
Okay. That's promising; ralink generally well supported. It is unclaimed. Have you plugged in a cable and gotten your updates, checked 'Additional Drivers'? Is this very new card and you know it doesn't work with the existing native Linux drivers?

```
*-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1d10000-f1d1ffff
```That's the bit we're interested in. As you can see, unclaimed and no drivers loaded. 

PS: You can put code in [code] tags by clicking 'Go Advanced', marking the code and clicking the # icon. ;)

---

### Post by jiaweihuo on 2012-09-19
Thanks. I have checked 'Additional Drivers' and see 'no proprietary drivers are in use'. I don't know whether the card works with the existing native Linux drivers or not.

---

### Post by Bucky Ball on 2012-09-19
> **Bucky Ball said:**
> Have you plugged in a cable and gotten your updates, ***then*** check 'Additional Drivers'? 

?? You see no proprietary drivers in use but are there any there to use? What is the exact model of your machine? That might give us the wireless card model. Do you know for certain you need ndiswrapper for this card or was it just a punt/old thread?

---

### Post by jiaweihuo on 2012-09-19
Yes, I have. And see 'no proprietary drivers are in use'.

---

### Post by Bucky Ball on 2012-09-19
Please reread last post, have edited.

---

### Post by jiaweihuo on 2012-09-19
The machine is Fujitsu LH 772 U2W. I just follow old post to use ndiswrapper. 


Here is more information:

```
jiaweihuo@jiaweihuo-laptop:~$ hwinfo --short
cpu:                                                            
                       Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz, 1200 MHz
                       Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz, 1200 MHz
                       Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz, 1200 MHz
                       Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz, 1200 MHz
                       Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz, 1200 MHz
                       Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz, 1200 MHz
                       Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz, 1200 MHz
                       Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz, 1200 MHz
keyboard:
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Pixart Imaging USB Optical Mouse
  /dev/input/mice      PS/2 Generic Mouse
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel VGA compatible controller
                       nVidia VGA compatible controller
sound:
                       Intel Audio device
storage:
                       Intel SATA controller
network:
  eth0                 Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller
                       RaLink Network controller
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
disk:
  /dev/sda             ST9750420AS
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             MATSHITA DVD-RAM UJ8A2AS
usb controller:
                       Intel USB Controller
                       Intel USB Controller
                       Intel USB Controller
bios:
                       BIOS
bridge:
                       Intel Host bridge
                       Intel PCI bridge
                       Intel PCI bridge
                       Intel PCI bridge
                       Intel PCI bridge
                       Intel PCI bridge
                       Intel ISA bridge
hub:
                       Linux 3.2.0-30-generic ehci_hcd EHCI Host Controller
                       Linux 3.2.0-30-generic ehci_hcd EHCI Host Controller
                       Linux 3.2.0-30-generic xhci_hcd xHCI Host Controller
                       Linux 3.2.0-30-generic xhci_hcd xHCI Host Controller
                       Hub
                       Hub
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel Communication controller
                       Intel SMBus
                       RaLink Bluetooth
                       Realtek Unclassified device
  /dev/input/event10   Chicony Electronics FJ Camera
                       AuthenTec Fingerprint Sensor
```

---

### Post by Bucky Ball on 2012-09-19
Unfortunately no:

```
network interface:   lo                   Loopback network interface   eth0                 Ethernet network interface
```

Not finding any information on that model, either.

---

### Post by Bucky Ball on 2012-09-19
> **jiaweihuo said:**
> ```

network:
  eth0                 Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller
                       RaLink Network controller
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface

```

Unfortunately this tells us nothing about your wireless card model. I can't find any information about that model of laptop either.

---

### Post by jiaweihuo on 2012-09-19
Thanks all the same. Seems unlucky for me.

---

### Post by Bucky Ball on 2012-09-19
Before you give up though, go here and identify your computer:

[http://support.fujitsupc.com/CS/Portal/support.do?srch=GUIDES](http://support.fujitsupc.com/CS/Portal/support.do?srch=GUIDES)

What you've given (Fujitsu LH 772 U2W) may not be the model as not getting much info in a regular search on their site. See if you get anywhere with that link, download the manual and identify the card. Then there's hope!

---

### Post by jiaweihuo on 2012-09-19
The attachment is what I use when installing the windows driver by ndiswrapper.

---

### Post by Bucky Ball on 2012-09-19
Gives no details at all. Find your computer on the Fujitsu link I gave if you can.

---

### Post by jiaweihuo on 2012-09-19
Maybe I have to use a USB adaptor.  Which model can be used? Is TP-Link TL-WN725N OK?

---

### Post by Bucky Ball on 2012-09-19
I've used a TP-Link with no problem. They have the Realtek driver from memory.

 The brand is not important, the wireless chipset is. You want to be looking for Realtek, Broadcom, Atheros. The very new ones might not work now but will, and the slightly older ones generally work 'out of the box'.

Not sure why you're not finding the manual, though. That should tell you what card you have and if it's not too brand new, it is a Ralink and they will generally work fine.

---

### Post by jiaweihuo on 2012-09-19
> **Bucky Ball said:**
> Gives no details at all. Find your computer on the Fujitsu link I gave if you can.

I just find the manual, but I cannot see the model of the wireless card. See the attachment.

---

### Post by Bucky Ball on 2012-09-19
Great stuff and well done finding it. That is one sweet machine and I'm guessing a very new model. I can find no information on running Ubuntu on one, let alone what wireless card it has and getting that up. You're right; I can't find the wireless card make or model anywhere either.

I'd get the dongle and as it's a Ralink the drivers for the internal wireless will arrive eventually. I'm out of ideas for now, sorry, but you might get lucky and someone who has wireless up on one of these beasts can jump in. Good luck. ;)

PS: Do you dual boot with Win? If so, get in there and check the details of the wireless card. Think it's Control Panel, and check out the Network Devices and see exactly what driver the card is using and especially what model it is.

PPS: Whatever it needs is going to look something like this:

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

---

### Post by jiaweihuo on 2012-09-20
> **Bucky Ball said:**
> 
PS: Do you dual boot with Win? If so, get in there and check the details of the wireless card. Think it's Control Panel, and check out the Network Devices and see exactly what driver the card is using and especially what model it is.

PPS: Whatever it needs is going to look something like this:

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)


Currently, I do not have a Win OS. I am going to install it via Virtue Box.

---

### Post by jiaweihuo on 2012-09-20
> **Bucky Ball said:**
> 
PS: Do you dual boot with Win? If so, get in there and check the details of the wireless card. Think it's Control Panel, and check out the Network Devices and see exactly what driver the card is using and especially what model it is.

PPS: Whatever it needs is going to look something like this:

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

I found that the model is Ralink RT 3290LE 802.11 b/g/n Wireless Lan adaptor. See the attachment. Sorry, it is not English because it is obtained from other's computer, but the same model of the machine.

---

### Post by jiaweihuo on 2012-09-20
Problem solved. See
[http://linuxforums.org.uk/index.php?topic=10422.0](http://linuxforums.org.uk/index.php?topic=10422.0)

I still have to thank this forum.

---

### Post by Bucky Ball on 2012-09-20
Great stuff. Enjoy. ;)

---

