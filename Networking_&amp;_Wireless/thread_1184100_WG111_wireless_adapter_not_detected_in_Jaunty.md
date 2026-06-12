---
title: "WG111 wireless adapter not detected in Jaunty"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by luuke on 2009-06-10
Hi all,
I'm using 9.04 jaunty on my laptop now and I am trying to get my netgear WG111 (version 1 I believe) wireless adapter working.

 When I first plugged it in, it was detected and worked perfectly.  Since then I have experimented (only on my own network, of course) with the aircrack-ng suite, and now the WG111 is no longer detected.  The little blue light on the adapter does not come on anymore and the card no longer shows in ifconfig or iwconfig.

I wouldn't be so surprised if the card was not detected in the first place, but the fact that it WAS working and now doesn't, has be boggled. :S

Any help would be greatly appreciated!

---

### Post by superprash2003 on 2009-06-11
post output of **lshw -C network** , try uninstalling aircrack..

---

### Post by MaindotC on 2009-06-11
Aircrack probably put the card in Monitor mode.

---

### Post by luuke on 2009-06-11
[LIST]
[*]lshw -C network returns details of my other network cards, but nothing about the wg111.
[*]uninstalling aircrack does not change anything.
[/LIST]

I'm not worried about this for personal use because I use my inbuilt wireless card anyway, but i'm sure there are others having similar issues...

---

### Post by superprash2003 on 2009-06-12
posting the output of that command will surely help

---

### Post by luuke on 2009-06-12
No problems, here it is! 
Thanks for the help =) :

luke@ubuntu:~$ sudo lshw -C network
[sudo] password for luke: 
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:df:2a:f2
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:5b:14:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.23 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ae:12:53:68:cb:65
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
luke@ubuntu:~$

---

### Post by MaindotC on 2009-06-13
WG111 is a USB adapter right?  Post the output of:
```

lsusb

```
Also per [this thread](http://ubuntuforums.org/showpost.php?p=1027896&postcount=3) try and find out what version number and chipset your device is using.

---

### Post by luuke on 2009-06-13
Sure, here it is!

root@ubuntu:/home/luke# lsusb
Bus 002 Device 002: ID 0c45:63fc Microdia 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 007: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 006: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 005: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@ubuntu:/home/luke#

---

### Post by MaindotC on 2009-06-14
I'm assuming this:
```

Bus 003 Device 004: ID 0a5c:4500 Broadcom Corp. 

```
is the WG111 and it is using a Broadcom chipset.  That being the case, try installing the bcm43xx or zd1211rw drivers.  I use the zd1211rw for my Belkin USB (in my signature) which has a broadcom chipset.

---

### Post by luuke on 2009-06-14
Hmmm ok, update:

I tried installing the zd1211rw drivers, I downloaded them from sourceforge, extracted the tarball, and did as it said in th readme which was to copy come files.  There was no luck with that, so I decided to try the bcm43xx drivers.

I followed the guide here: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/howto-bcm43xx-broadcom-drivers-462995/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/howto-bcm43xx-broadcom-drivers-462995/)

It seems a bit weird that you are putting bcm43xx on the blacklist, though?!

Anyway long story short, it's still not detected.  I can't understand why it WAS working flawlessly, and then it just stopped?!

---

### Post by MaindotC on 2009-06-16
Can you check iwconfig to see if the adapter is set in Monitor mode?

---

### Post by MaindotC on 2009-06-16
The OP on [this thread](http://ubuntuforums.org/showthread.php?t=1188651) is showing a similar card but his machine is telling to use the RTL8187B driver instead.  Check [his thread](http://ubuntuforums.org/showthread.php?t=1188651) and see if your machine is improperly detecting the chipset.

---

### Post by mark9950 on 2009-07-06
Im new to linux ubuntu,how do I do all this?

---

### Post by MaindotC on 2009-07-06
First try using the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  You will probably have questions, and that will lead to reading more documentation and man pages and googling but I assure you - get it done now and it will save you boatloads of time in the future.

---

### Post by mark9950 on 2009-07-06
Thanks but Im not going through all this crap,Im going back to windows,at least The drivers are handy and everthing works.

---

### Post by alone9394 on 2009-07-21
wish me good luck...because newegg is doing a sale on the wg111 right now...and i ordered two of them...by doing my research on this on driver for ubuntu 9.04...i think the ndiswrapper will work...let's hope i am right...one more thing...i was a user of windows for since the windows 95/dos age...been with 98, 98se, me, 2000work/server, xp, 2003server, vista, and 2008server...i like them all but now i am with ubuntu for a good long month and i like it more than windows...i like the fact that linux is structure like dos/win95...dos as the base and build win95 on top of it...i was able to setup multi win95 on just one dos...using a simple batch script "autoexec.bat"...long store short...dos=kernel...win95=gnome/kde...kernel just a lot more stable and a lot more functional then dos...further more...gnome is more fun the win/gui...even for win7...you got a fan, linux...

---

