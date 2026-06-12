---
title: "No wireless on Acer Aspire 5735"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Aperl on 2009-02-13
So I'm completely new to the world of linux and I can't for thelife of me figure out whats wrong.
Marvell Yukon 88E8071 PCI-E GIGABIT ETHERNET CONTROLLER is the wireless adapter
When I try to update the proprietary drivers it says there are none which I seems unlikely at best I tried to hunt down some drivers but as of yet no such luck.
Has anybody had a similar problem or know how to approach this problem, also my wired ethernet works just fine...

---

### Post by chili555 on 2009-02-13
I believe the Marvell Yukon ***is*** your wired connection. Let's dig a bit deeper and see if we can find the wireless. Please open a terminal and do:```
sudo lshw -C network
```Your wired *and* wireless will show up. You can search the forum or post back and we'll help you.

---

### Post by Aperl on 2009-02-13
his is all of the info it spat out

Wireless driver:iwlagn
Wireless Adapter:88E8071 PCI-E Gigabit Ethernet Controller (Marvell Yukon)

  *-network               
       description: Ethernet interface 
       product: 88E8071 PCI-E Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 16 
       serial: 00:1d:72:ea:e6:e7 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair 
  *-network DISABLED 
       description: Wireless interface 
       product: Intel Corporation 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wmaster0 
       version: 00 
       serial: 00:21:6b:02:15:98 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn 

The first 2 lines are my own

---

### Post by chili555 on 2009-02-14
> The first 2 lines are my ownThe Marvell Yukon is *not* wireless. The second entry:> *-network DISABLED
description: Wireless interface is clearly your wireless. We have a hurdle to jump before we can nudge it to life. This:> *-network DISABLEDsuggests that the wireless card is disabled in the BIOS, disabled by a little slide switch on the laptop or disabled by the appropriate key combination, Fn+F5, for instance.

Does the wireless LED light up?

Manipulate the switch or key combination and run ```
sudo lshw -C network
```See if DISABLED goes away.

---

### Post by Aperl on 2009-02-15
Problem is neither of those key combos work and my wireless button doesn't do anything...

---

### Post by chili555 on 2009-02-15
Wow! Nothing, eh?

May we please look at:```
dmesg | grep -i kill
lsmod | grep acer
sudo tail -f /var/log/messages
```This last command will remain open and print kernel messages until you stop it with Ctrl+c. While it's open, manipulate your wireless button and see if the kernel is aware of the button presses.

---

### Post by Aperl on 2009-02-15
it seems to detect the button presses and now my wireless "kill switch" in the kernels words lights up and it detects my network but won't allow me to connect, it says dhcdbd: Unrequested down after I try to connect and asks for my passphrase again.

---

### Post by ASchweitzer on 2009-02-16
Hey Perl
You're running 64 bit, correct? and are you using WEP or WPA/WPA2?

---

### Post by Aperl on 2009-02-16
Yes I'm running 64 bit and its WEP I was detecting the network for a bit then i lost it now I'm back to square one... I'm a wee bit frustrated is it a problem with drivers, or maybe 64 bit on my computer...

---

### Post by SoCentral2 on 2009-03-27
I'm having the same problem. I have an Acer Aspire 5735 and I've just installed Ubuntu Studio 8.10 so it dual boots Vi$ta and Ubuntu.My listing is similar to the one above - the WiFi connection is shown as DISABLED. Pressing the button doesn't do anything and there don't appear to be any FN+(x) keyboard combinations.

This thread seems to have faded away, which is a shame - it's always nice to hear resolutions and work-arounds. 

I'm not sure what do next. I'm tempted to try Windoze drivers. Suggestions are welcome.

Paul.

---

### Post by ASchweitzer on 2009-03-27
We never did find a solution, really. Although ndiswrapper was working for half a day, so go ahead and give that a shot. What wireless hardware do you have?

---

### Post by SoCentral2 on 2009-03-27
It's an 'Intel Wireless WiFi Link 5100'. The listing below show's that it's detected but remains DISABLED. I'm finding bug reports on iwlagn (e.g. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284069]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284069")) so it's not looking too promising. 

 sudo lshw -C network
[sudo] password for <my machine>: 
  *-network DISABLED      
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:d7:e0:96
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:79:b3:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 42:6e:0c:10:97:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by ASchweitzer on 2009-03-27
If you're willing to play with it, try ndiswrapper. You won't get extended driver functionality out of that though (like packet injection, monitor mode, etc). For that you pretty much need madwifi, which doesn't support intel cards. Run
```
lspci
```
to see if there's any other hardware info output, though I doubt it

---

### Post by Aperl on 2009-03-30
I got to the point where I was using ndiswrapper to emulate the windows drivers it worked when it wanted A few days later I ended up taking the computer back under warenty. If I was me which I am I would try ndiswrapper and see if that works you miught have more patients than I do.

---

### Post by rodneymillerpca on 2009-03-30
This is a wide spread problem. I tried tut after tut. Then I found this tut and had my Aspire 4520 with Ubuntu 8.04 up in less then 15 minutes. See my notes on last post. [http://www.hp2133guide.com/forums/viewtopic.php?p=10230](http://www.hp2133guide.com/forums/viewtopic.php?p=10230)

---

