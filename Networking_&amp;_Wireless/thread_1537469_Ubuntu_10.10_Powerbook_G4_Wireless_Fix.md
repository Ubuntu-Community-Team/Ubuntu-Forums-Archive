---
title: "Ubuntu 10.10 Powerbook G4 Wireless Fix"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by bemental on 2010-07-23
Hello all.

For any of you who are interested in installing Ubuntu 10.10 Maverick Meerkat ([http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)) onto your old and dusty Powerbook G4 (21") and are frustrated with the wireless networking issues, please find these instructions below helpful.  If you're curious why I chose 10.10 its because I wanted the most up to date software running on my crap, old hardware.

Also, would someone more experienced from the community then myself like to evaluate these instructions (taken from YDL.net - [http://www.yellowdoglinux.com/support/solutions/ydl_6.x/airport-extreme.shtml](http://www.yellowdoglinux.com/support/solutions/ydl_6.x/airport-extreme.shtml)) and vet them for us?

Granted, they work (wireless kicks off and reconnects from time to time) but I feel like I have both Gnome's networkmanager running and wicd (although I have quit wicd after booting into the desktop and Gnome's NWM works fine)

Thanks in advance and keep up the great support everyone!

Andrew

----------

Again, these instructions can be found HERE ([http://www.yellowdoglinux.com/support/solutions/ydl_6.x/airport-extreme.shtml](http://www.yellowdoglinux.com/support/solutions/ydl_6.x/airport-extreme.shtml)) via YDL.net and involve a bit of command line work, but nothing anyone here should be scared of.  In addition, ignore the steps specific to YDL only (obviously).

OPIC: Enabling Airport Extreme 


Introduction
This HOWTO will guide you through the steps of setting up Airport Extreme with YDL v6.x for Apple hardware. It was tested on an Apple PowerBook G4 1.67GHz running a fresh install of YDL v6.1. 

This procedure requires 3 steps:
Discover your Airport firmware version.
Extract the Airport Extreme firmware.
Configure your wireless card under Linux.

Discover your Airport Extreme version
Broadcom is the manufacturer of the Airport Extreme wireless chip for Apple. The Broadcom chip in the Powerbook used to write this HOWTO is the BCM4306 802.11b/g (rev 03). Different versions of the firmware and driver might not be as straightforward. To discover the version of the Airport you have on your computer, under Linux run this command as root:
[root@localhost network-scripts]# lspci | grep -i broadcom [ENTER]

Here's the output I get on my laptop:
	0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g

	Wireless LAN Controller (rev 03)
	
If you have an earlier or later version, these instructions may or may not work for you. If you run into troubles, join the yellowdog-general mailing list or visit us on #yellowdog at freenode.irc.net. Someone there might be able to help you troubleshoot any problems you might have. 


Extract the Airport Extreme firmware
The first step in getting your Airport Extreme working is to extract the necessary firmware files from your MacOS X drivers.
Note that these instructions were written for YDL v.6.1. Other versions of YDL may require different versions of fwcutter and the firmware.
Change to user root:
su -
Download, extract and build b43-fwcutter software version 011, which will be used to extract the Broadcom drivers:
wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2) [ENTER]
tar xjf b43-fwcutter-011.tar.bz2 [ENTER]
cd b43-fwcutter-011 [ENTER]
make [ENTER]
The make command above should generate output similar to the following:
   cc -O2 -fomit-frame-pointer -std=c99 -Wall -pedantic -D_BSD_\
SOURCE-DFWCUTTER_VERSION_=006   -c -o fwcutter.o fwcutter.c
   cc -O2 -fomit-frame-pointer -std=c99 -Wall -pedantic -D_BSD_\
SOURCE-DFWCUTTER_VERSION_=006   -c -o md5.o md5.c
   cc -O2 -fomit-frame-pointer -std=c99 -Wall -pedantic -D_BSD_\
SOURCE-DFWCUTTER_VERSION_=006 -o bcm43xx-fwcutter fwcutter.o md5.o
... and you should be left with a binary executeable called b43-fwcutter. 

Type:
cd .. [ENTER]
Download and use fwcutter software to extract the Broadcom proprietary driver:
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) [ENTER]
tar xjf broadcom-wl-4.150.10.5.tar.bz2 [ENTER]
b43-fwcutter-011/b43-fwcutter -w "/lib/firmware" broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o [ENTER]
The b43 within the /lib/firmware directory should contain files:
	[root@localhost ~]$ ll /lib/firmware/ [ENTER]
	a0g0bsinitvals4.fw
	a0g0bsinitvals5.fw
	a0g0bsinitvals9.fw
	a0g0initvals4.fw
	a0g0initvals5.fw
	a0g0initvals9.fw
	a0g1bsinitvals13.fw
	a0g1bsinitvals5.fw
	a0g1bsinitvals9.fw
	(more ...)
	

If wicd cannot find any local wireless networks, even after pressing "Refresh" once or twice, you may need to change the permissions on the b43 directory:
chmod 755 b43

Configure your wireless card under Linux using wicd.
Refer to Using Wicd Network Manager 

You are on-line!
This HOWTO was written by Christopher Murtagh and Bonnie Gosler, Fixstars.

---

### Post by bemental on 2010-07-23
Ugg.  Everyone once and awhile the Powerbook will connect to the internet and STAY connected, but now it hops on and off on and off on and off (etc) INCESSANTLY.

-----

I have manually removed Gnome's Network-manager via apt (sudo apt-get remove network-manager) and it seems to have stopped.  Sometimes Wicd has trouble logging onto my WAP2 network but after a few tries we manage to get on.  

Now onto fixing flash on a PPC...

---

### Post by Sakrecoer on 2011-02-05
thank you! i will try it straight away! :)

---

### Post by Sakrecoer on 2011-02-05
unfortunatley, Wicd Network Manager is not preinstalled, which makes this procedure fail when there is no other alternatives to connect to internet.
But thank you anyway!
Still looking for my sollution....

---

### Post by 1984dc on 2011-04-12
I tried to do this but i get the error message  [COLOR=Red]"HTTP request sent, awaiting response... 404 Not Found 2011-04-12 21:18:23 ERROR 404: Not Found."[/COLOR] when i run:

```

wget [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2]("http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2")
```I did try to install this on YDL before I un-installed YDL (as i didn't like it), but i can't seem to get this working on ubuntu. Any suggestions or workarounds would be great as i curently have about 10 feet of tele cable across my house!

Many Thanks in advance.

Dc

---

### Post by 1984dc on 2011-04-12
Scratch hat I didn't realise that you had to click he link and copy it's location that way. Whoops.

Many thanks

Dc

---

### Post by 1984dc on 2011-04-12
Okay so I got the wireless working.

I had to use network-manager instead of wicd as wicd wouldn't accept my password and network manager picked up the WLAN signals (they are now running side by side without any problems).

---

### Post by Jumponskis1 on 2011-09-04
I could really use some help with this exact same setup. Installed maverick on my powerbook g4 and had the same problem, tried these steps but was met with many error messages. anyone with time to coach me through this i beseech you! Been a while since i touched an ubuntu system but am not exactly a novice. any help is appreciated:lolflag:

---

### Post by nm_geo on 2011-09-04
> **Jumponskis1 said:**
> I could really use some help with this exact same setup. Installed maverick on my powerbook g4 and had the same problem, tried these steps but was met with many error messages. anyone with time to coach me through this i beseech you! Been a while since i touched an ubuntu system but am not exactly a novice. any help is appreciated:lolflag:

I assume you are trying to get the Broadcom b4306 wireless working?
Do you have ethernet connection?

Let's see what we are dealing with from terminal:

```
lspci -nn | grep 0280
``````

sudo lshw -C network
```Paste result

---

### Post by Jumponskis1 on 2011-09-05
```
0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
``````
 *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@0001:10:12.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=16
       resources: irq:52 memory:a0006000-a0007fff
  *-network
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:24:0f.0
       logical name: eth0
       version: 80
       serial: 00:0d:93:4a:96:9c
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=half latency=16 link=no maxlatency=64 mingnt=64 multicast=yes port=MII speed=10MB/s
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0d:93:85:0f:18
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-30-powerpc firmware=N/A ip=10.0.1.14 link=yes multicast=yes wireless=IEEE 802.11bg
```

edit: it seems the solution was so easy that this thread was actually making it more difficult for my situation than it needed to be. I simply went to System>Administration>Additional Drivers and activated Broadcom B43 wireless driver. I then noticed that the "firmware missing" disappeared and i could pick up wireless signals once again! Much to my dismay when I tried to connect to my router it would not connect so i tried removing wicd and now it is running smoothly, for the time being anyways. Thank you for your swift response.

---

### Post by nm_geo on 2011-09-05
**> Do you have ethernet connection?**If you have ethernet connection..

```
sudo apt-get update && sudo apt-get upgrade

```Then you need 

```
sudo apt-get install b43-fwcutter

``````
sudo apt-get install firmware-b43-installer

```

---

### Post by nm_geo on 2011-09-05
From your edit I see you got it going good...
Have fun and be sure to do those 

```
sudo apt-get update && sudo apt-get upgrade
```

---

