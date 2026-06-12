---
title: "Gigabit NIC changes to 100 MB"
date: 2012-08-31
forum: Networking &amp; Wireless
---

### Post by revtds on 2012-08-31
Running an AMD PhenomII, 4X, 3.4GHz, 16Gig RAM, 11.04 Ubuntu because 12.o4 dropped Evolution, and wouldn't sync with Palm anymore, 2.6.38.15g Kernel, and an RTL 8111 onboard Gigabit NIC.

After install, the machine ran for 2 months very, very well, with a Gigabit eth0.  Yesterday, I had not rebooted for quite some time, and after a series of updates which included a kernel update, I restarted to complete the updates, and I now have a 100MB NIC, instead of a Gigabit NIC.

I do not even know where to start troubleshooting this.

I have powered down, unplugged for 20 minutes, and powered up, no joy.

I disabled eth2 which it switched to when it changed from Gigabit, and rebooted, and got eth0 back, but still 100MB. It is now back to an "eth2" for some reason.

Partial output of "lspci"
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

"ifconfig" yields
tom@tom-desktop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr f4:6d:04:95:df:28  
          inet addr:192.168.2.113  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fe95:df28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1066334 (1.0 MB)  TX bytes:169668 (169.6 KB)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3888 (3.8 KB)  TX bytes:3888 (3.8 KB)
 The other systems on the network are getting Gigabit connections, but mine doesn't.

Where do I begin?

---

### Post by revtds on 2012-09-01
Bump. Anyone out there?

---

### Post by TheFu on 2012-09-01
Ok, seems the OS knows what card you have. That's good.
Does it load the driver?
 * Is there a module with "r816*" loaded?

Is the driver used?

Is the correct device being used by the OS?  
* ifconfig -a

Are the settings for the driver correct for each device?
* sudo ethtool eth0
 * sudo ethtool eth1
* sudo ethtool eth2
* sudo ethtool eth3
* sudo ethtool eth4 
 and so on for every ethernet device in the ifconfig output.

Could the switch/router port be failing?  Try a different port / switch.
Could the cable have a crimp or nick?  Did a mouse (rodent) eat into it?
Did you use the cheapest possible CAT5e cable? Are the connections good?

---

### Post by revtds on 2012-09-01
I have no idea how to check for a loaded module "r816", but here is the output of ethtool eth2:

tom@tom-desktop:~$ sudo ethtool eth2
Settings for eth2:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
**********************************
If I use the command "sudo ethtool -s eth2 speed 1000" and then follow it with "ethtool eth2, it tells me it set the speed to 10 Mb.

---

### Post by TheFu on 2012-09-01
> **revtds said:**
> I have no idea how to check for a loaded module "r816", but here is the output of ethtool eth2:

tom@tom-desktop:~$ sudo ethtool eth2
Settings for eth2:
                            1000baseT/Half 1000baseT/Full 
    Link detected: yes
**********************************
If I use the command "sudo ethtool -s eth2 speed 1000" and then follow it with "ethtool eth2, it tells me it set the speed to 10 Mb.

Those 2 lines say that the OS knows what the card can do and that the cable isn't completely unusable.  I'm guessing it is the router, switch, or cables that are the issue.
Any thought on those other questions?

---

### Post by NadirPoint on 2012-09-01
Looks like link partner, which would be:
> **TheFu said:**
> I'm guessing it is the router, switch, ...
...advertised 100Mb full max. possible speed.

---

### Post by revtds on 2012-09-03
OK, I am not following what you are saying, but here is some more info.

Router is in my house. A moderately good quality CAT5e cable feeds a hub in my church office, with three other computers on it, besides mine.  Everybody in the house is wireless except my wife, who is wired and getting 1Gb.

The other three computers in the office are getting 1Gb connections. Mine is the only one reporting 100Mb.  Due to this I (possibly) eliminate switches, routers and most cables.

I have plugged in a new CAT5e from the router to my computer and it still gets 100Mb.

Shouldn't I be able to tell the card to run at 1Gb with ethtool?  Why would it switch to 10Mb when I try to modify it, and then switch back on its own to 100 Mb?

How would I go about uninstalling this driver and re-installing it?

---

### Post by TheFu on 2012-09-03
> **revtds said:**
> OK, I am not following what you are saying, but here is some more info.

Shouldn't I be able to tell the card to run at 1Gb with ethtool?  Why would it switch to 10Mb when I try to modify it, and then switch back on its own to 100 Mb?

How would I go about uninstalling this driver and re-installing it?

rmmod and insmod and lsmod are the commands but that isn't likely to be the issue. If you've rebooted, then you've already tested that. 

**Sorry, there is no magic fix for you.**

You have bad hardware somewhere. Start swapping 1 part at a time.
* switch ports
* cables
* NIC
* interference from other electric stuff - are there power cables near the ethernet cable?  Running coax and ethernet near each other over a few feet is reported to have caused issues too.
* Sun spots - Total Recall says that can be an issue. ;)

If none of that works, perhaps the cable is too long or you've found a bug.
Since ethtool sees that your card is capable of GigE, it is unlikely you have the wrong driver.  Did you verify that the driver and chips in the NIC match?

Look at the log files - dmesg and syslog especially.  Some routers and switches will tell you where the cable break is. Does yours?  I think this only works when the cable is completely faulty, not when it just drops to a lower speed.

If you aren't on a laptop .... a good quality Intel PRO/1000 card is only $25, so those are easy to swap in test. I've been burned by cheaper NICs, so I don't bother anymore to save $10.  The PRO/1000 **is** the standard and is extremely well supported across all platforms.  I'm a little network crazy, so having an extra PRO/1000 around has never been wasted for long. ;)

---

### Post by revtds on 2012-09-04
The more I work with it, it appears to be the hub, a Netgear Gigabit 5port hub.

It also acts like the cable, as the connection is not 100% stable and repeatable, but I moved the cable to another port on the hub (1 currently unused) and with the original cable I am now getting 1Gb, in Windows and Ubuntu.  The new cable also does 1GB, but both of them gave me only 100Mb once each.  I did not reboot, just let the NIC reconnect.

For now solved as a Hub hardware issue.

Thanks for the input and assistance.

---

