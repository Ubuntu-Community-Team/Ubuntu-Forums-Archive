---
title: "Any ideas for getting the wired connection to work with 2Wire 3800HGV DSL Modem?"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by christopherbalz on 2010-01-17
Wireless works fine on Ubuntu, but not the wired connection. Wired connection works fine on my Mac OS X 10.4.  This is using AT&T U-verse 18mbps connection.

This post ([https://answers.launchpad.net/ubuntu/+question/56342](https://answers.launchpad.net/ubuntu/+question/56342)) indicates the issue is due to lack of the appropriate driver on Ubuntu for this dsl modem. Is there any workaround that does not involve adding a PCI Ethernet card?

Technical details below.  Thanks in advance!

Running Ubuntu 9.10

//cbalz-tp-r51-0/.../~ $ uname -a
Linux cbalz-tp-r51-0 2.6.31-17-386 #54-Ubuntu SMP Thu Dec 10 18:27:05 UTC 2009 i686 GNU/Linux

//cbalz-tp-r51-0/.../~ $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


#iface eth1 inet dhcp

//cbalz-tp-r51-0/.../~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:60:cf:57:a2  
          inet6 addr: fe80::20d:60ff:fecf:57a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:75021 (75.0 KB)  TX bytes:12393 (12.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:0e:35:36:78:0a  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe36:780a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2948 errors:6 dropped:6 overruns:0 frame:0
          TX packets:2828 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2490182 (2.4 MB)  TX bytes:441161 (441.1 KB)
          Interrupt:11 Base address:0xe000 Memory:c0214000-c0214fff 

irda0     Link encap:IrLAP  HWaddr fa:cd:59:6b  
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:98548 (98.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11372 (11.3 KB)  TX bytes:11372 (11.3 KB)

virbr0    Link encap:Ethernet  HWaddr ce:d5:4b:4f:1e:5b  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:4130 (4.1 KB)

//cbalz-tp-r51-0/.../~ $

---

### Post by christopherbalz on 2010-03-10
I found that while there is a wireless issue with this modem, the ethernet on my machine was not working.  

The wireless problem with this modem was that, at least with my ubuntu machine, it would drop the connection repeatedly.  

Fixed that by using a new wired+wireless dlink router as my wireless link (it gets the connection via ethernet from the 2wire modem).

Realized that the ethernet on my machine (ThinPad R51 running Ubuntu 9.10 up-to-date

[INDENT]//cbalz-tp-r51-0/.../~ $ uname -a
Linux cbalz-tp-r51-0 2.6.31-20-386 #57-Ubuntu SMP Mon Feb 8 11:42:49 UTC 2010 i686 GNU/Linux
[/INDENT]

does not work when I tried to configure the new dlink router and my ubuntu box could not even reach the router on its subnet i.p.  (I configured it instead on a Mac).

With previous updates and versions of Ubuntu, the ethernet always worked fine on my box.  

So now there are two issues: Wireless flaky on the 2wire modem (but I'm freed from that myself now with the dlink router), and ethernet not working.

---

### Post by roman2440 on 2010-03-11
Wireless dropping is typically caused by 1 of 2 issues:  Wireless signal strength or Encryption issues.

For Wireless signal strength, the easiest way to identify it as the root would be to look at how good the connection is when it is working.  If strength is full when it is working and then just drops, its not likely due to signal strength, however if the strength is only 1/2 or 1/3 when it is working, then that signal strength can cause random drops in connectivity.

To resolve signal strength issues look at the following items:
1) Wireless configuration - check the GUI on the gateway for wireless power and channel settings.  Power should be set as high as possible, and channel should be changed to a different one.  This will most likely fix your wireless issues.

2) Distance - What is the distance between the wireless adapter and the gateway?  How many walls are involved and of what materials?  Likely this is not an issue in your case as you have another wireless access point that works in the same location.

The other potential issue, Encryption issues, is related to how different adapters and drivers handle different types of wireless encryption in different environments.  By default the 2Wire gateway uses WPA for wireless encryption.   What kind of encryption settings are you using on the dlink, likely it is not the same as the 2Wire?  

As far as the 2Wire goes, I'd recommend (if the signal strength troubleshooting doesn't fix the issue) changing the encryption key to a custom key.  If it still fails, try changing it to WEP instead of WPA.  A final test can be run to rule out encryption issues and that is to try the connection with encryption completely turned off (Note, do not leave your gateway in this state, use it only for a very short amount of time for testing and then turn security back on - without encryption turned on you are exposing your data to anyone within wireless range).

---

### Post by christopherbalz on 2010-03-19
<solved> Apparently some or all new ethernet connections currently require a new connection profile.  Fixed by plugging in the ethernet cable and setting up a new wired connection (Edit Connections -> Wired tab -> Add) and connecting with that one (Available Networks (click on connection icon) -> <new wired network>).  

Previously, I never had to configure a connection profile in order to get a wired (ethernet) connection to work.  

I don't know if I'd tried the solution described above before, but there was a kernel update last night that may have made it work again.  Or it may never have been broken, just changed, or maybe there is something about my current home connection that requires the wired connection to be explicitly created.

---

### Post by christopherbalz on 2010-03-19
Thank you roman2440 - I checked the wireless and it is indeed at full power (10).  The left side of the machine is about six inches from the 2wire wireless router.  Additionally, I have a new D-Link DIR-628 wireless router on the other side (right) of the machine, about five inches away.

The wireless channel is on 'auto' and works well when the machine has come out of a clean reboot/restart.  I have since learned that the machine seems to only experience wireless connection problems when it has come out of 'suspend' mode.

As posted above, I got the wired ethernet to work.  That plus the fact that wireless works out of a restart/boot is good enough for me.  It would be nice if it would work out of hibernate, though.  I suppose it's possible that wireless channel setting 'auto' doesn't work as well when coming from 'suspend' due to some software issue. 

I never had a wireless issue on my machine (IBM ThinkPad R51; circa 2004) with prior versions of Ubuntu, although there was a bad NetGear router (lamely marketed as "open source" - you had to hack the install program to get it to work on anything but the IE browser from Microsoft) that didn't work well in either wired or wireless mode.  

Some posts I have seen indicate that it is a kernel issue.  If so, I imagine it will not be long before it's fixed.

In any case, certainly, setting a different wireless channel is a good thing to try to get wireless to work when the machine is out of 'suspend' and having a wireless connection issue.  Thanks for the tip.

---

