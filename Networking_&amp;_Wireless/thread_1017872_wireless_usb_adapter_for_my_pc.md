---
title: "wireless usb adapter for my pc"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by busky147 on 2008-12-21
i  just bought a (Netgear) wireless usb adapter,to make my pc wireless,but i can't get it to work,i need help please.

---

### Post by pytheas22 on 2008-12-21
Please plug the adapter in, run the following command and post the output here:
```

lsusb
```

---

### Post by busky147 on 2008-12-21
> **pytheas22 said:**
> Please plug the adapter in, run the following command and post the output here:
```

lsusb
```
home@home-desktop:~$ lsusb
Bus 005 Device 002: ID 0846:9010 NetGear, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
home@home-desktop:~$

---

### Post by busky147 on 2008-12-21
home@home-desktop:~$ lsusb
Bus 005 Device 002: ID 0846:9010 NetGear, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
home@home-desktop:~$

---

### Post by pytheas22 on 2008-12-21
Please try running these commands (make sure you are plugged into the Internet via ethernet first):
```

sudo apt-get install git git-core build-essential
git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/otus.git ~/Desktop/otus
cd ~/Desktop/otus
make
sudo make install
```

This will compile and install a Linux driver for your device.  After it's done installing, please reboot, then post the output of:
```

sudo modprobe otus
lshw -C Network
lsmod | grep otus
sudo iwlist scan
```

As a disclaimer, I spent a long time last week trying to help [someone else]("http://ubuntuforums.org/showthread.php?t=989653&page=3") with this same adapter--Netgear WNDA3100--and we still haven't solved it.  It seems that this is a very new device.  A Linux driver first appeared for it about a month ago, and it compiled but didn't seem to work so well--although that was a week ago, and by now it may work better using the latest snapshot of the code.  So please try following the instructions above, and we can take it from there.

---

### Post by busky147 on 2008-12-22
i still can't get it to work,i've been trying all night to make it work but i can't,what can i do now?,am getting fustrated please try to help me

---

### Post by pytheas22 on 2008-12-22
Please run all of these commands and post the total output here:
```

sudo apt-get install git git-core build-essential
git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/otus.git ~/Desktop/otus
cd ~/Desktop/otus
make
sudo make install
sudo modprobe otus
lshw -C Network
lsmod | grep otus
sudo iwlist scan
```

It will be long but I need to see that stuff in order to be able to help.

---

### Post by busky147 on 2008-12-22
home@home-desktop:~$ sudo apt-get install git git-core build-essential
[sudo] password for home: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
git-core is already the newest version.
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic python-bittorrent
  bittorrent
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
home@home-desktop:~$

---

### Post by pytheas22 on 2008-12-22
It looks like you completed the first command successfully, but please run all of these others as well (one per line) and post the output from each one:
```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/otus.git ~/Desktop/otus
cd ~/Desktop/otus
make
sudo make install
sudo modprobe otus
lshw -C Network
lsmod | grep otus
sudo iwlist scan
```

---

### Post by busky147 on 2008-12-23
home@home-desktop:~$ git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/otus.git ~/Desktop/otus
Initialized empty Git repository in /home/home/Desktop/otus/.git/
remote: Counting objects: 266, done.
remote: Compressing objects: 100% (126/126), done.
remote: Total 266 (delta 138), reused 217 (delta 118)
Receiving objects: 100% (266/266), 885.46 KiB | 310 KiB/s, done.
Resolving deltas: 100% (138/138), done.
home@home-desktop:~$

---

### Post by busky147 on 2008-12-23
home@home-desktop:~$ cd ~/Desktop/otus
home@home-desktop:~/Desktop/otus$

---

