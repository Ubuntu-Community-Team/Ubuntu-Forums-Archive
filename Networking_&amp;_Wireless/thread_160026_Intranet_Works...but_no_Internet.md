---
title: "Intranet Works...but no Internet"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by guidotex on 2006-04-14
Hola, amigos!
   Here goes:  after wading through much tribulation, I have finally got my ubuntu 5.10 server connected to my router:) .  This is way cool, because I can now connect to it with the other devices on my network...or device.  This particular device happens to be a sweet little dual boot machine that I cooked up last year.  It's running XP and FedoraCore3(upgraded to current kernal).  Point being, that I can boot in XP and open a putty (SSH client) session, or I can boot in FC3 and SSH from a command line into my ubuntu server.  No problemo!  I can also login to my ubuntu server and ping all sorts of cool things(actually only two).  I can successfully ping the router, and I can successfully ping the other machine (no matter which OS is running).

   However (and here's the rub), I CAN'T GET OUT!!  That is, I can't connect to anything on the internet.  I can't use apt, I can't ping google, I can't do anything except read messages like "connect: Network is unreachable".  (By the way, the internet connection is fine for the other machine, with either OS running.  Yea, verily I type this as I sit in front of GNOME on FC3).

   So, anybody know what gives? ](*,) 

muchos gracias por todos!!

---

### Post by bscbrit on 2006-04-14
Does FC3 install a firewall as default?

Have you told the FC3 what gateway to use?

---

### Post by guidotex on 2006-04-14
I don't know about the FC3 firewall.  I haven't told FC3 what gateway to use.  However, FC3 isn't the problem.  It's the ubuntu server 5.10 that I can't get out  to the internet on. 

Following is what I have done to get it working:

  ifconfig eth0 up                                //turn it on
  ifconfig eth0 192.168.254.5                //assign ubuntu box ip address
  ifconfig eth0 netmask 255.255.255.0    //assign ubuntu box netmask

'route' gives me the following:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.254.0   *               255.255.255.0   U     0      0        0 eth0

My router's address on the intranet is 192.168.254.254.
I don't know how to find it's internet address (assigned by my ISP).

My configuration is as follows :  Cable internet service from COX.  Comes into cable modem (Motorola surfboard).  From there to router (Siemens SpeedStream).  From router out to my two boxes.

Not sure where to go from here.

---

### Post by mips on 2006-04-14
You have no default route specified.

---

### Post by guidotex on 2006-04-15
[QUOTE=mips]You have no default route specified.[/QUOTE]
aye, that's true.

But I'm not sure what that really means.
 -What is a default route?
 -How do I set one up?
 -what should it be (i.e what address, etc should it be, and how do I find this address?)

Thanks.

---

### Post by guidotex on 2006-04-15
[QUOTE=mips]You have no default route specified.[/QUOTE]
Okay, I got the default route specified using
route add default gw 192.68.254.254 (address of my router).
now 'route' shows me this:

Kernel IP routing table
Destination     Gateway               Genmask         Flags Metric Ref    Use Iface
192.168.254.0   *                           255.255.255.0   U        0      0          0    eth0
default          192.168.254.254    0.0.0.0                UG       0      0          0    eth0



When I use 'route' in FC3, i get:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.254.0   *                      255.255.255.0   U        0        0        0    eth0
169.254.0.0        *                      255.255.0.0       U        0        0        0    eth0
default         192.168.254.254  0.0.0.0               UG      0       0        0     eth0

So what's that extra line in there (and how do I get it).

Any other ideas, y'all?  I'm still stuck in my intranet!!

Thanks,
guidotex

---

### Post by bscbrit on 2006-04-15
Sorry about the confusion regarding which computer we were working on - your initial post confused me a little bit.

The 169.254.0.0 was allocated automatically when the FC3 computer couldn't find a DHCP server.  Are you using DHCP or manual IP addresses? - I assume the latter but it seems that, initially, the FC3 was looking for DHCP.  If you have specified the router address correctly then it should not be required on either machine.

On your ubuntu machine, providing you have restarted the network, you should now be able to ping machines on your intranet and at least numbered IPs on the internet.  Depending on whether you have set up DNS resolution (or it has been set up automatically) then you might also be able to ping named IPs e.g. [www.ubuntuforums.org](www.ubuntuforums.org).

If it is still not working, can you please post the contents of /etc/networks/interfaces file.

---

### Post by bscbrit on 2006-04-15
Just for information:

> 
*  "Autoconfiguration" IP Addresses:

  169.254.0.0 - 169.254.255.255

Addresses in the range 169.254.0.0 to 169.254.255.255 are used automatically by some PCs and Macs when they are configured to use IP, do not have a static IP Address assigned, and are unable to obtain an IP address using DHCP.

This traffic is intended to be confined to the local network, so the administrator of the local network should look for misconfigured hosts. Some ISPs inadvertently also permit this traffic, so you may also want to contact your ISP.


---

### Post by guidotex on 2006-04-19
figured it!  
I edited my /etc/network/interfaces file to set up with DHCP instead of a static ip.

I also added the nameservers of my ISP (COX) to etc/resolv.conf

I'm on!  I can ping, send stuff.  It's ALL GOOD YO!.  Thanks everybody for your help and clues to getting this done along the way.

The first cup of ubuntu is pretty good....wonder how the rest of the pot tastes?

-guidotex

---

