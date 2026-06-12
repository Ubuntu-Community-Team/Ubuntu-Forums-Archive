---
title: "ubuntu as router without firewall"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by dmshade3 on 2011-01-24
I want to use an Ubuntu server as a router - straight up - no firewall on it or in it.  I don't wan to do NAT or any other kind of translation.  I simply want it to be my point for creating/supporting subnets.

I have ip_forward enabled and it shows a "1" in the /proc/sys/net/ipv4/ip_forward file (might have mistyped that - it was from memory, it is correct when checked).  I have 4 nics in the "server" and I have dhcp-relay working - to route to a dhcp-server on one of the subnets.  And, the dhcp-relay is working very well.

But, I can't get anything but dhcp to relay or route.  I really don't want to have ipchains or nat or anything on the server - I want as little overhead as possible.

Any suggestions or places/things I should be looking at?

Details:
using ubuntu server 10.10 with gui/gnome config for both the router server and the dhcp server (on a subnet)

have 4 nics:

172.16.200.125/16 which is my default gateway on the server - as it goes out to my internet connection

172.17.1.0/24  (.1.1 on the server for each of these three)
172.18.1.0/24
172.19.1.0/24

I can ping form anything to any of the server nics and do get a reply.  But, I cannot ping to a pc on any subnet - like 18.1.100 from 17.1.100 - that fails.

Thanks in advance,

Mark

---

### Post by gmargo on 2011-01-24
What does your routing table look like?

---

### Post by dmshade3 on 2011-01-24
On the "router" server

techsupp@u-dhcp-relay-test:/proc/sys/net/ipv4$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.18.1.0      *               255.255.255.0   U         0 0          0 eth3
172.19.1.0      *               255.255.255.0   U         0 0          0 eth4
172.17.1.0      *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth1
172.16.0.0      *               255.255.0.0     U         0 0          0 eth1
default         172.16.1.1      0.0.0.0         UG        0 0          0 eth1


on the dhcp server (intentionally broken out onto one of the subnets - but successfully answering properyly to all workstations on all subnets)

netstat -r
Kernal IP routing table
Destination     Gateway                 Genmask          Flags     MSS     Window     irtt Iface
172.17.1.0      *                              255.255.255.0   U           0          0                0  eth0
link-local         *                              255.255.0.0       U           0          0                0 eth0
default             u-dhcp-relay-test   0.0.0.0               UG        0          0                0 eth0


Thanks,

Mark

---

### Post by SeijiSensei on 2011-01-24
> **dmshade3 said:**
> ```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.18.1.0      *               255.255.255.0   U         0 0          0 eth3
172.19.1.0      *               255.255.255.0   U         0 0          0 eth4
172.17.1.0      *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth1
172.16.0.0      *               255.255.0.0     U         0 0          0 eth1
default         172.16.1.1      0.0.0.0         UG        0 0          0 eth1

```

You have the wrong subnet on eth1.  172.16.0.0/16 covers the entire range of hosts from 172.16.0.0 to 172.31.255.255.  Assign a 255.255.255.0 netmask to eth1 rather than 255.255.0.0.

---

### Post by dmshade3 on 2011-01-24
I understand what you are saying, but that presents a problem.

We are trying to setup subnetting for building a, building b, and building c to have different subnets.  Thus, the need for a router to handle them and the dhcp relay (we need to have just one dhcp server for all subnets - so relay is needed).

That said, we use 172.16.x.x as our current main real network.  We are trying to test by creating a temporary test lan with the info given above (a server at 172.16.200.125 that acts as a router for all subnets, but allows traffic up to the main network and out the real internet gateway of 172.16.1.1.

We actually do have it routing now, by adding some rules to the main firewall/router to the internet.  I am not sure how to progress now to a larger/real world test - with the issue you mentioned.  We will have to change the main/real network of IP's before we can begin to truly employ the subnets - but need the downtime to make that change for all of the pcs, especially the limited number that have static IP's.

Thanks a bunch for your help!  It is truly appreciated.

Mark

---

### Post by dmshade3 on 2011-01-24
So, now I can get web traffic (ping, http, etc.) out through my Ubuntu network router all the way out to the Internet.

The last thing I need but can't quite get is for Windows networking to work between the subnets.  I have a pc on each subnet but none can see the other.  I have even searched by ip address - and each can't find the others.

Do I need to do something special to enable the flow of Windows Networking across the Ubuutu server/router?

Thanks,

Mark

---

### Post by SeijiSensei on 2011-01-24
Getting browsing to work in Windows across subnets is a tricky proposition.  

One solution is run to an internal DNS server, probably on the router, that contains the names and addresses of the hosts on the local network.  Windows 2000 and later will use DNS to resolve Netbios connections; just enter "\\host.example.com\share" when prompted to set up mapped network drive.  I believe if you pass "example.com" as a "search" or "domain" directive for name resolution through DHCP, you can use just "\\host\share".

However getting all the machines to see each other and appear in Network Neighborhood is a more complicated task.  You might want to look into setting up Samba's nmbd daemon to provide a "WINS" server.  Take a look at [this](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/integrate-ms-networks.html) and [this](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html) for help.

---

### Post by dmshade3 on 2011-01-25
I have the browsing/ftp/etc all working across the subnets.  I suspect that succeeded in spite of myself.  :-)