### Post by busky147 on 2008-12-23
home@home-desktop:~$ make
make: *** No targets specified and no makefile found. Stop.
home@home-desktop:~$ sudo make install
make: *** No rule to make target `install'. Stop.
home@home-desktop:~$ sudo modprobe otus
FATAL: Module otus not found.
home@home-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: eth0
       version: 01
       serial: 00:17:a4:15:a1:bb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5752-v3.10 ip=192.168.1.64 latency=0 module=tg3 multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ath0
       serial: 00:03:7f:11:22:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-MIMO
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:38:d6:39:81:2c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
home@home-desktop:~$ lsmod | grep otus
home@home-desktop:~$ sudo iwlist scan

---

### Post by busky147 on 2008-12-23
i dont know if am asking too much,i would like u to do it for me,using remote desktop to control my desktop,because am not really good with computers programmes, like what am doing now,will u be able to help me?,i would really really appreciate,please let me know so i can allow u access

---

### Post by skyrate on 2009-01-11
Hi..

I have been following this thread from the start (the first one wich leads to this one)..

I have a D-Link dwa160 usb wireless adapter and tryied to do the tips in the thread.

I lost track when i compiled otus driver and the other guy got ath0 up in the  lshw -C Network

I stil does not have this interface up and running. I have tryied to use ndiswrapper with windows drivers installed and always got the ndsiwrapper -l to tell the right ID and that the adapter was present. But still no success..

here is the list output from me:

eirik@eirik:~$ sudo modprobe otus
[sudo] password for eirik: 
FATAL: Module otus not found.
eirik@eirik:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth1
       version: 74
       serial: 00:04:76:0d:ee:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth0
       version: 03
       serial: 00:01:80:60:07:1d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5788-v3.04 ip=10.0.0.30 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:0b:20:61:be:28
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
eirik@eirik:~$ lsmod | grep otus
eirik@eirik:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eirik@eirik:~$ ndiswrapper -l
arusb_lh : driver installed
	device (07D1:3C10) present (alternate driver: arusb_lnx)
eirik@eirik:~$ lsusb
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:3c10 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---------------
Hope this can be helpful if there is help to be given :)

Regards

Frode

---

### Post by pytheas22 on 2009-01-11
skyrate: what is the output of:
```

lsmod | grep -e ndis -e ar
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
sudo rmmod ndiswrapper
sudo modprobe arusb
dmesg | grep -e arusb -e ath
iwconfig
```

---

### Post by bij33 on 2009-03-13
I have exactly the same problem. I followed the instructions on the site below with installation of latest ndiswrapper but Ubuntu still doesn't see the DWA-160. The bad thing is D-Link does not support Linux any longer, not sure they ever did... 
([http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847))
Hope you do have a better luck than I do. I don't believe there are any Linux driver for chipset 07D1:3C10 (dwarusb_xp). I'll check the postings soon.

Thanks,

---

### Post by pytheas22 on 2009-03-14
bij33: there are native Linux drivers in development for this card (thanks to volunteers, not D-Link), but they may not work well yet.  If you want to give them a try, though, run these commands to check out the latest code and compile it:
```

sudo apt-get install git git-core build-essential
git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/otus.git ~/Desktop/otus
cd ~/Desktop/otus
make
sudo make install
```

Then reboot.  If you're lucky, the card will work.  If so, please report here.

You may also have better luck under ndiswrapper if you try different Windows drivers.  [This thread]("ubuntuforums.org/showthread.php?t=885847") might also help you troubleshoot ndiswrapper problems.

---

### Post by bij33 on 2009-03-14
Thanks for the link and instructions to native Linux drivers. I am still working on ndiswrapper issues. I think I need to add a couple of lines to the blacklist.
One thing I do not understand is, can I have both wired and wireless drivers installed in Ubuntuat like Win XP? I read somewhere that I need to uninstall the wired driver in order for ndiswrapper to work with wireless card driver.
Presently I am conected to this forum via my wired connection as I am tying this and hope that has not effected the output below.

Here are the list output from me:

root@p670:/etc# ndiswrapper -l
dwarusb_xp : driver installed
	device (07D1:3C10) present
root@p670:/etc#

root@p670:/etc# lsusb
Bus 005 Device 003: ID 07d1:3c10 D-Link System 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 002 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@p670:/etc#

root@p670:/etc# lshw -C Network
  *-network               
       description: Ethernet interface
       product: 82545GM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: e
       bus info: pci@0000:03:0e.0
       logical name: eth0
       version: 04
       serial: 00:11:43:16:ac:d9
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=1GB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:87:10:39:9d:d7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@p670:/etc#

root@p670:/etc# cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
root@p670:/etc#

root@p670:/etc# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:43:16:ac:d9  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe16:acd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1500874 (1.5 MB)  TX bytes:213867 (213.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4808 (4.8 KB)  TX bytes:4808 (4.8 KB)

pan0      Link encap:Ethernet  HWaddr 5e:87:10:39:9d:d7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@p670:/etc#

root@p670:/etc# cat /etc/network/interfaces
auto lo
iface lo inet loopback

root@p670:/etc#


Thanks,

---

### Post by pytheas22 on 2009-03-14
bij33: of course you can have both wired and wireless drivers installed in Ubuntu at the same time.  I don't know who suggested otherwise, but it's not true.

I'm not sure why ndiswrapper is not bringing up your card, but if you post the output of this command, it might give an explanation:
```

