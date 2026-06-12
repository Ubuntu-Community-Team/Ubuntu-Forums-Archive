---
title: "ubuntu 10.04 wired and wireless at same time"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by Rasta420 on 2012-02-20
Hello everyone

I am having a heck of a time getting both wired and wireless connections to work at the same time. I have googl'd and read so many different forum posts related to this but each one I try is to no avail.

I am a not a newb to linux but by the same respect i am not a guru by any means. Any help would be greatly appreciated.

I get Internet wirelessly from a provider, what I would like to do is share it with my other wired connections on the switch. I can use one or the other but not both at same time  :( I have wicd installed currently but can certainly change it if necessary

**[COLOR=Red]Rasta420@iPhone:/$ lspci[/COLOR]**
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
**[COLOR=Red]00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 05)[/COLOR]**
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
**[COLOR=Red]05:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)[/COLOR]**
05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]


Rasta420@iPhone:/etc/network$ cat interfaces
auto lo
iface lo inet loopback

# The primary network interface
[B][COLOR=Red]auto eth0
iface eth0 inet static
address 10.5.0.1
netmask 255.0.0.0
network 10.5.0.0
broadcast 10.5.0.255[/COLOR][/B]

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Thanks
Rasta420

---

### Post by Perkins on 2012-02-21
Most likely it is your network management program turning off one connection whenever you enable the other one.  Changing network managers or eschewing use of one entirely may solve the problem, but as I have never tried setting up a machine to share a wireless internet connection over a wire, I am not sure what the best way to do this would be.  Instructions for configuring a wireless connection via command line can be found via Google.  There are some variations based on the details of the wireless connection.


The simple, first thing to try would likely be to use your network manager to connect to the wireless, and then run:
```
sudo ifconfig eth0 up
```
to enable the wired interface.  With luck whatever hi-jinks your network manager program is trying to pull won't trigger.

If that works then you just need to use ifconfig to assign an address to eth0 (details in the ifconfig man page) and enable IP forwarding ([http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/](http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/)) and make sure your default route goes out through the wireless connection.

You may additionally wish to install a DHCP server on the machine so that you don't have to configure static addresses on the machines with which you are sharing the internet connection.

---

