---
title: "Wired (and wireless) networking woes 8.04 32 bit"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by aidan.whitehouse on 2009-01-01
I have had enormous problems trying to install a RT2500 chipset wireless adapter.  So after a lot of attempts, I decided to do a fresh 8.04 install and try and hook up a wired connection (took me half a day to wire it in).

After doing the fresh Ubuntu install I had both my wired connections working (still no wireless).  The only networking changes I made were
[LIST]
[*]I installed ndiswrapper and the rt2500.inf driver, and blacklisted rt2500pci
[*]I configured a static IP address for wireless and wired adapters the same as they are in Windows
[/LIST]
After some initial router configuration issues due to IP address conflicts, everything still working really well.  Couple of reboots - still everything OK

Then another reboot, create additional user account and nothing works!  All wired and wireless connections showing in network manager, although without a link speed.  I *may* have booted windows in the meantime.

I have done some research on these forums, and it would appear that having the same static IP address on Windows and Linux can cause conflicts.  Anyone care to elaborate on this?  I would have thought that the router does not see anything dramatically different between Windows and Linux?  It should be the same MAC address after all?

I am going to try the following in the hopes that one of these solves the issue:

[LIST]
[*]Configure Linux and Windoze to use DHCP and get my router to assign the current static IP on a permanent lease.

[*]Restart Network Manager.
[/LIST]
Hope one of these solves it, but any other ideas really appreciated.  Sorry I can't grab any terminal output or screenshots - currently using Windoze...

---

### Post by aidan.whitehouse on 2009-01-01
OK it appears the addressing conflict was the problem.  Wired connection works OK now, if wireless is disabled:
[INDENT]eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          inet addr:192.nnn.nnn.nnn  Bcast:192.nnn.nnn.nnn  Mask:255.255.255.0
          inet6 addr: xxxx::xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2734081 (2.6 MB)  TX bytes:412879 (403.2 KB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xdd00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43784 (42.7 KB)  TX bytes:43784 (42.7 KB)

[/INDENT]

I will try and get wireless working OK, think that wpa_supplicant needs to be configured correctly.  Wired connection does not work at all

But I would still like to know why static IPs configured the same way in Windows and Ubuntu cause conflicts.

TIA

---

### Post by superprash2003 on 2009-01-01
the basic rule in networking is no 2 machines can have the same ip address on a network..

---

### Post by aidan.whitehouse on 2009-01-01
You have misunderstood.  This is the same machine but different O/S...

I was also careful to make sure that the same IP addresses were assigned to the same devices in Windows and Ubuntu.

My question remains.

---

