---
title: "One nic works only if the other is disabled"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by dcroxton on 2009-08-17
(Using Jaunty): I have a wired nic and a wireless usb dongle on my computer.  Either of them will work, but only one at a time.  I have to type "sudo ifdown eth0" to get the wireless working, and "sudo ifdown eth1" to get the wired one working (or unplug the dongle).  From my ignorant perspective, it seems to be something with DHCP.  Both devices will function, but I don't get a workable DHCP lease unless one is disabled.  I thought it might be related to my configuration, but I have everything commented out in /etc/network/interfaces except

iface lo inet loopback
auto lo
iface eth0 inet dhcp
auto eth0

Still, when I shut down eth0, I get the following:

```
There is already a pid file /var/run/dhclient.eth0.pid with pid 3780
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:0b:6a:90:50:02
Sending on   LPF/eth0/00:0b:6a:90:50:02
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
 * Reloading /etc/samba/smb.conf smbd only
   ...done.

```

The strange thing is that this occurs regardless of whether both are connected to anything.  I would really like to have them both be able to function at the same time, but I would settle at the moment for just being able to use my wireless without having to disable the wired nic every morning.

I have the same issue on my wife's laptop, which runs Xubuntu + Hardy.

Sincerely,
Derek

---

### Post by Iowan on 2009-08-17
Are both interfaces trying to get leases in the same subnet - check **ifconfig -a** when each interface is active.

---

### Post by Dave WuzHere on 2009-08-17
hmm..I think I'm in the same boat.
 
I'm running Jaunty Jackalope on a thinkpad (built-in gigabit ethernet and 54mbps wireless).
 
Wireless gets a DHCP address, but I can't use it unless I disable eth0 using;
 
       sudi ifdown eth0  
 
Is there a "device manager" somewhere  like there is in Windows or a command that will disable a network device for longer than the next reboot?
 
I've been using Ubuntu for almost 36 hours!
 
Thanks for your help guys, these forums have been great.
 
Dave

---

### Post by dcroxton on 2009-08-17
I brought up eth0 and this is the output of ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:90:50:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xcc00 

eth1      Link encap:Ethernet  HWaddr 00:11:a3:00:4e:ca  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:a3ff:fe00:4eca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14756114 (14.7 MB)  TX bytes:4187250 (4.1 MB)

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:6a:90:50:02  
          inet addr:169.254.3.218  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1674737 (1.6 MB)  TX bytes:1674737 (1.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-A3-00-4E-CA-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

It's interesting that I'm able to post this with eth0 up.  The wireless connection never lets me get on the internet until I bring eth0 down.  Once the internet connection was working, however, I'm now able to bring eth0 back up and the wireless still works.

Sincerely,
Derek

---

### Post by Iowan on 2009-08-18
You can see if it works - the avahi address is usually a bad sign (unless you have other machines in that subnet).

---

