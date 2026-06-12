---
title: "Network settings lost when cable is unplugged/plugged in."
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by jmickela on 2010-09-18
Running /etc/init.d/networking restart restores my connection, but the moment a cable is removed or added I either lost my networking settings, or they get changed to something else. The settings in /etc/network/interfaces are correct, and are what's loaded when the networking script runs.

What could be causing this?

---

### Post by jmickela on 2010-09-21
Bump

Every time my wireless router goes down my networking settings are all lost. Since this is on a server that doesn't have a monitor attached this is pretty annoying.

---

### Post by redmk2 on 2010-09-21
> **jmickela said:**
> Bump

Every time my wireless router goes down my networking settings are all lost. Since this is on a server that doesn't have a monitor attached this is pretty annoying.

So what are the settings in /etc/network/interfaces ?

Your title says *"lost when cable is unplugged/plugged in"*.  Are your connections to this server wireless or cabled?

---

### Post by jmickela on 2010-09-21
Below is my interfaces file.
```
auto lo eth3 eth2
iface lo inet loopback


iface eth2 inet static
	address 90.0.0.1
	netmask 255.255.255.0
	broadcast 90.0.0.255
	network 90.0.0.0
	up ip route add 192.168.1.0/24 via 173.11.124.93

iface eth3 inet static
	address 173.11.124.93
	netmask 255.255.255.0
	broadcast 173.11.124.255
	network 173.11.124.0
	gateway 173.11.124.94
	up ip route add 173.11.124.93/32 via 173.11.124.94
```

The specific problem is that eth2 isn't being set up when its connection state changes (cable unplugged/plugged in). 

All the connections are wired; right now the internet comes in through a cable box, goes in to the server, which is then connected to a wireless router which connects to the computers in the office. Sometimes  the wireless router needs to be rebooted, when that happens the server loses its network settings.

simply running /etc/init.d/networking restart
fixes the issue, however I'd rather not have to connect a keyboard and monitor to the server if I don't have to.

---

### Post by redmk2 on 2010-09-21
> **jmickela said:**
> Below is my interfaces file.
```
auto lo eth3 eth2
iface lo inet loopback


iface eth2 inet static
	address 90.0.0.1
	netmask 255.255.255.0
	broadcast 90.0.0.255
	network 90.0.0.0
	up ip route add 192.168.1.0/24 via 173.11.124.93

iface eth3 inet static
	address 173.11.124.93
	netmask 255.255.255.0
	broadcast 173.11.124.255
	network 173.11.124.0
	gateway 173.11.124.94
	up ip route add 173.11.124.93/32 via 173.11.124.94
```

Are you sure about the gateway configurations?  I'm aware this ISP uses a strange gateway setup.
> 
The specific problem is that eth2 isn't being set up when its connection state changes (cable unplugged/plugged in).

Do we know for sure that the interface is disabled?  Earlier you commented: *"either lost my networking settings, or they get changed to something else"*. Can you verify that eth2 ** has lost its configuration **when disconnected?  Could we just have a *down interface* with the correct configuration?
> 
All the connections are wired; right now the internet comes in through a cable box, goes in to the server, which is then connected to a wireless router which connects to the computers in the office. 
What is the reason for eth3?  Is this host a gateway too?  What are you trying to achieve here?  A picture is worth a 1000 words.  Can you provide a diagram?  Pretty is not important.  Just draw it out and then scan the drawing as a JPG.> 
Sometimes  the wireless router needs to be rebooted, when that happens the server loses its network settings.
Hmmmm, that seems unusual.  By your description, it sounds like the wireless router is downstream of eth2.> 

Simply running /etc/init.d/networking restart
fixes the issue, however I'd rather not have to connect a keyboard and monitor to the server if I don't have to.
A convenient work around for right now is to ssh to the server and run the restart command.  No need of a local keyboard, mouse or video.

---

### Post by jmickela on 2010-09-22
I've attached a simple diagram of my network.

I can't SSH to the server since it no longer has a valid network configuration.

From what I can tell, what happens is that eth2, at the very least, doesn't get an ip address assigned to it, or if it has one it is removed when the connection status changes. Because of this the entire internal network doesn't work, but the server still has internet access because eth3 is still functional.

---

### Post by redmk2 on 2010-09-22
> **jmickela said:**
> I've attached a simple diagram of my network.

Not very conventional though.  I assume that the server has been setup as a router (gateway).  Is this correct? Why is there a need for the manual route on both interfaces?  

What is the reason for using the 90.0.0.0/24 network? Why not use NAT (private addressing)?  The 90.0.0.0/8 (all of 90.0.0.0) should not be used for private networking. These are public IP addresses owned by RIPE.net in Holland.  See below.```
**[COLOR="Red"]NetRange:       90.0.0.0 - 90.255.255.255[/COLOR]**
CIDR:           90.0.0.0/8
OriginAS:       
NetName:        90-RIPE
NetHandle:      NET-90-0-0-0-1
Parent:         
NetType:        Allocated to RIPE NCC
NameServer:     TINNIE.ARIN.NET
NameServer:     SUNIC.SUNET.SE
NameServer:     NS-PRI.RIPE.NET
NameServer:     SEC3.APNIC.NET
NameServer:     NS2.LACNIC.NET
NameServer:     SEC1.APNIC.NET
Comment:        These addresses have been further assigned to users in
Comment:        the RIPE NCC region. Contact information can be found in
Comment:        the RIPE database at http://www.ripe.net/whois
RegDate:        2005-06-30
Updated:        2009-05-18
Ref:            http://whois.arin.net/rest/net/NET-90-0-0-0-1

OrgName:        RIPE Network Coordination Centre
OrgId:          RIPE
Address:        P.O. Box 10096
City:           Amsterdam
``` As an aside, RIPE uses funny gateway configuration for their networks.  That's why I did not question your gateway configuration at first. > 

I can't SSH to the server since it no longer has a valid network configuration.


Can you post the output of ***ifconfig*** and ***route -n*** obtained form the Server when the wireless goes down.  
> 

From what I can tell, what happens is that eth2, at the very least, doesn't get an ip address assigned to it, or if it has one it is removed when the connection status changes. Because of this the entire internal network doesn't work, but the server still has internet access because eth3 is still functional.

We don't really know, do we?  You may have to connect a monitor and keyboard for a while.  :-(

---

