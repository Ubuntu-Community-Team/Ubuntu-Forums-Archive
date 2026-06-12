---
title: "Can connect to IP but not hostname"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by Nevon on 2009-03-05
I've been trying to set up file and printer sharing between some Ubuntu boxes and some Windows XP boxes using Samba. It seems like I've gotten the Windows machines to see the Ubuntu shares, but my Ubuntu computers can't see the Windows shares. Neither did they automatically detect the Windows-attached printer. However, I can access shares and printers if I do it via IP instead of hostname. smb://192.168.55.98/HPC4280 works, but smb://NINA/HPC4280 doesn't - even though they're the same machine. 

Also, pinging IP addresses works, but not pinging hostnames. This is true both for pinging from Ubuntu &#8594; Windows and the other way around.

The problem is that every time I reboot one of the Windows computers they get a new IP address, which means I can't access the printer until I change the associated IP. 

I've checked my /etc/resolv.conf, and it points to my router and my ISP as it should. 

Any ideas as to what the problem could be? Should I be looking at the router settings?

If you need any additional info, just ask.

---

### Post by puppywhacker on 2009-03-05
Hi,

Name resolving for samba uses NMB and LMHOSTS. These are the microsoft netbios equivelents to DNS or the HOSTS file resolving. Therefor pinging the host is therefor different than "seeing" the host.

Since you use internal 192.168 addresses you might consider assigning static addresses. That way you can set all your names in /etc/lmhosts

The windows browsing is half of a mystery to me, so goodluck figuring them out.

---

### Post by Nevon on 2009-03-05
> **puppywhacker said:**
> Hi,

Name resolving for samba uses NMB and LMHOSTS. These are the microsoft netbios equivelents to DNS or the HOSTS file resolving. Therefor pinging the host is therefor different than "seeing" the host.

Since you use internal 192.168 addresses you might consider assigning static addresses. That way you can set all your names in /etc/lmhosts

The windows browsing is half of a mystery to me, so goodluck figuring them out.
How do I assign static internal IP addresses? Do I do that from within the router?

---

