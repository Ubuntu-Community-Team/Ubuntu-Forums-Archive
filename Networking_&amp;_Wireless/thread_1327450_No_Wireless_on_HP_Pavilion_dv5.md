---
title: "No Wireless on HP Pavilion dv5"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by emmanuelchavez on 2009-11-15
Hi all.  New to the forum/community/ubuntu.  I've recently decided to do a clean-install of Ubuntu 9.10 onto my laptop, rather than forking out unnecessary amounts of cash on Windows 7.  I tried Ubuntu once before on a dell laptop, a couple of years ago, but removed it for my inability to get wireless working.  I've spent an incredible amount of time trying to find a way to get things working, but I've seen no results, where other people have. :(

running the lspci -v command i get:

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3602
    Flags: bus master, fast devsel, latency 0, IRQ 31
    I/O ports at 6000 [size=256]
    Memory at d1410000 (64-bit, prefetchable) [size=4K]
    Memory at d1400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d1420000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169



I've also tried going to System -> Administration -> Hardware Drivers.  I have the option of activating 'Broadcom STA wireless driver'.  However, when I click activate, then type my password to authorize, it still remains inactive, even after restarting.


Currently, I'm using a wired connection.  Can anyone offer any type of solution?  My Vista recovery CDs decided they weren't going to work... so I'm left with only Ubuntu as an OS (plus, I never want to go back to Vista)

I'd really like to get wireless working before I have to go to school tomorrow... considering how I have a ton of online assignments.

Any help is appreciated.  Many thanks!

---

### Post by emmanuelchavez on 2009-11-15
nothing?

---

### Post by mikewhatever on 2009-11-15
Basically, you need to hook up a cable and install the required packages manually. Check out the guide.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by emmanuelchavez on 2009-11-15
You are awesome! Thank you! It took a couple of tries to get it, but it's finally working.

---

### Post by sioux_cyclist on 2009-11-30
Hi everyone.  I am VERY new to this Ubuntu forum and...well...forums in general but I'm really hoping you smart guys/gals can help me out here.

I have an HP Pavilion dv5 on which I installed Ubuntu 9.10 and I CANNOT get this stinkin' wireless working.  When I run "lshw -C network" this is what comes up:

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:db600000-db603fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:89:5b:b6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.109 latency=0 multicast=yes
       resources: irq:31 ioport:6000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)

In System>Administration>Hardware Drivers I have the Broadcom STA Wireless driver selected and at the bottom it says, "This driver is active but not currently in use." with a green light next to it.

I really hope that all aids in the diagnosis.

---

### Post by sioux_cyclist on 2009-12-01
All is well.  This is what worked for me: Did a fresh install, got a wired connection, ran the update manager **(System>Administration>Update Manager), **opened a terminal and ran:

sudo apt-get update
sudo apt-get upgrade

Then followed directions below.  Although, I'm not totally sure the two command lines did anything or if the first two links provided were necessary after running the update manager, but I ran them out anyway to be sure.

>                      Originally Posted by **kut77less**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8211551#post8211551")                 
                 [I]Well it worked!!!!

But I did it a different way. I downloaded 

dpkg-dev (and some dependencies for it) 

[http://packages.ubuntu.com/karmic/dpkg-dev](http://packages.ubuntu.com/karmic/dpkg-dev)

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)

And then I ran 

     Code:
     sudo dpkg-reconfigure bcmwl-kernel-source 
And Then 

                                   Code:
     sudo modprobe -r b43 ssb wl
 sudo modprobe wl 
It finally worked. 

Thanks for all your help.[/I]


---

