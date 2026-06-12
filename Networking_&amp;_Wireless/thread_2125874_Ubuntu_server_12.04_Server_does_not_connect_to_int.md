---
title: "Ubuntu server 12.04: Server does not connect to internet. SSH works fine"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by LiefhebberLinux on 2013-03-15
Hi I have have recently moved and got a new ISP. Connecting to the server worked out of the box, but the server has no connection to the internet. Not clear to me how to fix this. I have a Netgear cg3100 router (on 192.168.0.1)

My /etc/network/interfaces look like

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.250
        netmask 255.255.255.0
        gateway 192.168.0.1

my /etc/resolve.config looks like (I have no idea which addresses to use here, but it worked fine at my previous place)

nameserver 194.168.4.100
nameserver 194.168.8.100

ifconfig gives

eth0      Link encap:Ethernet  HWaddr 84:2b:2b:42:7e:dc  
          inet addr:192.168.0.250  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::862b:2bff:fe42:7edc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:968474 (968.4 KB)  TX bytes:455124 (455.1 KB)
          Interrupt:36 Memory:da000000-da012800 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4488378 (4.4 MB)  TX bytes:4488378 (4.4 MB)

Any help / suggestions would be greatly appreciated.

---

### Post by Roasted on 2013-03-15
What happens if you ping 8.8.8.8? Do you get a response?

What if you ping [www.weather.com?](www.weather.com?) Any response there?

I'm particularly interested in your nameserver section there. I just checked my server (12.04 server edition) at home and my nameserver is listed the same as my gateway, which in my case is 192.168.1.1. Try changing it to the same as your gateway... as your router, I would think, would forward you over to whatever DNS servers it picks up dynamically. For example, I just switched from Verizon DSL to Comcast Cable. My router was set to pick up DNS servers dynamically, so I changed nothing and my router still did its job fine - which I can only assume was due to having my gateway in the nameserver entry so it forwards accordingly.

If you can ping by IP, but not by an actual address, this definitely screams DNS issue.

---

### Post by LiefhebberLinux on 2013-03-15
Thanks for your suggestions.

ping 8.8.8.8 works fine
ping [www.weather.com](www.weather.com) does not work (unknown host)

changed my nameserver (in resolve.config)
to 192.168.0.1 (which is my router) and ran sudo /etc/init.d/networking restart

still the same issue. Other suggestions?

---

### Post by papibe on 2013-03-15
Hi LiefhebberLinux.

Could you post the results of these commands?
```
apt-cache policy network-manager

route -n

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by LiefhebberLinux on 2013-04-04
Thanks for your suggestion. Apologies for the late reply. I thought switching to dhcp and getting some default settings would be an option, but then I could not connect at all to the server. Took me a while to get a monitor to undo the damage. See below for the output

network-manager:
  Installed: (none)
  Candidate: 0.9.4.0-0ubuntu4.1
  Version table:
     0.9.4.0-0ubuntu4.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
     0.9.4.0-0ubuntu3 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages



route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


nslookup ubuntu.com
;; connection timed out; no servers could be reached

dig ubuntuforums.org
;; connection timed out; no servers could be reached

---

### Post by LiefhebberLinux on 2013-04-04
I figured this out. For people with similar issues. I had to update my nameservers in [COLOR=#000000]my /etc/resolve.config [/COLOR]

[COLOR=#000000]nameserver CHECK PRIMARARY ISP NAMESERVER[/COLOR]
[COLOR=#000000]nameserver CHECK SECONDARY ISP NAMESERVER[/COLOR]

---