### Post by issih on 2009-03-05
[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

That still works I think. Your basic problem is that windows networking uses a seperate hostname resolution protocol called netbios that ubuntu does not include by default.

Hope that helps.

P.S. static ips are set in network manager or /etc/network/interfaces, but you need to be careful not to impinge on any dhcp ranges used by your router.

---

### Post by Nevon on 2009-03-05
> **issih said:**
> [http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

That still works I think. Your basic problem is that windows networking uses a seperate hostname resolution protocol called netbios that ubuntu does not include by default.
Winbind was already installed, and making those changes in /etc/nsswitch.conf doesn't seem to do anything at all.

> **issih said:**
> P.S. static ips are set in network manager or /etc/network/interfaces, but you need to be careful not to impinge on any dhcp ranges used by your router.

Tried that, but I think I did something wrong. I just lost access to the network. Was that because I used an IP that was similar to the one my router gave me?

---

### Post by issih on 2009-03-05
Strange, it works on my box, anyway to do static ip's, assuming you have a bog standard home network you need to use the following:

IP address that is unique on the local network and in the same subnet as your router.

Given that you mention that one of your addresses is: 192.168.55.98.

Potentially valid IP addresses in a normal home network would be 192.168.55.2 through to 192.168.55.255. The first three numbers should stay the same. You need to ensure, however that no other machine uses the same last number, and that any addresses handed out by the router using dhcp do not conflict either (usually you can set the range that dhcp will use in the router config).

Your subnet mask will probably be 255.255.255.0 and your default gateway will be whatever the address of your router is, and the same goes for dns server.

You need to set all of those to get things working properly.

Hope that helps

---

### Post by issih on 2009-03-05
One potential work around is to append .local to the hostname you are trying to access, that way it should use avahi to resolve the IP address. seems to work here

---

### Post by Nevon on 2009-03-05
> **issih said:**
> One potential work around is to append .local to the hostname you are trying to access, that way it should use avahi to resolve the IP address. seems to work here

Doesn't work for me.

> **issih said:**
> Strange, it works on my box, anyway to do static ip's, assuming you have a bog standard home network you need to use the following:

Oddly enough, that doesn't seem to work. Whenever I set a static IP, I can't access the internet anymore. I can connect to the local network though. I just can't get online.

---

### Post by issih on 2009-03-05
Have you set default gateway to the routers ip address?

---

### Post by Nevon on 2009-03-06
> **issih said:**
> Have you set default gateway to the routers ip address?

Yes. The default gateway is the same as the router's IP address.

---

### Post by issih on 2009-03-08
At this point theres not much to suggest other than double check everything..

See if you can ping the router's ip, that would confirm local networking is functional

See if you can ping an ip address out in the wilds of the internet, e.g. this 74.125.43.147 is a google server, can you ping that?

does it resolve to an ip if you ping [www.google.com](www.google.com)

the settings I suggest should work so you are down to troubleshooting time.

---

### Post by redmk2 on 2009-03-08
> **Nevon said:**
> I've been trying to set up file and printer sharing between some Ubuntu boxes and some Windows XP boxes using Samba. 

It seems like I've gotten the Windows machines to see the Ubuntu shares, but my Ubuntu computers can't see the Windows shares. Neither did they automatically detect the Windows-attached printer. 

However, I can access shares and printers if I do it via IP instead of hostname. smb://192.168.55.98/HPC4280 works, but smb://NINA/HPC4280 doesn't - even though they're the same machine. 

Also, pinging IP addresses works, but not pinging hostnames. This is true both for pinging from Ubuntu &#8594; Windows and the other way around.

The problem is that every time I reboot one of the Windows computers they get a new IP address, which means I can't access the printer until I change the associated IP. 

I've checked my /etc/resolv.conf, and it points to my router and my ISP as it should. 

Any ideas as to what the problem could be? Should I be looking at the router settings?

If you need any additional info, just ask.

This is a pretty common situation.  You actually have 2 issues to deal with.  

The first item is a best practice idea.  Whenever you have services to offer the network (the shared printer) it should always be at a known location (a fixed IP address).  Clients should not have to search for the address.

Second, you to should have a LAN wide naming service if you wish to access the server (the shared printer) by an assigned name.  There are several ways to accomplish this.

You can use either netBIOS (COMPUTER NAME) or DNS (hostname).  In mixed networks (linux and Windows) I recommend DNS hostnames.  Both windows and Linux have ways of understanding DNS hostnames.    Samba will also understand DNS hostnames.

If you have a small network and your not going to be constantly making changes this can be accomplished with entries in the "hosts" file.  The Linux (Ubuntu) hosts file is located at: **/etc/hosts**.  The hosts file on a Windows XP machine is located at:  **C:\WINDOWS\system32\drivers\etc\hosts**.

The hosts file maps the IP address to the hostname.  This  is my hosts file from Ubuntu:```

127.0.0.1 localhost
192.168.1.10   ferrari
192.168.1.12   jaguar
192.168.1.200  hp2200

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

This is the hosts file from Windows XP```
# Copyright (c) 1993-1999 Microsoft Corp.

#

# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.

#

# This file contains the mappings of IP addresses to host names. Each

# entry should be kept on an individual line. The IP address should

# be placed in the first column followed by the corresponding host name.

# The IP address and the host name should be separated by at least one

# space.

#

# Additionally, comments (such as these) may be inserted on individual

# lines or following the machine name denoted by a '#' symbol.

#

# For example:

#

#      102.54.94.97     rhino.acme.com          # source server

#       38.25.63.10     x.acme.com              # x client host



127.0.0.1       localhost
192.168.1.10 ferrari      # This host
192.168.1.12 jaguar       # Ubuntu host
192.168.1.200 hp2200      # Networked Printer 

```


As you can see the entries are the same for both XP and Ubuntu hosts files.  Both hosts can be called by name and so can the printer.

My suggestion is to have fixed IP addresses and use hosts files to map the IP addresses to the host names.

If you have a larger network where you need to administer the hostnames (DNS) from a centralized location, but still a home network, I would use [**DNSmasq**]("http://thekelleys.org.uk/dnsmasq/doc.html").

---

### Post by Nevon on 2009-03-09
> **issih said:**
> See if you can ping the router's ip, that would confirm local networking is functional

See if you can ping an ip address out in the wilds of the internet, e.g. this 74.125.43.147 is a google server, can you ping that?

does it resolve to an ip if you ping [www.google.com](www.google.com)

Yes, I could ping all of those.

> **redmk2 said:**
> This is a pretty common situation.  You actually have 2 issues to deal with.  

The first item is a best practice idea.  Whenever you have services to offer the network (the shared printer) it should always be at a known location (a fixed IP address).  Clients should not have to search for the address.

Second, you to should have a LAN wide naming service if you wish to access the server (the shared printer) by an assigned name.  There are several ways to accomplish this.

You can use either netBIOS (COMPUTER NAME) or DNS (hostname).  In mixed networks (linux and Windows) I recommend DNS hostnames.  Both windows and Linux have ways of understanding DNS hostnames.    Samba will also understand DNS hostnames.

If you have a small network and your not going to be constantly making changes this can be accomplished with entries in the "hosts" file.  The Linux (Ubuntu) hosts file is located at: **/etc/hosts**.  The hosts file on a Windows XP machine is located at:  **C:\WINDOWS\system32\drivers\etc\hosts**.

My suggestion is to have fixed IP addresses and use hosts files to map the IP addresses to the host names.
That's exactly what I've been trying to do. However, I can't seem to set any fixed IPs. Whenever I try in Ubuntu, I just lose my internet access.

---

### Post by issih on 2009-03-09
I meant can you ping those from a fixed ip address, if that all worked with a fixed ip then you should be able to access the internet, as you need both ip accesss and dns working to be able to ping [www.google.com](www.google.com).

I can only think that you are running into intrepid's little fixed ip bug somehow

This page should help:

[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

I think I did the 2nd method which basically is to copy down the mac address of the network card, then delete the pre-existing connection entirely, and create a new one using the mac address of my network card.

I know I had to do this when intrepid first launched, but I had assumed that this would have been patched by now, maybe it hasn't.

Hope that helps

---

### Post by Nevon on 2009-03-09
> **issih said:**
> I can only think that you are running into intrepid's little fixed ip bug somehow

This page should help:

[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

How do I know what IP to assign to the computers? My router reports the DHCP IP pool to range between 192.168.55.2-102, does that mean I should assign an IP within that range or outside it? It also has options for DHCP IP address reserving, should I reserve whatever IP addresses I decide to assign to the computers?

---

### Post by issih on 2009-03-09
The dhcp pool is the range of numbers that the router will use when it hands out addresses to clients connecting using dhcp. Therefore any static ip's on the same network should be outside this range (i.e. larger than 102 in your case) so that there is no chance that a random client connects and is handed a dhcp assigned ip that is already in use in the network.

The dhcp reserving feature is actually an alternative to static ips, but not one that all routers have. In fact in your case it may be a perfect solution.

In essence, using dhcp reservation, the router looks at the mac address (basically the networking hardware profile) of all clients trying to connect using dhcp and if it matches any of the mac addresses in its list it will hand that computer a specific predefined ip address from the dhcp pool rather than just one at random.

It basically allows you to achieve the same thing as having a static ip, but still using dhcp to manage the ip assignments.

---

### Post by Nevon on 2009-03-09
> **issih said:**
> The dhcp reserving feature is actually an alternative to static ips, but not one that all routers have. In fact in your case it may be a perfect solution.

In essence, using dhcp reservation, the router looks at the mac address (basically the networking hardware profile) of all clients trying to connect using dhcp and if it matches any of the mac addresses in its list it will hand that computer a specific predefined ip address from the dhcp pool rather than just one at random.

It basically allows you to achieve the same thing as having a static ip, but still using dhcp to manage the ip assignments.

Hey, that's perfect! So basically I just input my network interface's MAC address (called HWaddr in ifconfig?) as the physical address, choose an IP within the DHCP range, and voila! I pretty much get a static IP by DHCP.

---

### Post by issih on 2009-03-09
Thats about all there is to it yes :)

Its a good solution if your router supports it.. I think hwaddress is probably the right information, they look something like this at any rate:

```
00:1b:63:b8:cd:f8 
```

---

### Post by SteinbergerNate on 2009-03-09
One possible solution that I've started using is an alternative firmware for the router. dd-wrt is a really nice one and has something called static dhcp. Sounds kinda like what you guys are already talking about. I have a standard range of ip addresses for dhcp but then I can take the mac address of each computer/printer/whatever that I want a static ip for and assign it. 

Really helpful when you have a network printer that you don't want the ip to change on.

---

### Post by Nevon on 2009-03-09
> **SteinbergerNate said:**
> One possible solution that I've started using is an alternative firmware for the router. dd-wrt is a really nice one and has something called static dhcp. Sounds kinda like what you guys are already talking about. I have a standard range of ip addresses for dhcp but then I can take the mac address of each computer/printer/whatever that I want a static ip for and assign it. 

Really helpful when you have a network printer that you don't want the ip to change on.

I don't want to mess around with my router's firmware, in case I muck something up permanently (it's not really my router). This solution worked perfectly!

> **issih said:**
> Thats about all there is to it yes :)

Its a good solution if your router supports it.. I think hwaddress is probably the right information, they look something like this at any rate:

```
00:1b:63:b8:cd:f8 
```
Yup. The web configuration page could even fill in the MAC address automatically, so it was a breeze to set up. Now everything is working near perfectly (I still can't access samba shares via hostname, even though I've configured the /etc/hosts file).

---

### Post by redmk2 on 2009-03-09
Where have you configured the /etc/hosts file?  You need to set this up on all hosts in the net.  The host asking for name resolution uses its own file.

---

### Post by Nevon on 2009-03-09
> **redmk2 said:**
> Where have you configured the /etc/hosts file?  You need to set this up on all hosts in the net.  The host asking for name resolution uses its own file.

I've configured it on all computers in the house. Both Windows and Linux.

---

### Post by redmk2 on 2009-03-09
Can you ping by hostname?  As in -- ping *hostname*

---

### Post by Nevon on 2009-03-09
> **redmk2 said:**
> Can you ping by hostname?  As in -- ping *hostname*

That's the weirdest part; I can!

---

### Post by redmk2 on 2009-03-09
Not so weird if you think about it.  

I'll bet you made your shares using Gnome (Nautilus) IE: Places >> Connect to Server >> ,or some such method.  You also made them before you added the hosts files and a fixed IP address.  These are located at /var/lib/samba.  Try creating a new (different named) share.  If it works, I would delete the old shares.  See here: [http://ubuntuforums.org/showthread.php?t=1083000]("http://ubuntuforums.org/showthread.php?t=1083000")

You can manually define them in the file smb.conf.  This located at /etc/samba/smb.conf.  I define mine manually and use the same conf file whenever I  build a new server.

Edit: It is also important that you understand that the underlying routines (libs) used for Gnome (gvfs -GIO) are different than the ones used by the CLI commands (smbfs).  There are instances where you might be able to view shares using the CLI and not be able to view them in Nautilus.  ;-)

---