I just need to get the netbios name res/browsing working across them now.

Thanks for all the help!

Mark

---

### Post by dmshade3 on 2011-01-25
We have everything but Windows browsing working through the router (Ubuntu server).  We are even drawing dhcp addresses from the main Windows dhcp server for the subnets (at the same time as it serves the network that is not sub-netted).

We can browse the internet etc. all through the router/Ubuntu server.

I have tried to make sure that any/all traffic is allowed to flow through the router/Ubuntu server.  But, I don't seem to be finding a way for it to "route" that traffic.  It also fails from subnet to subnet to share - even by ip address (which are able to ping each other).

Any suggestions?  Or, have I gotten all I am gonna get out of it?

Thanks,

Mark

---

### Post by mips on 2011-01-25
> 172.16.0.0      *               **255.255.0.0**     U         0 0          0 eth1

Gonna cause you problems, flaunting basic tcp/ip rules will do that.

---

### Post by dmshade3 on 2011-01-25
Mips, thanks for the help.

I see the command you put and I understand where it does.  But where do I put or issue it?

PS - We have and will continue to have an external firewall.  This is only to work as an internal router for subnetting.  So the security risks should be nearly non-existent.   Now, if you mean that trying to use the command you gave will cause problems for IP of a non-security type, can you elaborate?

Thanks,

Mark

---

### Post by mips on 2011-01-26
> **dmshade3 said:**
> Mips, thanks for the help.

I see the command you put and I understand where it does.  **But where do I put or issue it?**


You don't, I just quoted part of your route output.

You cannot have overlapping networks and expect them to work.

172.16.200.125/16 overlaps all the other networks listed below.

172.17.1.0/24
172.18.1.0/24
172.19.1.0/24



Have a look at this, I know it's old and some things might have changed slightly but it's more or less what you want to do:
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)
[http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320) This is the background info to that tutorial.

There is more stuff in there than you need but you can leave out the firewalliing etc

---

### Post by dmshade3 on 2011-01-26
Ok, I understand about overlaps.
 
But, I am limited at this time because I am trying to use a connection to the prodcution network environment to develop a test solution.
 
Our production network runs on 172.16.x.x/16 - I have no choice on that as it is governed by someone above me.
 
I could change my subnets to something else - 10.x.x.x or 192.x.x.x - but I would have to get the person who has control of our real router and firewall to add those routes to it in order for me to be able to interact with that network.  If those routes are not in the current production router then I cannot ping or talk to any of the current servers and workstations as they don't know how to get to whatever my subnets are setup to be.
 
It was a week long struggle to get the 172.17 or 18 or 19 subnets added to the router.  Once I did - everything came on like a light switch had been flipped.
 
But, if I change my subnets to be 172.17.x.x/16 (and 18 and 19) - does that remove the network overlap?  I checked using an online subnet calculator and indicates that it does.  If that is the case, and the overlap is removed so long as I use 172.16/16, 172.17/16 etc., then what I have now is working as I said above.
 
I changed the subnets to be as listed in the paragraph just above this one.  And, everything except Windows sharing/browsing is working at this point.
 
Thanks again for all your help and time!
 
Mark

---

### Post by gmargo on 2011-01-26
> **mips said:**
> 
172.16.200.125/16 overlaps all the other networks listed below.

172.17.1.0/24
172.18.1.0/24
172.19.1.0/24


Where is the overlap?
```

    ip/mask                     network range
-----------------          ---------------------------
172.16.200.125/16          172.16.0.0 - 172.16.255.255
172.17.1.0/24              172.17.1.0 - 172.17.1.255
172.18.1.0/24              172.18.1.0 - 172.18.1.255
172.19.1.0/24              172.19.1.0 - 172.19.1.255

```

---

### Post by mips on 2011-01-26
> **gmargo said:**
> Where is the overlap?
```

    ip/mask                     network range
-----------------          ---------------------------
172.16.200.125/16          172.16.0.0 - 172.16.255.255
172.17.1.0/24              172.17.1.0 - 172.17.1.255
172.18.1.0/24              172.18.1.0 - 172.18.1.255
172.19.1.0/24              172.19.1.0 - 172.19.1.255

```

Quite correct, looking at it now. Dunno how I figured there is an ovelap :redface:

Somehow my mind starting counting one octet earlier, sigh, I'm getting old.

---

### Post by dmshade3 on 2011-01-26
So, now that the ip overlap is out of the way....  Is routing everything except windows share/browsing (and even doing dhcp-relay across the subnets) as good as it will get?  Or, is it really possible to enable windows sharing/browsing across subnets using linux (ubuntu) as the router?

Thanks,

Mark

PS - the answer is 42

---

### Post by chaonis on 2011-10-17
delete please. sorry

---

