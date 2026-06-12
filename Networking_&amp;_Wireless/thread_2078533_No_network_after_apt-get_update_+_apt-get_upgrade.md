---
title: "No network after apt-get update + apt-get upgrade"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by jvahub on 2012-10-31
Hi,
 
I'm running a virtual machine (Hyper-V) Linux image and thus am only using virtual LAN (no wireless whatsoever).
 
This was Ubuntu 10.04.3 LTS, after apt-get upgrade is .4.
After I rebooted I now longer seem to have a network connection.
 
I've checked settings and could not find anything wrong. Then I've removed the network card from the image and re-added it. Unfortunately that also did not help.
 
When I ping localhost I get this:
64 bytes from localhost (127.0.0.1): imc..... etc.
 
When I ping the IP the image should have I get this:
connect: Network is unreachable
 
When I check /etc/network/interfaces everything seems fine/unchanged.
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
address 10.etc....
 
When I do a route -n I get something I think I'm not supposed to get:
 
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
<nothing here, empty!>
 
 
Any idea what could be wrong / how I can resolve this?
Thanks!

---

### Post by jvahub on 2012-10-31
Oh and ifconfig says this:
 
lo     Link encap: Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
etc...

---

### Post by jvahub on 2012-10-31
It seems somehow the NIC does not get recognised. It says this when I do a networking restart...
 
So before the update/upgrade everything was fine. After this suddenly an unrecognised Hyper-V virtual NIC - what gives?

---

