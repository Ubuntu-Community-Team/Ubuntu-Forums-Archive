---
title: "Static IP in 11.10 not working"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by MickSulley on 2011-11-02
Hi,

I have been struggling with a few issues in 11.10 and I think the network is the cause of most of them.  This is a desktop machine, wired connection no wireless.

I have it configured for static IP, on the IPv4 Setting tab I have
Method:  Manual
Address  192.168.0.90
Netmask  255.255.255.0
Gateway  192.168.0.1
DNS Servers  192.168.0.1
Search domains  255.255.255.0
Require IPv4 addressing... is ticked

I can access the internet, that is how I am writing this.
If I click on the network icon it has Wired Network and underneath that it says 'Device not managed'
If I click on Connection Information the box says
  Error displaying connection information:
  No valid active connections found!

ifconfig returns
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:36:d4:4c  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fe36:d44c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4405363 (4.4 MB)  TX bytes:942439 (942.4 KB)
          Interrupt:20 Memory:fbfc0000-fbfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6419 (6.4 KB)  TX bytes:6419 (6.4 KB)

So it looks like the ip is 192.168.0.8 and not 192.168.0.90 as I set it.
Also I have just tried to connect to it with SSH from another machine and I can connect to 192.168.0.8 but not 192.168.0.90 which I guess confirms that it has not used the static IP I set.

What is going on here?  Is setting a static IP different in 11.10?

Thanks
Mick

---

### Post by MickSulley on 2011-11-03
Fixed it!!!  Although I really don't understand why.

From a Google hit I edited my /etc/network/interfaces file and deleted the contents, reboot and everything is fine.

Like I said, don't understand why, but hey ho....

Cheers
Mick

---

