---
title: "Wired connection suddenly stopped working (a problem with NetworkManager?)"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by m4443 on 2010-04-11
So, the problem is simple, my computer's wired connection stopped working after just normal shutdown - that's pretty much everything I can say about this problem, I don't remember changing any settings/files or updating packages that may have caused this problem.

Anyways, my network card is Atheros AR8121 which uses ATL1E.ko module as it's driver. I'm using Karmic.
EDIT: Dunno, but it may affect on some things; I'm using realtime-kernel.

Here's some logs/files and outputs of commands:

/etc/network/interfaces:
```
auto lo
iface lo inet loopback
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:22:15:57:2b:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

lshw (network part):

```
*-network
                description: Ethernet interface
                product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: 00:22:15:57:2b:2c
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 multicast=yes
                resources: irq:28 memory:fe9c0000-fe9fffff ioport:dc00(size=128)
```

ethtool eth0:
```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x00000000 (0)
	Link detected: no
```

nm-tool:
```
NetworkManager Tool

State: disconnected


** (process:3925): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        00:22:15:57:2B:2C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```

/etc/NetworkManager/nm-system-settings.conf:
```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

And finally /var/log/daemon.log (NetworkManager parts):
```
Apr 11 14:21:39 jp-desktop NetworkManager: <info>  starting...
Apr 11 14:21:39 jp-desktop NetworkManager: <info>  Trying to start the modem-manager...
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0, iface: eth0)
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Apr 11 14:21:40 jp-desktop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 11 14:21:40 jp-desktop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  Wireless now enabled by radio killswitch
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: (149383920) ... get_connections.
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: (149383920) ... get_connections (managed=false): return empty list.
Apr 11 14:21:40 jp-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  (eth0): carrier is OFF
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'ATL1E')
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  (eth0): now managed
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  (eth0): bringing up device.
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  (eth0): preparing device.
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 11 14:21:40 jp-desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  modem-manager is now available
Apr 11 14:21:40 jp-desktop NetworkManager: <info>  Trying to start the supplicant...
Apr 11 14:22:14 jp-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Apr 11 14:22:14 jp-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Apr 11 14:22:14 jp-desktop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
```

Hope those will help :)

---

### Post by m4443 on 2010-04-12
Bump.

What I've understood, the reason why my wired connection doesn't work is because NM deactivates my Ethernet controller, as you can see from the daemon.log. But what I don't know is *why* NM deactivates it. What is the "reason 2"? I really want to get this working again :(

```
<info>  (eth0): deactivating device (reason: 2).
```

---

### Post by nitstorm on 2010-04-12
[http://bbs.archlinux.org/viewtopic.php?id=69987](http://bbs.archlinux.org/viewtopic.php?id=69987)

I think other people have had this problem too. Check that link out, says its an upstream bug or something...

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205)

Also a bug report has been filed looks like it....

---

### Post by m4443 on 2010-04-12
> **nitstorm said:**
> [http://bbs.archlinux.org/viewtopic.php?id=69987](http://bbs.archlinux.org/viewtopic.php?id=69987)

I think other people have had this problem too. Check that link out, says its an upstream bug or something...

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205)

Also a bug report has been filed looks like it....

I believe that the cause of my problem is different than in those that are in the links, although the pasted logs in those have the same message (deactivating device). Since in the first link they are talking about wireless connection and how killswitch is thought (by NM) to be on. My connection is wired one and thus killswitch *should* not affect on it.

And the second one is about problems with Point-to-Point connections, I suppose.

So far I've tried to change "managed=false" to true in nm-system-settings.conf and adding "auto eth0" and "iface eth0 inet dhcp" to interfaces file (both tried at the same time and separately). Neither helped.

The meaning of "reason 2" still remains unknown - these are the moments when I wish OSS projects were better documented.

EDIT: If there isn't any "NM gurus" here, someone may know how to totally reset **all** of my network configurations? My installation has gone through quite a many version updates, so it wouldn't be a surprise if my configurations are a bit messed up..?

---

### Post by 2hot6ft2 on 2010-04-12
To find out if it's network manager or not you could go to
System > Preferences > Startup Applications
and disable (uncheck) Network Manager
click close then open it again and repeat until it stays unchecked (beats me as to why but once rarely does it) then

Open a terminal
Applications > Accessories > Terminal
and run
```
gksu gedit /etc/network/interfaces
```
add 2 lines so it looks like this
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
save and close
shut down connect to a wired connection and boot up

If it doesn't connect then it's not network manager so remove the 2 lines from the interfaces file and re-enable network manager in
System > Preferences > Startup Applications

If it connects then the problem is network manager
So run
```
sudo apt-get purge network-manager-gnome
```
When it finishes close everything and reboot

Then run
```
sudo apt-get install network-manager-gnome
```
Then run
```
gksu gedit /etc/network/interfaces
```
remove the 2 lines so it looks like this
> auto lo
iface lo inet loopback
save and close
and re-enable network manager in
System > Preferences > Startup Applications
reboot

All your settings should have been purged.

---

