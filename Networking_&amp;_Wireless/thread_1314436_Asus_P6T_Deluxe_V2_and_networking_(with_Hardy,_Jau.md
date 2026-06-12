---
title: "Asus P6T Deluxe V2 and networking (with Hardy, Jaunty &amp; Karmic)"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by tim71 on 2009-11-04
I have a computer with Asus P6T Deluxe V2 and I have a problem.

This motherboard has two 88E8056 PCI-E Gigabit Ethernet Controllers from Marvell on it and the problem is related to this.

When I initially build this setup few months ago, I tried to run 32bit Hardy installation from the old computer, which worked pretty good, but had one BIG problem, which killed all my home network every time after the computer was shut down. Lights on NIC port stayed on and after some time (10-15 min) this network adapter started to flood the router with some strange packets to the point, when router became unaccessible. It happened every time after shutting down the machine. There was only one simple cure - flip the power switch on the PSU off (and on again) or just simply pull the plug from the mains. Disconnecting the ethernet cable did not help - flood would continue immediately after reconnection.

It may partly be hardware issue, as described here -> [http://blog.controlspace.org/2009/09/asus-p6t-deluxe-v2-networking-problems.html](http://blog.controlspace.org/2009/09/asus-p6t-deluxe-v2-networking-problems.html) - because it also appears with other OS, if NIC will remain up after the shutdown - including the motherboard-integrated Splashtop. When computer is started up from this state, the network adapter will be reset and brought down at the time the message **"Initialising USB controllers"** is displayed.

However there is another side of this problem - as mentioned before, 32bit Hardy failed on bringing down the active NIC on shutdown.

Then I made a new clean install with 64bit Jaunty and the problem disappeared - there always was a message like this
```
nm-system-settings: SCPlugin-ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_1a_92_XX_XX_XX)
```on console -> NIC was brought down without problems and the system was cleanly shut down - ALWAYS!

Everything was fine until I installed Karmic. I did a clean install once again and guess what - the old problem from Hardy was BACK! Shutdown left the NIC up again.
```
~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          inet addr:10.0.0.1  Bcast:10.0.3.255  Mask:255.255.252.0
          inet6 addr: fe80::224:8cff:fe52:892d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:178679 (178.6 KB)  TX bytes:38559 (38.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:580 (580.0 B)  TX bytes:580 (580.0 B)
```Few simple commands revealed that system has no clue of things at all - connection can be managed normally with nm-applet, but command line has an idiotic output like this.
```
~$ sudo ifdown eth0
Ignoring unknown interface eth0=eth0.

~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0
```Actually (un)ticking the 'Enable networking' option brings the interface down and up again, but obviously it can not be done with ifupdown.

Unticking the 'Enable networking' - 
```
U-desktop NetworkManager: <info>  Sleeping...
Nov  4 18:45:14 U-desktop NetworkManager: <info>  (eth0): now unmanaged
Nov  4 18:45:14 U-desktop NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
Nov  4 18:45:14 U-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 37).
Nov  4 18:45:14 U-desktop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Nov  4 18:45:14 U-desktop avahi-daemon[1573]: Withdrawing address record for 10.0.0.1 on eth0.
Nov  4 18:45:14 U-desktop avahi-daemon[1573]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.0.1.
Nov  4 18:45:14 U-desktop avahi-daemon[1573]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov  4 18:45:15 U-desktop NetworkManager: <info>  (eth0): cleaning up...
Nov  4 18:45:15 U-desktop NetworkManager: <info>  (eth0): taking down device.
Nov  4 18:45:15 U-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Nov  4 18:45:15 U-desktop avahi-daemon[1573]: Withdrawing address record for fe80::224:8cff:fe52:892d on eth0.
Nov  4 18:45:15 U-desktop kernel: [   81.126996] sky2 eth0: disabling interface
```re-enabling it again - 

```
U-desktop NetworkManager: <info>  Waking up...
Nov  4 18:45:59 U-desktop NetworkManager: <info>  (eth0): now managed
Nov  4 18:45:59 U-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov  4 18:45:59 U-desktop NetworkManager: <info>  (eth0): bringing up device.
Nov  4 18:45:59 U-desktop NetworkManager: <info>  (eth0): preparing device.
Nov  4 18:45:59 U-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov  4 18:45:59 U-desktop kernel: [  125.196529] sky2 eth0: enabling interface
Nov  4 18:45:59 U-desktop kernel: [  125.198327] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  4 18:46:01 U-desktop kernel: [  126.971096] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Nov  4 18:46:01 U-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Nov  4 18:46:01 U-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Wired connection 1'
Nov  4 18:46:01 U-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov  4 18:46:01 U-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Nov  4 18:46:01 U-desktop avahi-daemon[1573]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.1.
Nov  4 18:46:01 U-desktop avahi-daemon[1573]: New relevant interface eth0.IPv4 for mDNS.
Nov  4 18:46:01 U-desktop avahi-daemon[1573]: Registering new address record for 10.0.0.1 on eth0.IPv4.
Nov  4 18:46:01 U-desktop kernel: [  126.973070] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov  4 18:46:02 U-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Nov  4 18:46:02 U-desktop NetworkManager: <info>  Policy set 'Wired connection 1' (eth0) as default for routing and DNS.
Nov  4 18:46:02 U-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Nov  4 18:46:02 U-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
```Currently I have only one way for bringing down the connection on shutdown - disabling the "Available for all users" option in the connection options, which brings the NIC down before the shutdown sequence - which makes impossible for the umountnfs script to run, because the network connection is already lost. This causes a long timeout on shutdown because nfs/samba shares would fail to unmount.

When the connection is made "Available for all users" the NIC will remain up after shutdown - which would not be a problem in itself without this packet flood thing.

From the Ubuntu point-of-view there is one question - can it be a NetworkManager/ifupdown or sky2 driver bug?

Have anyone has any experience similar to this and maybe some ideas what to try?

---

### Post by tim71 on 2009-11-05
It is probably sky2 bug after all
    
    
    [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156738](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156738) <- before jaunty
    
    was fixed in jaunty
        
        [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464305](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464305) <- again back in karmic
 
 [SIZE=1]P.S. This probably means, that Asus is shipping this motherboard with buggy driver integrated into on-board Splashtop OS.[/SIZE]

---

### Post by tim71 on 2009-11-05
Now one more update to this - I digged around the internet and (almost) accidentally found out the firmware issues about 88E8056 NIC chip
```
~$ lspci -vvv |grep 88E8056
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
```
I studied the following links:

[http://vip.asus.com/forum/view.aspx?board_id=1&model=P6T+Deluxe+V2&id=20090614044621112&page=1&SLanguage=en-us]("http://vip.asus.com/forum/view.aspx?board_id=1&model=P6T+Deluxe+V2&id=20090614044621112&page=1&SLanguage=en-us")

[http://vip.asus.com/forum/view.aspx?SLanguage=en-us&id=20080813182205171&board_id=1&model=P&page=1&count=18]("http://vip.asus.com/forum/view.aspx?SLanguage=en-us&id=20080813182205171&board_id=1&model=P&page=1&count=18")

[http://www.driverheaven.net/windows-vista-forum/131109-marvell-yukon-88e8056-sata-raid-problem-under-vista.html]("http://www.driverheaven.net/windows-vista-forum/131109-marvell-yukon-88e8056-sata-raid-problem-under-vista.html")

which all pointed to this FAQ on Gigabyte's site:

[http://www.gigabyte.com.tw/Support/Motherboard/FAQ_Model.aspx?FAQID=2372&ProductID=2422&ClassValue=Motherboard]("http://www.gigabyte.com.tw/Support/Motherboard/FAQ_Model.aspx?FAQID=2372&ProductID=2422&ClassValue=Motherboard")

I took the risk and updated the firmware - 
```
~$ lspci -vvv |grep 88E8056
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
```

After repeating shutdown tests with both Ubuntu and Splashtop it looked like this problem is solved, but longer uptime with network activity like audio streaming etc brought the problem back again.

---

### Post by arjay67 on 2010-02-10
Is there any update on this?

I've been having a **very** similar issue with this also. I have seen it occur on Jaunty and Karmic. (can't remember if it was happening on Intrepid or not) The motherboard is Asus P5T with a Pentium D 3.2 gHz installed. This is my "sandbox" machine so I wanted to resolve these issues before migrating my primary desktop to Ubuntu.

I can duplicate the packet flood 100% of the time with Jaunty or Karmic installed. So far I have also attempted installations of DSL, Puppy, Mint in the Linux flavors and Windows XP, Vista32, 7/32 and the packet flood does not present itself on shutdown.

So, for my situation the issue does appear to be specific to Ubuntu and the Marvell chip.

---

