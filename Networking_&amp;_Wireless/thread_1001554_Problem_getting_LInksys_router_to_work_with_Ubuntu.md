---
title: "Problem getting LInksys router to work with Ubuntu"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by ballsingtripp on 2008-12-04
Hello

I've been using Ubuntu for about a month (on and off with OSX), so I have no idea what I'm doing. I've never had to deal with networking problems in Ubuntu, since everything was just automatically set up connecting my modem directly to the PC's onboard ethernet port.

I have a Linksys WRT54G2 router that I'd like to use with the Ubuntu PC and my Macbook (both wired connections). Wireless would be a plus, but isn't completely necessary at this point. If I connect my modem to the router and the router to the Ubuntu PC, it says I'm connected (on "Auto eth0") but I can't access any sites. I've tried to create new configurations in Network Connections and messed with them a bit, but I don't really know what info to enter (for MAC address, DNS servers and IP if I need to do it manually, etc.).

I've Googled and searched this forum for a solution for the past 2 hours and still can't figure it out..so sorry for the noob question. Please keep in mind that I have absolutely no experience if you post..

Thanks in advance.

-dk

---

### Post by madverb on 2008-12-04
Can you paste the print out of ifconfig

---

### Post by superprash2003 on 2008-12-04
yea, go to the terminal and type ifconfig and post output

---

### Post by ballsingtripp on 2008-12-04
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:01:50:4a  
          inet addr:192.168.1.44  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe01:504a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48174004 (48.1 MB)  TX bytes:4331341 (4.3 MB)
          Interrupt:16 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4000 (4.0 KB)  TX bytes:4000 (4.0 KB)

---

### Post by superprash2003 on 2008-12-05
post output of following
1)cat /etc/resolv.conf
2)ping 72.14.205.100

---

### Post by ballsingtripp on 2008-12-05
Did you want the output of ifconfig and the other two when I'm connected directly to the modem or connected through the router?

---

### Post by kevdog on 2008-12-05
Looks like a route problem or a DNS problem.

---

### Post by gpsmikey on 2008-12-05
In general, the DNS address should be set to point at the router (which says "beats me" and forwards the DNS request to the real DNS servers that it knows about (given to it by your ISP on the wan side)).  From your IP of 192.168.1.44, I am assuming your router should be at 192.168.1.1 - you should be able to log into the router and check the status etc (this also verifies you are talking to it).

mikey

---

### Post by ballsingtripp on 2008-12-06
Connected (but not being able to load sites) with the router, I can type 192.168.1.1 in firefox and get to the router settings. Here's the output of ifconfig when connected through the router (I think the last one I posted might've been while it was connected directly to the modem):

eth0      Link encap:Ethernet  HWaddr 00:e0:4d:01:50:4a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe01:504a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3945732 (3.9 MB)  TX bytes:597373 (597.3 KB)
          Interrupt:16 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:660 (660.0 B)  TX bytes:660 (660.0 B)


And here are the router settings @192.168.1.1:

Automatic Configuration (DHCP)

Router Name: WRT54G2	
Host Name: (empty)		  	
Domain Name: (empty)	  	 
MTU: Auto	  	 
Size: 1500

Local IP Address: 192.168.1.1
Subnet Mask: 225.225.225.0

DHCP Server: Enable
Starting IP Address: 192.168.1.100
Maximum Number of DHCP Users: 50
Client Lease Time: 0
Static DNS 1: 0.0.0.0
Static DNS 2: 0.0.0.0
Static DNS 3: 0.0.0.0
Static DNS 4: 0.0.0.0
WINS: 0.0.0.0

MAC Address Clone: Disable

Firewall:
Block Anonymous Internet Requests [checked]
Filter Multicast [checked]
Filter Internet NAT Redirection [not checked]
Filter IDENT(Port 113) [checked]

VPN:
IPSec Passthrough: Enable
PPTP Passthrough: Enable
L2TP Passthrough: Enable	



Here is the output of cat /etc/resolv.conf:
# Generated by NetworkManager
domain myhome.westell.com
search myhome.westell.com
nameserver 192.168.1.1



And the output of ping 72.14.205.100:
PING 72.14.205.100 (72.14.205.100) 56(84) bytes of data.



When messing around in Network Configuration, should I be working under Wired or DSL?

---

### Post by madverb on 2008-12-06
DHCP Server: Enable
Starting IP Address: 192.168.1.100
Maximum Number of DHCP Users: 50
Client Lease Time: 0
Static DNS 1: 0.0.0.0

Maybe you should set a static DNS to your ISP's DNS server

---

### Post by gpsmikey on 2008-12-06
You don't indicate what the results of the ping to the outside address was -- did it time out or complete?

One thing that comes to mind here - if you just connect a router (or some other device for that matter) to your modem and don't cycle power on both the router and modem, they will often not talk.  If you have not done that, with the router connected to the modem, turn them both off, wait for 30 seconds or so and turn them back on again.

mikey

---

### Post by ballsingtripp on 2008-12-08
gpsmikey, I guess I didn't wait for the ping results before, but I tried it again and it outputs the following:


PING 72.14.205.100 (72.14.205.100) 56(84) bytes of data.
ping: sendmsg: Network is unreachable [repeats this about 50 times]
^C
--- 72.14.205.100 ping statistics ---
530 packets transmitted, 0 received, 100% packet loss, time 529200ms


I've tried power cycling the router and modem, both by using the reset buttons and turning them off and on..still the same problem. I also tried going into Network Configuration and editing Auto eth0..under IPv4 Settings I changed the method to Automatic (DHCP) addresses only and the DNS Server to 192.168.1.1..I restarted my modem and router and nothing changed.

madverb, I have no idea what my ISP's DNS server is, and I can't call Verizon because they offer no Linux support at all...I tried setting a static DNS to 192.168.1.44 and restarted everything and nothing changed. Not sure what I was trying to do, but it didn't work. I set the static DNS back to 0.0.0.0.

This router seems so dependent on its firmware in Windows..can't figure out how to manually configure any of this.

---

### Post by madverb on 2008-12-09
Set the DNS server to the routers IP

---

### Post by ballsingtripp on 2008-12-09
Isn't that what I did here:

> **ballsingtripp said:**
> I also tried going into Network Configuration and editing Auto eth0..under IPv4 Settings I changed the method to Automatic (DHCP) addresses only and the DNS Server to 192.168.1.1..I restarted my modem and router and nothing changed.


---

### Post by ianhaycox on 2008-12-09
You could try the OpenDNS servers for your DNS if you don't know your ISP's

nameserver 208.67.222.222
nameserver 208.67.220.220


Either set them in the router or your desktop.

---

### Post by gpsmikey on 2008-12-09
If you can get to the router config pages (which you say you can), then your local network is working and you are on the same subnet as the router.  That is good.  What it sounds like is missing is the "gateway" address - usually, that should also be pointed at the router (192.168.1.1).  DNS has nothing to do with the issue if you are pinging an IP outside of your LAN and get the "Network is Unreachable" response since DNS is not used to resolve the IP.  

As far as the router "being dependant on windows", I have not used the WRT54G2, but I do use the WRT54G all the time and I NEVER use any of their windows config software or any of that stuff.  I just go into the router config pages and set up what I want.  Windoze is not involved.  If you look through the users manual for the G2, you can see what all the configuration stuff is.  Make sure you have the gateway set up to point at the router and you should be able to ping outside your LAN.  Then you can see if DNS is a problem (DNS gets involved when you are trying to ping [www.amazon.com](www.amazon.com) for example - DNS is used to resolve that to an IP address).

mikey

---

