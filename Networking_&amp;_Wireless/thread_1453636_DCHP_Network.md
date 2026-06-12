---
title: "DCHP Network"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by synoptic on 2010-04-13
Hello,
I'm completly new to setting up a network and I have some problems getting it done.
 
Hardware
ethernet eth0 Connected to Static ip 95.xxx.xxx.xxx
ethernet eth1 Not connected
 
I have ubuntu 9.10 clean install
I installed dhcp3-server
 
What do I need
I need to have a DHCP server that can make new ip addresses to linked computers prefered ip range 192.168.3.10 192.168.3.250
All those addresses need to be able to use my eth0 ip address for connecting to the internet.
 
Any one has an idea how I can set this all up.
 
Thanks,
Marcel

---

### Post by Iowan on 2010-04-13
You will need to give eth1 a static address in the 192.168.3.X subnet (outside your DHCP range). Then, you'll need to set up DHCP range in */etc/dhcp3/dhcpd.conf*. I'm going by (poor) memory - I switched to DNSMasq for DHCP/DNS server.
Perhaps [this]("https://help.ubuntu.com/9.10/serverguide/C/dhcp.html") help page will be more helpful...

---

### Post by synoptic on 2010-04-14
What ever I do I keep getting the error chack syslog for diagnostics.
If I check that I see no subnet for eth1 (0.0.0.0)
 
This is what I set;
 
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.3.10;
option routers 192.168.3.9;
option domain-name-servers 192.168.3.1, 192.168.3.2;
option domain-name "mydomain.com";

subnet 192.168.3.0 netmask 255.255.255.0 {
range 192.168.3.10 192.168.3.100;
} 

What am I doing wrong???

---

### Post by Iowan on 2010-04-14
Have you set up an IP address for eth1? Is this a server install - or is eth1 supposed to get an address via Network Manager? **ifconfig -a** should show interfaces and addresses.

---

### Post by synoptic on 2010-04-15
Looks like eth1 is still not setup with an IP address.
 
Where can I set this up looks like (System/Preferences/Network Connections) is not doing this right. I did set eth1 there but on ifconfig no show.

---

### Post by synoptic on 2010-04-15
I chanched to dnsmasq and trying to configure that right now.
If you know what I need to set please tell me.
 
Thanks,

---

### Post by synoptic on 2010-04-15
Hello,
 
I did go true some webpages about dnsmasq but looks like my knowledge and english are poor. I do not understand how to set it all up.
 
I did install dnsmasq but what now?
 
I have eth0 that is linked by the router ip 95.97.xxx.xxx (static)
 
I want use my eth1 as dhcp for my home network using ip 168.192.3.10
And all other hardware I connect getting a ip in the range 168.192.3.50, 168.192.3.200
 
Offcourse all computers must be able to have internet connection using eth0 for it.
 
I realy hope your willing to help me out and tell me what to set in what *.conf file, because I get dissy on reading all and not understanding it.
 
Thanks,
Marcel

---

### Post by Iowan on 2010-04-15
> **synoptic said:**
> 
I realy hope your willing to help me out and tell me what to set in what *.conf file, because I get dissy on reading all and not understanding it.
I'm willing to help - I hope I don't make things worse...
> **Iowan said:**
> Is this a server install - or is eth1 supposed to get an address via Network Manager? First task will be to get eth1 an address in the 192.168.3.0 subnet.
 If you have a server install, there will be no Network Manager unless you installed it. A desktop defaults to using Network Manager unless you change it.

---

### Post by synoptic on 2010-04-15
It's no server install just a regular ubuntu 9.10

---

### Post by Iowan on 2010-04-15
You should be able to set up a manual IP address for eth1 in Network Manager. Set it to "Connect Automatically". [This]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%209.10%20Method") help page has a section for sharing the connection (that comes later...). 
It just occurred to me - even if we can set an address for eth1 this way, we may still want to manually configure via */etc/network/interfaces*. Network Manager seems to configure interfaces at login - so the machine will need a logged-in user to work. To make */etc/network/interfaces* work properly, we *might* need to uninstall NM (I shudder to suggest it - since sometimes it's hard to get back).

---

### Post by synoptic on 2010-04-16
We can do what ever it takes if I know all steps and what to do where I can make a clean install again and redo all.
 
I set eth1 to automatic (DHCP)
 
I did setup de gateway according to the link you have in your reply.
I configured the eth1, I enabled routing and added ipv4 forwarding to the /etc/sysctl.conf file.
 
So what can I do next?
 
Greetings,
Marcel

---

### Post by Iowan on 2010-04-19
I just learned that the [available to all users]("http://ubuntuforums.org/showthread.php?p=9146044#post9146044") option makes NM configure the interface at bootup - rather than login!

I might as well tack in [this]("http://ubuntuforums.org/showthread.php?p=9144235#post9144235") link about starting DHCP server at startup.

---

### Post by synoptic on 2010-04-25
Thanks for all the help but it;s fixed by using this website;
 
[https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%209.10%20Method](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%209.10%20Method)
 
Exelent how to.
 
Greetings,
Marcel

---

### Post by NichoTL on 2010-04-25
I know you fixed it but I hope you understand that because eth1 will dish out DHCP addresses it can't be set (in Network Manager or via the command line) to receive its address via DHCP. You have to specify the address for eth1 manually, along with the right subnet, because the DHCP server (that you set up) needs to know what to send to the other computers as a default gateway.

---

