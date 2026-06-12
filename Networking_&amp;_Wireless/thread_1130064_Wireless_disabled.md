---
title: "Wireless disabled?"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by WelshMikey on 2009-04-19
Sorry I have been trying to sort out this problem out for a while now but cant seem to get it to work. I am using wicd as my netowrk manager and running ubuntu 8.01 (64 bit). The drivers for my wirless card have been installed in three different ways so should be working (ndiswrapper, a windows driver installer program and a linux build thoug hthe linux build said "error 2")

I get this out put from lshw -c network

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32
  *-network
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:e0:4d:8f:1f:91
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f6:0b:d1:e8:22:9d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:ee:01:6c:ee
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  

any ideas what maybe wrong? I'm a little new to linux. Many thanks in advance =)

---

### Post by Ericyzfr1 on 2009-04-19
I may be off here, but if you do a right click on the network icon are the networking and wireless boxes checked?

---

### Post by WelshMikey on 2009-04-19
not sure what you mean sorry, if I right click the wicd icon then i get an options to either  connect, about or quit. If i open up my wicd then no wirless icons show up it just gives my wired connection and says no wireless networks. Also I dont actualyl know what to call my "wirelss interface" in preferences.

thought I had better add this information too: (out put from  ndiswrapper -l)

tnet1130 : driver installed
	device (104C:9066) present

---

### Post by t0mppa on 2009-04-19
> **WelshMikey said:**
> I get this out put from lshw -c network

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32


Just to tip you to the right direction: UNCLAIMED means that no driver has been associated with your wireless interface. Thus you need to do some more configuration/reinstalling. I have no experience with TI cards or NDISwrapper though, so can't really help there.

---

### Post by chili555 on 2009-04-19
Please do the following commands and let us know the outcome:```
sudo modprobe acx
sudo lshw -C network
```Is your wireless still UNCLAIMED? If so, please let us see:```
ndiswrapper -l
```Thanks.

---

### Post by WelshMikey on 2009-04-19
Cheers I had been wonderign what unclaimed meant, as for the outputs they are as follows:

1) sudo modprobe acx

FATAL: Module acx not found.

2)  sudo lshw -C network

 *-network UNCLAIMED     
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
  *-network
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:e0:4d:8f:1f:91
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.101 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5a:11:e4:60:fe:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

3) ndiswrapper -l

tnet1130 : driver installed
	device (104C:9066) present


NOTE: In relation to the above problem (output 1) I have both the acx-20071003 and acx20080210 versions of the acx driver for linux downloaded, but neither of them seem to build properly.acx-20071003 wont even start to build using the make command and the acx20080210 seems to work but then gives an output of "error 2" in the last line (once again using the make command)

---

### Post by chili555 on 2009-04-19
> seems to work but then gives an output of "error 2"When you try to compile a module and it ends in 'error', it is not ever going to work. I think your missing acx module is an example of a good plan gone bad:> FATAL: Module acx not found.For now, let's switch to plan B. Please do:```
sudo modprobe ndiswrapper
sudo lshw -C network
```You don't have to copy and paste the whole lshw, just tell us if UNCLAIMED has gone away. If it has, we can fine-tune your ndiswrapper setup and get you connected. If not, we will turn to Plan 9!

---

### Post by WelshMikey on 2009-04-20
cheers, tried it but It still says unclaimed

---

### Post by chili555 on 2009-04-20
Wonderful! It doesn't like *acx* and it won't bind to *ndiswrapper*! Let's see what the logs say about all this. Please do:```
sudo modprobe ndiswrapper
sudo cat /var/log/messages | grep ndis
```Thanks.

---

### Post by WelshMikey on 2009-04-20
Apr 20 17:24:15 welshmikey-desktop kernel: [   20.577493] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Apr 20 17:24:15 welshmikey-desktop kernel: [   21.170090] usbcore: registered new interface driver ndiswrapper
Apr 20 20:09:27 welshmikey-desktop kernel: [   13.373805] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Apr 20 20:09:27 welshmikey-desktop kernel: [   13.516449] usbcore: registered new interface driver ndiswrapper


Cheers for the help btw =) its much appreciated

just found something strange, firstly in /root there is a folder called acx with something called acx.ko in it? not sure what that is, also my kernel folder has no drivers folder in it is this normal?

---

### Post by chili555 on 2009-04-21
> /root there is a folder called acx with something called acx.ko in it? not sure what that is, also my kernel folder has no drivers folder in it is this normal?Not at all normal. It looks as if you tried to install acx-20071003 and acx20080210 and, while the 'make' ended in errors, you went on to 'sudo make install.' Trying to install a module based on a broken 'make' will never, ever work. Never.

For the moment, let's concentrate on the built-in acx.ko module that was in your original kernel. Please open a terminal and do:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those little backticks are on the same key with ~ on my US keyboard.

That should put acx.ko back in place, as well as any other unseen consequences of a failed 'sudo make install.' Then do:```
sudo modprobe acx
sudo lshw -C network
```Is the device still unclaimed?

---

### Post by WelshMikey on 2009-04-22
It now says disabled rather than unclaimed =) which sounds a little better to me :p

---

### Post by chili555 on 2009-04-22
Is this a laptop with a switch that has been nudged to 'off?' Also, please post:```
sudo cat /var/log/messages | grep -i kill
```Also, did the lshw output show a driver and logical name, like this?> description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       [COLOR="Red"]logical name: eth0[/COLOR]
       version: 00
       serial: 00:16:41:e6:cb:ef
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=e1000e [/COLOR]Thanks.

---

### Post by WelshMikey on 2009-04-24
The last command line gave no output, with regards to the other question the configoration output part said:

autonegotiation=on, boadcast=yes, diver = forcedeth, drive version = 0.61, latency=0, link=0, maxlatency = 20, mingnt = 1, module = foredeth, multicast = yes, pot = MII



just some extra info, not sue if needed: my mother board (with the lan) is a nvidia gefoce 8100 and the pci wieless cad is unbranded. Im lso unning 64 bit ubuntu linux.     

sorry for late reply, been moving house.

---

### Post by chili555 on 2009-04-25
> autonegotiation=on, boadcast=yes, diver = forcedeth, drive version = 0.61, latency=0, link=0, maxlatency = 20, mingnt = 1, module = foredeth, multicast = yes, pot = MIIYou've given us the ethernet details but we are trying to see if the acx module has attached to the wireless card. Please do:```
sudo modprobe acx
sudo lshw -C network
```> description: Network controller
product: ACX 111 54Mbps Wireless Interface
vendor: Texas Instruments
physical id: 8
bus info: pci@0000:01:08.0
[COLOR="Red"]logical name: ???[/COLOR]
version: 00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=32
[COLOR="Red"]driver: ???[/COLOR]What do you see?

---

### Post by WelshMikey on 2009-04-26
Your a genius ^_^ I can pick p wireless now, but cant seem to connect to wpa encypted netwok through wicd?

the data you requested were:
wlan1
acx_PCi

---

