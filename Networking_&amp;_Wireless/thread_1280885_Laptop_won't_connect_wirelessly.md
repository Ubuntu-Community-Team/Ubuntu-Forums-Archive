---
title: "Laptop won't connect wirelessly"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by dkolars on 2009-10-02
Greetings -- have desktop running Ub 9.04... connected to Comcast cable, no problem (other than Comcast speed, the usual!)... now, bought a new HP laptop with Atheros Communications AR242x 802.11abg Wireless PCI Express Adapter...   Installed Ubuntu 9.04 and all the updates.

CAN NOT make the wireless work!!  Running lshw tells me that the Network is UNCLAIMED.  Computer/internet works fine with RJ45 connected...
 
I have a Belkin G router, and have set the router to accept the addy of the laptop, but no go... I can find NO WHERE to tell it to try to connect?  Does that not exist in Linux?  I'm used to Windows (retired NT guy) and am still figuring out Linux...  Would be nice to attempt connection and see fail results!!

I've searched the web for about 4 days now looking for answers, and did find out that the network connection light on the HP laptop is ALWAYS amber... thanks, guys, that's really helpful!!  HP is a G60-445DX.

I did find and run "madwifi" to get the Linux drivers for the card, but that didn't help...

Also, under System, Admin, Network Tools, when I open that window I see 3 Network Devices:  Loopback (lo), Ethernet (eth0), & Unknown (pan0)... the Hardware address for the Ethernet is always the same, but the Unknown changes with every re-boot... what is this?  And why do I have it?

So, for now, the laptop languishes, awaiting connection.  Thanks in advance...

---

### Post by wilee-nilee on 2009-10-02
Since your not using the Comcast wireless router, you might talk with them, Comcast as far as I know doesn't care if you use another router.

---

### Post by Iowan on 2009-10-02
**pan0** is Personal Area Network (usually Bluetooth). I haven't yet developed a good understanding of the difference between Disabled, Unclaimed, and maybe another description for an interface that doesn't work.  You've already discovered **lshw** - try it as **lshw -C network** to limit results to network devices.  It *should* list a driver.  A forum search for your specific card *might* turn up some leads for drivers.
[Here]("http://ubuntuforums.org/showthread.php?p=6769417&highlight=AR242#post6769417") is one.
 [Another]("http://ubuntuforums.org/showthread.php?t=854059") (somewhat dated) one.
Hope [this]("http://ubuntuforums.org/showthread.php?p=7168287&highlight=AR242#post7168287") one isn't a duplicate.

---

### Post by dkolars on 2009-10-03
Well, here's what I get when I run lshw -C network:

[I]dkolars@laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: xx:1f:xx:xx:5c:xx
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: xx:aa:xx:2b:xx:39
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/I]


Shouldn't the NIC have a serial?  NO drivers listed...  If I run this with the RJ45 connected, I get the IP address listed in the GeForce description.  

If I go to Sys, Admin, Hardware drivers, I can de-activate the madwifi driver, but it says that it's been de-activated, but is still in use.  What's up with that?  How do I turn it off?

---

### Post by Iowan on 2009-10-04
Looks like a driver problem (as opposed to a router issue). I haven't had need to try madwifi or ndiswrapper... yet. Hopefully, one of the AR242x links will help.

---

### Post by Jackp90 on 2009-12-05
I have the same laptop.  The wireless works great with Ubuntu 9.10, so if that is an option for you, you could try that.  

I personally prefer Ubuntu 9.04 over Ubuntu 9.10 at this point because I like the old GDM better.  Here is how I got my wireless working: 

After upgrading to the 2.6.28-16-generic Linux kernel my wireless was still not working so after some reading I tried:

```
sudo apt-get install network-manager-gnome network-manager-openvpn network-manager-pptp network-manager-vpnc

```

Restart you computer and now your wireless should work.

I am not sure why this works my hypothesis is that it upgrades everything to the newest version because I believe that these packages are already installed by default (I know that the first one is).  I lost the link when I restarted my computer so I honestly don't know why it works but it does.

I hope that this is of some use to you.

---

### Post by dkolars on 2009-12-06
Thanks for the response...  I solved this by doing the upgrade to 9.10... works fine... now to figure out how to mark this [solved]!!

---

### Post by acho on 2009-12-06
> **Jackp90 said:**
> I have the same laptop.  The wireless works great with Ubuntu 9.10, so if that is an option for you, you could try that.  

I personally prefer Ubuntu 9.04 over Ubuntu 9.10 at this point because I like the old GDM better.  Here is how I got my wireless working: 

After upgrading to the 2.6.28-16-generic Linux kernel my wireless was still not working so after some reading I tried:

```
sudo apt-get install network-manager-gnome network-manager-openvpn network-manager-pptp network-manager-vpnc

```

Restart you computer and now your wireless should work.

I am not sure why this works my hypothesis is that it upgrades everything to the newest version because I believe that these packages are already installed by default (I know that the first one is).  I lost the link when I restarted my computer so I honestly don't know why it works but it does.

I hope that this is of some use to you.

Nice job team.... my Jaunty have same problem.:KS

---

### Post by aciconte on 2010-02-01
Im having the same problem but ive tried the madwifi and some other stuff nothing is working for me for my wifi.......

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:e2:55:90
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.0.174 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c2000000-c200ffff

help?

---

### Post by Jackp90 on 2010-02-01
[QUOTE=aciconte]hi, I was just going through the fourm because im having a problem with my G60 445DX  with the wireless..... I've done what you said, i've tried madwifi and some other stuff and nothing seems to work.... ive posted the info with the wireless on the fourm page

[http://ubuntuforums.org/showthread.php?p=8758138#post8758138](http://ubuntuforums.org/showthread.php?p=8758138#post8758138)

think you could help me out?[/QUOTE]

I couldn't get the madwifi drivers working for me either I suggest that you disable them if they are not working.

Before you tried installing the packages did you update your sources?  If not try 

```
sudo apt-get update
```

then run 

```
sudo apt-get install network-manager-gnome network-manager-openvpn network-manager-pptp network-manager-vpnc
```

What version of Ubuntu are you using?  I assume that you are using Ubuntu 9.04 but I am unclear about this also is it a new install or did it stop working after an upgrade?

---

### Post by aciconte on 2010-02-02
Im Running Karmic 9.10 and no i just ran the updatemanager.

---

### Post by aciconte on 2010-02-02
oh it just didnt work from the begining.
i downloaded the file from online burned it. then i used update manager and activated my graphics card. restarted and no luck ive been trying to use everything possible but if this doesnt work ill try it from scratch and see if it works if that will be needed.

---

### Post by Jackp90 on 2010-02-04
> ok i just installed the Ubuntu 9.10 Netbook Remix and everything works perfectly!

No updates needed it just worked right off the bat!

If anyone is having problems recomend this to them.
I know I am haha.

But thanks for all the help. Didn't think anyone was going to reply.

Its odd that it worked in the netbook remix but not the normal Ubuntu 9.10 Well glad you got it to work.

---