### Post by m4443 on 2010-04-14
I changed settings so that NM will not start on boot, and... still not working :(

So the cause of this isn't NM.., any suggestions what to try next? I tried to boot with generic kernel and not so surprisingly, it didn't make any difference. Also checked bios settings - they were OK.

My PC doesn't appear as connected in my ADSL modem - in other words seems that the ethernet controller isn't on. This is also how it was in 8.04 which didn't have ATL1E module (and which I later had to compile by myself). I can't say if this is about the driver, because at least in the logs NM reported that it found a driver and etc..

---

### Post by =not4prophet= on 2010-04-14
are you sure it's a software problem?  It could be that a power surge damaged the NIC while your PC was turned off.

---

### Post by m4443 on 2010-04-14
Of course I can't be sure if it's or is not a software problem, but mainly it seems to be (I think), since the device is listed in lspci and from logs it seems that NM actually interacts with it.. 

And atm I don't have a chance to test it out, though.. (the installation CDs I have does not include ATL1E driver, so they are useless for this - and I don't want to download another 700 mb just for this with my slow connection o.O)

---

### Post by m4443 on 2010-04-15
Actually I did test it, I just remembered that I have external PCI network card. So I installed it into my PC and tried if it could connect with that.

But well well, didn't work any better than with the onboard card. NM logs just same things ("deactivating device"), though now from both cards..

So what we know now is:
1. It's a software problem
2. Not caused by NetworkManager
3. Ethernet controller(s) appears to be literally shutdown (no power, or something)

Argh, I don't want to reinstall my Ubuntu - but at the moment it seems that pretty much I have to... :(

---

### Post by 2hot6ft2 on 2010-04-15
> **m4443 said:**
> 
```
Apr 11 14:21:39 jp-desktop NetworkManager: <info>  starting...
Apr 11 14:21:39 jp-desktop NetworkManager: <info>  Trying to start the modem-manager...
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: init!
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/eth0, iface: eth0)
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: device 
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: end _init.
Apr 11 14:21:40 jp-desktop NetworkManager: Loaded plugin ifupdown: (C) Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: (149383920) ... get_connections.
Apr 11 14:21:40 jp-desktop NetworkManager:    SCPlugin-Ifupdown: (149383920) ... get_connections (managed=false): return empty list.
Apr 11 14:21:40 jp-desktop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Apr 11 14:22:14 jp-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Apr 11 14:22:14 jp-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.

I see a lot of ifupdown there.
If you right click on NM and select Edit connections does wired have ifupdown listed?
If it does then

How to remove ifupdown(eth0)??
http://ubuntuforums.org/showthread.php?t=1316705

> **peepingtom said:**
> NetworkManager is the best way for end-users to configure their network I think these problems are happening with people who configured their networks using the command line using some cut-and-paste fiddling with pppoeconf or stuff in /etc. 

To have NetworkManager manage all interfaces without editing ifupdown/interfaces files, this should work.

Check /etc/network/interfaces.

Press alt+F2 and paste in:
[CODE]gksudo gedit /etc/network/interfaces
```

Remove everything but 
```
auto lo
iface lo inet loopback

```

Then Check /etc/NetworkManager/nm-system-settings.conf 
Press alt+F2 and paste in:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

set 

```
 [ifupdown]
managed=false 
```

Restart computer or NetworkManager service.
From now on, only configure the network using the NetworkManager applet in the notification area (aka system tray).

For more info See: [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)


---

### Post by m4443 on 2010-04-16
> **2hot6ft2 said:**
> ...

ifupdown is not listed in the connections and my configuration files are just like in that howto.. Still I can see ifupdown in the log. But maybe those messages may also come because the plugin is loaded, I mean it's not in use but when it loads it prints those messages...?

---

### Post by m4443 on 2010-04-16
I'm not sure but I probably found something interesting from syslog

```
Apr 16 19:13:49 jp-desktop kernel: [   14.011970] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

Googled with that and got somewhat similar problems, still not sure. At least with that fast googling I didn't find any kind of 'common fix', though..

---

### Post by 2hot6ft2 on 2010-04-16
I don't know, it seems to be a problem for a few people.
Might take a look at this thread starting at post #8 may provide some help
[http://ubuntuforums.org/showthread.php?t=1206649](http://ubuntuforums.org/showthread.php?t=1206649)

If it sounds like your issue jump to post #16 same thread.

---

### Post by m4443 on 2010-04-16
Oh god. -.-

Now I feel kinda stupid.. and, lol. 

So the cause is.. that "something" has corrupted my ethernet cable. :confused:

But this was kind of reason I expected the least.. Since I thought that it was just normal behavior when it didn't appear on my ADSL box.., I mean because it had behaved that way before when the ATL1E driver wasn't loaded and when the cable was still okay.

But everything is now okay, just new cable then.. - solved :)

---

### Post by 2hot6ft2 on 2010-04-16
> **m4443 said:**
> 
But everything is now okay, just new cable then.. - solved :)
Too funny, it's usually the simplest things that get us.
:guitar:

---

