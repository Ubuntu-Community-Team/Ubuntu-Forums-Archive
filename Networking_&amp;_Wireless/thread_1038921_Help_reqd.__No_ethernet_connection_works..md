---
title: "Help reqd.  No ethernet connection works."
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by ferrisxb9r on 2009-01-14
Not a 1st time Ubuntu user, but definitely a nix noob.  Last attempt to embrace was 6.10 Edgy.  I'm not a complete techno-dumbass, but I will readily admit I'm totally at sea when it comes to any command line interface commands for linux.  I don't know any except what I've been browsing here to try to help me.

Ok, long story short:  Installed Ubuntu 8.10 via the live cd, on a pre-existing Windows Vista install.  10gig partition, on secondary HDD.  *** NO ETHERNET WORKY *** but only when on Ubuntu.  Connects to a Belkin N1 Vision router, which is running DHCP.  I can ping nothing except my own ip when I manually make one.

The 8.10 install is using Network Manager 0.7 obviously.  I made the stupid mistake of removing network-manager-gnome and then trying to use just the /etc/network/interfaces file to manually set it all up, but to no avail, and then I couldn't figure out how to re-install the n-m-g.  So fresh installed it again.  (FWIW I also tried just playing with it via the live cd boot, and no joy either, on this computer and another laptop wirelessly)  So I have the Network Manager running again.

I've tried deleting the auto eth0 and eth1 connections and remaking them from scratch, to no avail.  I've also tried deleting /etc/network/interfaces to no avail also.  For all intents and purposes, eth0 is the interface I normally connect to the router (and therefore, the internet.)

Ok, so I gather that these commands are needed for you guys to help me:
lspci
sudo lshw -C network and
ifconfig

so without further adieu, here goes:
```
lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
03:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)

```

```
sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:15:6c:0c:be:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
Now even I can see there's a problem there, but I don't know what I need to type to fix it.

And finally, ifconfig...
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:05:b7:b5  
          inet6 addr: fe80::21b:fcff:fe05:b7b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3952 (3.9 KB)
          Interrupt:247 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:05:d3:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:248 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:368 (368.0 B)  TX bytes:368 (368.0 B)

```

So please, I humbly beg you Ubuntu Gurus to help me find the problem and fix it.  I really want to embrace this OS and learn as much as I can from it.

---

### Post by Iowan on 2009-01-14
No begging required... May not fix the problem, but try adding a line to /etc/network/interfaces:
```
auto eth0
```

---

### Post by ferrisxb9r on 2009-01-14
oddly enough, /etc/network/interfaces didn't exist.  I HAD deleted it in the previous install, but it didn't appear in the directory with the fresh install.

sudo gedit /etc/network/interfaces gave me a "error does not exist" then opened up a blank file for me.  I added the code you provided.  Should I also add

```
auto lo
iface lo inet loopback
```

above the code you provided me?

Nothing changed btw.  After each change I do a reboot.  The network manager gets as far as "requesting address from wired network..." before it fails.

---

### Post by Iowan on 2009-01-14
Yes, you'll need the loopback definition.  It also seems curious that **lshw** shows the interface as **pan0**. (I thought **pan** was personal area network... bluetooth). Hmmm, now I gotta remember where the interfaces are aliased...

---

### Post by ferrisxb9r on 2009-01-14
(typing on phone, so apologies for lack of formatting on this post)

Auto eth0 added, along with the loopback lines. FYI this is a desktop pc I built, and it has no Bluetooth capabilities. Just 2 nics in it, no wireless card either.

---

### Post by Iowan on 2009-01-14
Until I can find where that file is, try replacing **eth0** with **pan0** and restart networking.  Probably won't work, but...

---

### Post by ferrisxb9r on 2009-01-14
Ok I'll have a crack at that.

Any advice that doesn't involve me having to do any programming or compiling (not yet anyway.  :D  ) is welcome advice.  I'll have a go with pan0 instead of eth0.  I do know that eth0 and eth1 were sort of working yesterday, I could see them in the Administration>Network Tools area.  Oddly though, the inet always comes up with (it LOOKS like) an odd sort of address.  It looks like a mac address, but with really freaky hexadecimal.  

Playing with network manager I can never get eth0 to have an inet address how I'd like it. Even trying static IP etc,  192.168.x.x  I know the netmask needs to be binary style (eg: for a netmask of 255.255.255.0 I need to have "24" as the netmask)

It's kind of frustrating that I don't know how to troubleshoot with this OS yet, but I'm thankful that the ubuntu boards are full of helpful people.  I appreciate the help thus far.

I just wish it was ANYTHING ELSE but the networking that didn't work out of the box.  :D

---

### Post by Iowan on 2009-01-14
Maybe the file I seek is in here: /etc/udev/rules.d

---

### Post by Loosewheel on 2009-01-14
> **Iowan said:**
> Maybe the file I seek is in here: /etc/udev/rules.d

'/etc/udev/rules.d/70-persistent-net.rules'   
"This file maintains persistent names for network interfaces.
# See udev(7) for syntax". (Like eth0 or eth1, matched to a MAC)

'/etc/udev/rules.d/75-persistent-net-generator.rules'
"these rules generate rules for persistent network device naming"
(Like:  "MATCHADDR             MAC address used for the match")

