---
title: "Eth0 works on one network, but the another"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by skewray on 2009-07-27
I have a KDE 8.10 machine that works fine with a direct internet connection.  I have another network with a Windows machine (10.0.0.4) and a QNX machine (10.0.0.2).  I moved the ethernet cable over and used KNetworkManager to set the KDE machine to 10.0.0.3, with a netmask of 255.255.0.0 (same as the Windows machine).  most programs (ie, ping) on the KDE machine report that the network is unreachable, yet Wireshark can see packets from the other machines.  IfConfig doesn't report any IP address or any netmask either.  What could be the problem?

Thanks,

Brian

---

### Post by Iowan on 2009-07-27
How did you connect the Kubuntu machine to the 10.0.X.X network - via switch or hub? Check **route** results to see the gateway.
**ifconfig** reports no ip address? That can't be good... As I (barely) recall, Hardy and Intrepid were not kind to static addresses.  I still have some of the How-To links - if they still apply... 
[Here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is one.

---

### Post by skewray on 2009-07-27
Thank you for the reply.  The network just has one dumb 10/100 hub.  The 'route' command doesn't work either; it reports that the network is unreachable as well.  Any hint towards possibly useful commands to try out would be good, or directories to search.  Digging through /etc hasn't turned up anything useful yet, but one never knows...

Brian

---

### Post by skewray on 2009-07-28
"ifconfig eth0 10.0.0.3/16" fixes the problem.  Apparently the KDE gui is completely non-functional for static IP addressing.

Brian

---