dmesg | grep -e ndis -e wlan
```

---

### Post by bij33 on 2009-03-15
Thanks again for your support and explaining the drivers on both wired and wireless cases. This is the result of the command:

root@p670:/# dmesg | grep -e ndis -e wlan
[   32.378578] ndiswrapper version 1.54 loaded (smp=yes, preempt=no)
[   33.043711] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'NlsMbCodePageTag'
[   33.044043] ndiswrapper (load_sys_files:206): couldn't prepare driver 'dwarusb_xp'
[   33.045001] ndiswrapper (load_wrap_driver:108): couldn't load driver dwarusb_xp; check system log for messages from 'loadndisdriver'
[   33.045093] usbcore: registered new interface driver ndiswrapper
root@p670:/#

---

### Post by pytheas22 on 2009-03-15
These lines indicate that ndiswrapper doesn't like the Windows drivers that you loaded into it:
```

root@p670:/# dmesg | grep -e ndis -e wlan
[ 32.378578] ndiswrapper version 1.54 loaded (smp=yes, preempt=no[B])
[ 33.043711] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'NlsMbCodePageTag'
[ 33.044043] ndiswrapper (load_sys_files:206): couldn't prepare driver 'dwarusb_xp'
[ 33.045001] ndiswrapper (load_wrap_driver:10: couldn't load driver dwarusb_xp; check system log for messages from 'loadndisdriver'[/B]
[ 33.045093] usbcore: registered new interface driver ndiswrapper
```

Unfortunately there's not much that you can do about it.  You might have better luck if you used a different version of the Windows driver--for example, use version 1.0 instead of 2.0, or the one for Windows 2000 instead of Vista.

I remember doing some research on this a few months ago, however, and wasn't able to find anyone who had succeeded in getting this card running with ndiswrapper.  So you may be out of luck entirely on that front, unfortunately, in which case your best hope is to try compiling the 'otus' driver and hope it works better now than a few months ago.

---

### Post by bij33 on 2009-03-15
pytheas22; Thanks for your input. I just returned it back to the store. Now I am looking for another USB Wireless card that works with Ubuntu.
Are there any that you can recommend or I have to wait till the next release of Ubuntu?
And what is the command for uninstalling this latest version of ndiswrapper?

Thank you,

---

### Post by pytheas22 on 2009-03-16
> Are there any that you can recommend or I have to wait till the next release of Ubuntu?

There's a list of [well-supported wireless cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") that you could consult.  It may not be completely up to date, however, and some of the devices listed there may have multiple revisions, meaning that the version you buy might not be the same one that works well with Linux, even though they both have the same name.

I've also had luck in the past buying cards online on sites like amazon.com or newegg.com and reading customer comments; usually someone will make a note if the wireless card works well with Linux.
> 
And what is the command for uninstalling this latest version of ndiswrapper?

There's probably no real need to uninstall ndiswrapper, but you can do it with this command if you like:
```

sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by bij33 on 2009-03-20
pytheas22; Thanks for the list of wireless cards, I'll check it out. For now I use wired connection till we get a better support.

---

### Post by Scubdup on 2009-03-20
Bij33, when I first started playing around with Ubuntu I tried and failed to get a Netgear dongle working.

I struggled with the list of compatible cards. After a fair bit of research I found out that Edimax are a company who manufatcure wfi cards and USB dongles and they are pretty Linux-community friendly.

I bought a USB Wifi dongle made by them for £12 (about $18 ) and it worked straightaway without the need for any addition work or downloads. From my experience I recommend them highly.

---

### Post by bij33 on 2009-03-22
Scubdup; Thanks for recommending the Edimax, I need to call their tech support and get the model number(s) for USB _N_ wifi adapters. I looked at a couple of them but unfortunately Linux was not one of the supported O.S. on their list.

---

### Post by pytheas22 on 2009-03-22
> Scubdup; Thanks for recommending the Edimax, I need to call their tech support and get the model number(s) for USB N wifi adapters. I looked at a couple of them but unfortunately Linux was not one of the supported O.S. on their list.

You might also want to ask for the device ID numbers (which are hexadecimal, in the form XXXX:XXXX) so that you can look them up that way.  Sometimes wireless-card manufacturers change the insides of the cards without changing the names, so looking them up by the device ID is the only sure way to know which device is which and make sure it runs on Linux.

Also, most hardware manufacturers don't say their devices are supported on Linux because they don't want to deal with support problems for Linux users.  But that doesn't mean the devices don't work with Linux; in most cases there's a community-developed drive that will support the device.

---

### Post by rickzoll on 2009-04-02
> **pytheas22 said:**
> bij33: there are native Linux drivers in development for this card (thanks to volunteers, not D-Link), but they may not work well yet.  If you want to give them a try, though, run these commands to check out the latest code and compile it:
```

sudo apt-get install git git-core build-essential
git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/otus.git ~/Desktop/otus
cd ~/Desktop/otus
make
sudo make install
```
ave 
Then reboot.  If you're lucky, the card will work.  If so, please report here.


I gave this a try as I also have a DWA-160 usb adaptor.  Below is what I can now see. Is there a next step?
rickul@sun:~$ iwconfig
ath0      IEEE 802.11-MIMO  Frequency:inf GHz  Access Point: Not-Associated   
          Sensitivity=0  
          Power Management:on

---

### Post by pytheas22 on 2009-04-02
rickzoll: I'm not sure what that means, as I've never seen iwconfig output like that.  But it looks like the driver has at least recognized your interface, which is definitely good.  Are you able to connect to access points?  Can you at least see access points by typing:
```

sudo iwlist scan
```

---

### Post by rickzoll on 2009-04-05
rickul@sun:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

ath0      Interface doesn't support scanning.

The pan0 and ath0 interfaces seem to be new.  I have wlan0 working with a builtin Broadcom "g" interface but I really want to get my DWA-160 usb "N" adaptor which I've seen connect in Windows as high as 119 MB.
TIA, rickzoll

---

### Post by rickzoll on 2009-04-05
Additional information:
rickul@sun:~$ sudo lshw -C Network
[sudo] password for rickul: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:c6:7b:31
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.199 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:c3:fa:47
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:ad:6f:c6:ef:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:2 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: ath0
       serial: 00:03:7f:11:22:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-MIMO
TIA.

---

### Post by pytheas22 on 2009-04-05
**rickzoll**: your output indicates that ath0 is disabled:
```

*-network:2 **DISABLED**
description: Wireless interface
physical id: 3
logical name: ath0
serial: 00:03:7f:11:22:33
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-MIMO
```

but unfortunately it's not clear why.  Usually when it says that, the problem is that the wireless card is switched off, but I assume there's no button on your USB stick for turning the card on and off, right?

It's also possible that the interface is just down.  If you type:
```

sudo ifconfig ath0 up
```

and then run 'lshw -C Network' again, does the entry for 'ath0' still list it as disabled?

It would also be helpful to see the output of:
```

dmesg | grep ath0
```

which may also contain a clue as to why it's not working.

---

### Post by rickzoll on 2009-04-05
Lookks like the command activated the interface:
sudo ifconfig ath0 up
I rebooted to see if it would start by itself but no - I had to issue the command again.  See the other results below.  When I try to connect (I now see many wireless sites), it always prompts me for my WPA passphrase but it never connects.
  
rickul@sun:~$ dmesg | grep ath0
[  299.672036] ath0: no IPv6 routers present
rickul@sun:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:22:b0:54:43:60  
          inet6 addr: fe80::203:7fff:fe11:2233/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1b:24:c6:7b:31  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fec6:7b31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2050586 (2.0 MB)  TX bytes:171220 (171.2 KB)
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10760 (10.7 KB)  TX bytes:10760 (10.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:c3:fa:47  
          inet6 addr: fe80::21a:73ff:fec3:fa47/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139083 (139.0 KB)  TX bytes:5417 (5.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-C3-FA-47-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by pytheas22 on 2009-04-06
It's definitely good that you can now see networks with ath0 (assuming you're sure it wasn't just wlan0 seeing them--if in doubt, run the command 'sudo iwlist ath0 scan' and see if you get a list of networks).  You might have better luck actually completing the connection if you use wicd instead of NetworkManager.  You can install wicd by typing:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  Click 'Preferences' and make sure the wireless interface is set to 'ath0' (it will probably be set to 'wlan0' by default).  Then try connecting; any luck?

Note that installing wicd will force the uninstallation of NetworkManager.  If you want NM back later, just type:
```

sudo apt-get install network-manager-gnome
```

---

### Post by rickzoll on 2009-04-06
We're getting there...,, now,,, with the Wicd Manager I get: This network requires encryption to be enabled.

---

### Post by pytheas22 on 2009-04-06
Interesting, I've never seen that message in wicd before.  Did you specify the WPA passphrase?  I believe there's a drop-down menu titled 'advanced options' or something similar where you do that.  Unlike NetworkManager, wicd doesn't pop up a box asking for the key; you have to specify it before trying to connect.

---

### Post by rickzoll on 2009-04-07
I guess I was expecting something simple like "password missing" instead of "This network requires encryption to be enabled."  

Anyway, "validating authentication" is as far as I get now.  The interesting thing is that if I change the preferred device from ath0 to wlan0 to get to my built-in device, the connection is made.  I'm thinking that indicates my definition and passphrase are fine.  Any thoughts?
rickzoll

---

### Post by pytheas22 on 2009-04-07
It could just be that the driver doesn't support WPA properly right now.  It would be interesting to see if you can get connected under ath0 with security disabled on your router.  If that works, we can look into figuring out how to make the WPA play nicely.  Since this driver is so new and still under heavy development, it may not yet be in sync with Ubuntu's default wpa_supplicant framework (this is often the case with bleeding-edge wireless drivers, in my experience, but usually there's a way to make it work if you read the developer's instructions).

You might also have better luck if you recompiled the driver by running the commands in post #5 again.  If the code has been updated since then, it just might work with the latest version.  Back in December, when this thread was started, the driver didn't seem to work at all (it was unable to detect devices), so the fact that you're at least seeing an interface under it indicates that they're making progress.

---

### Post by rickzoll on 2009-04-10
Just got a chance to re-install and test without WPA security.  Unfortunately it still didn't connect. In fact after it did not connect, it then failed to show any wireless devices. I then changed back to the built-in device and it connected fine.

---

### Post by pytheas22 on 2009-04-11
If it didn't connect even with security disabled, I'm afraid the answer might be that it's just not going to work right now.  Your best option is probably to keep compiling the latest driver code every week or so, and hopefully it will allow your device actually to connect pretty soon.  If you do get it to work, please post here.

---

