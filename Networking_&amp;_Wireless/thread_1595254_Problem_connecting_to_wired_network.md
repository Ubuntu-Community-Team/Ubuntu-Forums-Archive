---
title: "Problem connecting to wired network"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by Jacdeb6009 on 2010-10-13
Hi there,

I have been running 10.04 now for about three months and I have had no problems.  Everything worked "out of the box".  Both the wired and wireless network connections worked flawlessly from home and in the office.

Since last Thursday (07.10.10) I have had problems connecting to the wired network in our office (no wireless available).  Both the wired and wirelss network at home still work without any problems.

The office set up uses DHCP, meaning that there is really nothing to set up.  It simply worked.  Since Thursday morning, however, my notebook will connect to the network and grab an IP address from the server, but it does not see anything beyond the gateway.

If I ping anything outside the office network, I get the following response:

```
ping gandalf@gandalf-laptop:~$ ping 8.8.8.8
connect: Network is unreachable

```While pinging the gateway is fine :

```
gandalf@gandalf-laptop:~$ ping 10.9.200.1
PING 10.9.200.1 (10.9.200.1) 56(84) bytes of data.
64 bytes from 10.9.200.1: icmp_seq=1 ttl=255 time=3.44 ms
64 bytes from 10.9.200.1: icmp_seq=2 ttl=255 time=0.241 ms
^C
--- 10.9.200.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.241/1.841/3.441/1.600 ms

```Using the route command yields the following:

```
gandalf@gandalf-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.9.200.0      *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
gandalf@gandalf-laptop:~$ 
```I have found a work around by simply setting a static IP with the corresponding gateway, subnet mask, DNS and search server IPs and this works perfectly.  It is not a problem as selecting a different network connection in 10.04 simply means clicking on the connection and it is active.

None of the Windows machines in the office (all XP) have this problem at all.

I have checked that this is not a "duplicate IP" problem, but it is not.  If I use the IP that the server offers as a "static" address, all is good.

I have checked this problem also by running the Live CD and by doing a clean (un updated) install on an external hard drive.  Both of these situations have the same network problem.

I will also check this against a different distro, but this more out of interest than anything else.

The question then is, what has caused this problem?  Our network administrator swears that nothing has been changed on the network (and certainly the nothing has been changed on any of the Windows machines).

While my computer is perfectly usable as it is, I am mystified as to what caused this to happen.

Any ideas would be most welcome!

Cheers,

---

### Post by Peter09 on 2010-10-13
Looks to me as though you are not seeing the default gateway. Are you seeing other windows machine on the network?

---

### Post by Jacdeb6009 on 2010-10-13
> **Peter09 said:**
> Looks to me as though you are not seeing the default gateway. Are you seeing other windows machine on the network?

Yes, for whatever reason, the machine does not see the gateway, although I can "ping" it.  No, the machine does not see any other machines on the network, but this has always been the case.

I use the network for two things only (1) to access networked printers and (2) the internet and Lotus Notes.  This has, however, always been the case, except that now this does not want to work unless I assign the machine a static IP address.

Connecting to the server for data occess or other machines is something that I have never been able to get to work, but is not critical to me.

The main issue is that up until last Thursday it worked "automatically" and now it does not.

*** Edit ***   
About the office network.  I work as a consultant (not IT :) ) and the office is a rep office in Hanoi.  I use this as a base.  The office network is used by the handful of people who are permanently in the office.  There are only a few of us working here, and generally we work from the client's offices (whoever and wherever that may be).  This is why connecting to the network "proper" and other machines is not an issue to me.  It would be nice to get this sorted, but it is partly a language thing.  The office is small and IT services are provided by a small local company.  Their support tech. does not speak any English and my Vietnamese is insufficient to explain to him what I need (also he has zero knowledge about Linux).  Our infrastructure support (and also Notes support) is out of Singapore.  This is pretty good, but not useful for setting up access to the server for general use.  Hope that clarifies a bit.

Also, the company firmly refuses to support Linux (this from a Finnish company, ironic :D), meaning that I am more or less on my own in this regard.  Having said this, I have been using Linux pretty successfully for about 90% of what I do for more than three years now.
*** Edit ***

Cheers,

---

### Post by Peter09 on 2010-10-13
When you right click on the network icon you are given the option the edit connections. You should be able to insert the default gateway for the network by editing the IPV4 settings for the office network.

---

### Post by Peter09 on 2010-10-13
To get further functionality make sure samba is installed and also install winbind. This should help you to see the Office machines.

---

### Post by Jacdeb6009 on 2010-10-13
Hi there Peter09,

Thanks for replying.

About setting the default gateway, if I edit the connection, and I select "IPv4 settings" I have a couple of choices.  One is to change the Automatic (DHCP), this I have done to create a working connection (I actually created a second connection called "Eth0_Office"), another is to insert a "route".  Using this option ("routes") would allow me to add the gateway, but it insists on having and address as well.  I have created a test connection and entered the required information (address, netmask and gateway). Selecting this connection has the same result as the default "Auto_eth0" connection (which used to work before...)

I spoke to our IT support tech in Singapore yesterday and he seems to think that the problem may be somehow related to the CISCO Pix firewall / NAT that is installed on our network, but he is not clear on what the problem could be.  He says that there were some changes made to the system on Wednesday of last week, but cannot see that this would have created a problem (he is also not quite clear on exactly what these changes were).

What still confuses me is the fact that none of the Windows machines have this problem and no changes were made to these machines (the local support guy has not been in this office for over a week and the Windows machines have not been accessed remotely by our Singapore IT tech).  :confused: :confused:

About access to the other machines on the network, I will play around with this a bit to see whether I can get it to work, but as I said in my reply of yesterday, this is of lesser importance and interest to me.

Anyway, thanks for you interest in trying to help resolve this one.  To me it is more a matter of personal interest to understand the problem than it is a handicap in working as I have got a working connection (albeit it using a manually assigned IP address).

Cheers!

---

### Post by Jacdeb6009 on 2010-10-18
Hi there,

After some testing and disucssion with out IT tech. in Singapore, it appears that the Cisco Pix unit that we have is "misbehaving".  The problem has been solved by moving the DHCP server back to the Windows server.

This has solved the problem. :)

Cheers,

---