So you might want to compare MAC's in '...net.rules, and 'ifconfig'.  ('udev' could rename eth0 to eth1).....

Is the driver installed? I have MCP51 and use the 'forcedeth' kernel module. Try 'lsmod' , and see if they are listed. Two NIC's, right?

And did you alredy click on the nm-applet and try to config manually using DHCP? Then maybe '/etc/init.d/networking restart'

---

### Post by Iowan on 2009-01-14
> **Loosewheel said:**
> '/etc/udev/rules.d/70-persistent-net.rules'   
Yup - that'd be the one... Thanks!!!

---

### Post by ferrisxb9r on 2009-01-14
Ok, I'm actually posting to you via the ubuntu 8.10 install, using a usb wireless dongle I found lying around.  Plugged it in, booted up, the wired connections failed as usual, I clicked the wifi link in network manager, and viola, I'm online.

So, the wifi bit worked.  This is a bandaid solution, as I can't use this PC on a wifi link forever, the bandwidth is just too low.

I'm performing the update manager at the moment, I'll let it update, then I'll have a look at /etc/udev/rules.d/70-persistent.net.rules and see what the mac address is listed in there.  I know what the mac address' SHOULD be for the 2 nics.


Report back to you guys shortly.  Thanks again.

---

### Post by ferrisxb9r on 2009-01-15
Ok doing a gedit of the /etc/udev/rules.d/70-persistent-net.rules gives me:

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0373 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR="Red"]THE CORRECT MAC ADDRESS REMOVED BY ME IN POSTING[/COLOR]", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10de:0x0373 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR="Red"]THE CORRECT MAC ADDRESS REMOVED BY ME IN POSTING[/COLOR]", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x1044:0x8008 (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR="Red"]THE CORRECT MAC ADDRESS REMOVED BY ME IN POSTING[/COLOR]", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```

So the correct MAC addresses are located in the file.

I'm still posting via the wifi card which plug and played immediately with network manager.

---

### Post by Loosewheel on 2009-01-16
> **ferrisxb9r said:**
> Ok doing a gedit of the /etc/udev/rules.d/70-persistent-net.rules gives me:

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0373 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR="Red"]THE CORRECT MAC ADDRESS REMOVED BY ME IN POSTING[/COLOR]", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10de:0x0373 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR="Red"]THE CORRECT MAC ADDRESS REMOVED BY ME IN POSTING[/COLOR]", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x1044:0x8008 (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="[COLOR="Red"]THE CORRECT MAC ADDRESS REMOVED BY ME IN POSTING[/COLOR]", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```

So the correct MAC addresses are located in the file.

I'm still posting via the wifi card which plug and played immediately with network manager.

Hi ferrisxb9r,
Looks like the same device "PCI device 0x10de:0x0373 (forcedeth)" is named 'eth0 and eth1....try 'sudo nano /etc/udev/rules.d/70-persistent-net.rules' and comment out with '#' the line that starts with 'SUBSYSTEM=="net" on the entry with 'NAME="eht1"'. If it works, you could go back and delete the entry for 'eth1'.

---

### Post by ferrisxb9r on 2009-01-16
I don't have nano, I have gedit, same thing though, right?
I'll try what you've suggested, but I'm not surprised the device is listed twice, as it's onboard lan 2 nics.  I have 2 ethernet ports supplied by my motherboard.

Either way I'll give your suggestion a try.  Thanks.  Report back soon.

(btw, I've been having problems with the gnome-display-manager when I enable the nvidia drivers, so I'm occasionally off the air while I purge the mistakes.  )  Thanks for your patience.

***EDIT: one more thing, should these changes require a reboot?  Or can I forgoe that and just try using the nm?  I've always rebooted after every change I make, and I wasn't sure if its necessary or not.

---

### Post by Loosewheel on 2009-01-16
You're right...two controllers, two MAC's...yea, two entries.
So nerver mind that idea. 
Is the kernel driver installed? 

'lsmod | grep forcedeth'

---

### Post by ferrisxb9r on 2009-01-16
```

ferris@ubuntu:~$ lsmod | grep forcedeth
forcedeth              68112  0 
ferris@ubuntu:~$ 

```

---

### Post by Loosewheel on 2009-01-16
> **ferrisxb9r said:**
> ```

ferris@ubuntu:~$ lsmod | grep forcedeth
forcedeth              68112  0 
ferris@ubuntu:~$ 

```

Yep, it's in there. Here's part of 'lshw -C network' from another box with 8.10.

And 'sudo lshw -C network':
 *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 02
       serial: xx:xx:xx:xx:xx:xx 
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.45 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

I know....your original question.

I'm kinda at a loss.

---

### Post by ferrisxb9r on 2009-01-16
Thanks for trying, Loosewheel.  ;)

---

### Post by Loosewheel on 2009-01-16
You bet.

And you know, 'lshw' doesn't always work on this 64bit 8.04 system.
But 'lshw -short' works every time.

Also, " lshw is a small tool to extract detailed information "
and Network Manager gets its info via dbus from hal.

'lshal | grep forcedeth' should show the linux driver.

anyhow, I'm out of here...Good Luck

---

