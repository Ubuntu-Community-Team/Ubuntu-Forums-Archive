---
title: "static IP not working on UBUNTU 12.04.2 LTS server install"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by n8nt on 2013-05-18
I installed the latest version (32-bit) of Ubuntu Server.

My server is a 1-u SuperMicro server from 2003 and has been running Windows (flawlessly) since November of 2003. But now I'm in a new job which uses Linux and Java rather than Windows and .NET so I want to re-familiarize myself with Linux. I had set up a UBUNTU box a couple of years ago so decided I want to do that again.

My server has two ethernet ports. From my cable modem I go to a netgear switch. From that switch I go directly to eth0 on my server box. Also from the switch I go to a netgear router. From one of the outputs of the router I go to eth1 on my server box. My cable company, WOWWAY, sells me one static ip address at 65.60.189.59 which I have configured to be the first NIC on the server box. It was working on the Windows OS for quite a while.

After installing UBUNTU on my server I checked the interfaces file in /etc/network and made it look like the following:

[COLOR=#0000ff]# This file describes the network interfaces available on your system[/COLOR]
[COLOR=#0000ff]# and how to activate them. For more information, see interfaces(5).[/COLOR]
[COLOR=#0000ff]
[/COLOR]
[COLOR=#0000ff]# The loopback network interface[/COLOR]
[COLOR=#0000ff]auto lo[/COLOR]
[COLOR=#0000ff]iface lo inet loopback[/COLOR]
[COLOR=#0000ff]
[/COLOR]
[COLOR=#0000ff]# The primary network interface[/COLOR]
[COLOR=#0000ff]auto eth0[/COLOR]
[COLOR=#0000ff]iface eth0 inet static[/COLOR]
[COLOR=#0000ff]address xx.xx.xx.xx[/COLOR]
[COLOR=#0000ff]netmask 255.255.248.0[/COLOR]
[COLOR=#0000ff]gateway xx.xx.xx.1[/COLOR]
[COLOR=#0000ff]broadcast xx.xx.xx.255[/COLOR]
[COLOR=#0000ff]dns-nameservers xx.xx.xx.2 xx.xx.xx.7[/COLOR]
[COLOR=#0000ff]#[/COLOR]
[COLOR=#0000ff]#[/COLOR]
[COLOR=#0000ff]auto eth1[/COLOR]
[COLOR=#0000ff]iface eth1 inet dhcp

[/COLOR]I also have installed open ssh on this server. I can ssh into it from my local network (i.e., from 192.168.1.54) but I cannot connect using the static IP. I tried going to another computer (out of my home) and tried to ssh into my xx.xx.xx.xx box  using the static address but again I get no connection.

If I change the interfaces file to this:[COLOR=#0000ff]

[/COLOR][COLOR=#0000FF]# This file describes the network interfaces available on your system[/COLOR]
[COLOR=#0000FF]# and how to activate them. For more information, see interfaces(5).[/COLOR]
[COLOR=#0000FF]
[/COLOR]
[COLOR=#0000FF]# The loopback network interface[/COLOR]
[COLOR=#0000FF]auto lo[/COLOR]
[COLOR=#0000FF]iface lo inet loopback[/COLOR]
[COLOR=#0000FF]
[/COLOR]
[COLOR=#0000FF]# The primary network interface[/COLOR]
[COLOR=#0000FF]auto eth0[/COLOR]
[COLOR=#0000FF]iface eth0 inet dhcp[/COLOR]


[COLOR=#0000FF]#[/COLOR]
[COLOR=#0000FF]#[/COLOR]
[COLOR=#0000FF]auto eth1[/COLOR]
[COLOR=#0000FF]iface eth1 inet dhcp

[/COLOR]Then I am able to get things to work on the static and dhcp addresses.

Any thoughts? I would really like to be able to use my SSH on the static address so I don't have to use something like dyndns (and not sure that even works on LINUX)

Hoping for some help...
[COLOR=#0000ff]

[/COLOR]

---

### Post by redmk2 on 2013-05-18
> **n8nt said:**
> I installed the latest version (32-bit) of Ubuntu Server.

My server is a 1-u SuperMicro server from 2003 and has been running Windows (flawlessly) since November of 2003. But now I'm in a new job which uses Linux and Java rather than Windows and .NET so I want to re-familiarize myself with Linux. I had set up a UBUNTU box a couple of years ago so decided I want to do that again.

***My server has two ethernet ports. From my cable modem I go to a netgear switch. From that switch I go directly to eth0 on my server box. ***
Which I assume is configured for the IP address that WOWWAY assigned you.  Is this correct?> 
Also from the switch I go to a netgear router. From one of the outputs of the router I go to eth1 on my server box.
Is this the IP address in the 192.168.1.0 /24 network?  This is assigned by DHCP.  Did you reserve this address via MAC address?> 
 My cable company, WOWWAY, sells me one static ip address at 65.60.189.59 which I have configured to be the first NIC on the server box. It was working on the Windows OS for quite a while.

After installing UBUNTU on my server I checked the interfaces file in /etc/network and made it look like the following:

[COLOR=#0000ff]# This file describes the network interfaces available on your system[/COLOR]
[COLOR=#0000ff]# and how to activate them. For more information, see interfaces(5).[/COLOR]
[COLOR=#0000ff]
[/COLOR]
[COLOR=#0000ff]# The loopback network interface[/COLOR]
[COLOR=#0000ff]auto lo[/COLOR]
[COLOR=#0000ff]iface lo inet loopback[/COLOR]
[COLOR=#0000ff]
[/COLOR]
[COLOR=#0000ff]# The primary network interface[/COLOR]
[COLOR=#0000ff]auto eth0[/COLOR]
[COLOR=#0000ff]iface eth0 inet static[/COLOR]
[COLOR=#0000ff]address xx.xx.xx.xx[/COLOR]
[COLOR=#0000ff]netmask 255.255.248.0[/COLOR]
[COLOR=#0000ff]gateway xx.xx.xx.1[/COLOR]
[COLOR=#0000ff]broadcast xx.xx.xx.255[/COLOR]
[COLOR=#0000ff]dns-nameservers xx.xx.xx.2 xx.xx.xx.7[/COLOR]
[COLOR=#0000ff]#[/COLOR]
[COLOR=#0000ff]#[/COLOR]
[COLOR=#0000ff]auto eth1[/COLOR]
[COLOR=#0000ff]iface eth1 inet dhcp

[/COLOR]I also have installed open ssh on this server. I can ssh into it from my local network (i.e., from 192.168.1.54) but I cannot connect using the static IP. I tried going to another computer (out of my home) and tried to ssh into my xx.xx.xx.xx box  using the static address but again I get no connection.

From the terminal of the server, can you reach the Internet at all with eth1 disconnected?   Did WOWWAY give you the IP settings (subnet mask and gateway)?  Can you ping the server from itself (65.60.189.59)?> 

If I change the interfaces file to this:[COLOR=#0000ff]

[/COLOR][COLOR=#0000FF]# This file describes the network interfaces available on your system[/COLOR]
[COLOR=#0000FF]# and how to activate them. For more information, see interfaces(5).[/COLOR]
[COLOR=#0000FF]
[/COLOR]
[COLOR=#0000FF]# The loopback network interface[/COLOR]
[COLOR=#0000FF]auto lo[/COLOR]
[COLOR=#0000FF]iface lo inet loopback[/COLOR]
[COLOR=#0000FF]
[/COLOR]
[COLOR=#0000FF]# The primary network interface[/COLOR]
[COLOR=#0000FF]auto eth0[/COLOR]
[COLOR=#0000FF]iface eth0 inet dhcp[/COLOR]


[COLOR=#0000FF]#[/COLOR]
[COLOR=#0000FF]#[/COLOR]
[COLOR=#0000FF]auto eth1[/COLOR]
[COLOR=#0000FF]iface eth1 inet dhcp

[/COLOR]Then I am able to get things to work on the static and dhcp addresses.

What is the IP address on eth0 when you use DHCP?
> 

Any thoughts? I would really like to be able to use my SSH on the static address so I don't have to use something like dyndns (and not sure that even works on LINUX)

Hoping for some help...
[COLOR=#0000ff]

[/COLOR]
If you have a static IP address from WOWWAY you should be able to ssh to the host with no problems.  You do need to have Firewall protection for a public facing IP address.  Do you have that configured.

---

### Post by n8nt on 2013-05-19
> **redmk2 said:**
> Which I assume is configured for the IP address that WOWWAY assigned you.  Is this correct?

Yes. 

Is this the IP address in the 192.168.1.0 /24 network? 
 
Yes.

This is assigned by DHCP.  Did you reserve this address via MAC address?

Agreed; the 192.168.1.4 address is assigned by the Netgear Router. No, this was not an address that was reserved. However, the 65.60.189.59 address was assigned to the mac address on the server. I just called wowway and had them verify that.


From the terminal of the server, can you reach the Internet at all with eth1 disconnected? only if the eth0 is set up as dhcp. If I set it to static, then no.
  
Did WOWWAY give you the IP settings (subnet mask and gateway)? 
yes
Can you ping the server from itself (65.60.189.59)?
yes

What is the IP address on eth0 when you use DHCP?
It is a different. I also noticed that the network mask comes up wrong - it comes up as 255.255.224.0 but wowway said it should be 255.255.248.0.

If you have a static IP address from WOWWAY you should be able to ssh to the host with no problems.  You do need to have Firewall protection for a public facing IP address.  Do you have that configured.

I checked and there is no firewall configured on the UBUNTU server. 

I am not going thru my router to the server when using the static ip address since it comes directly from the switch (before the router) so I don't have to worry about the firewall in the router either.



I ALSO noticed that when I boot the machine from a power up event that I see the following three lines:

Stopping Mount network file systems.
Waiting for network configuration.
Waiting up to 60 more seconds for network configuration

It will sit there for a while on the first waiting, then for at least 60 seconds on the second. Then it starts up.

I am about to give up and install the DeskTop version to see if that one will work.

ONE OTHER QUESTION: Can I have eth0 configured as static and eth1 configured as DHCP? That's what I'm trying. I assume that is ok. However, maybe I can answer that myself since I did disconnect eth1 and still have the same problems.

---

### Post by redmk2 on 2013-05-19
> **n8nt said:**
> I ALSO noticed that when I boot the machine from a power up event that I see the following three lines:

Stopping Mount network file systems.
Waiting for network configuration.
Waiting up to 60 more seconds for network configuration

It will sit there for a while on the first waiting, then for at least 60 seconds on the second. Then it starts up.

I am about to give up and install the DeskTop version to see if that one will work.

ONE OTHER QUESTION: Can I have eth0 configured as static and eth1 configured as DHCP? That's what I'm trying. I assume that is ok. However, maybe I can answer that myself since I did disconnect eth1 and still have the same problems.

[COLOR="#0000FF"]Edit:  The below is edited after @Doug_S's excellent catch. [/COLOR]
It's not at all clear what your settings are or are supposed to be,  The IP address 65.60.189.59 with a subnet mask of 255.255.248.0 means that the range of IP addresses is 2048.  This starts at 65.60.184.0 (the Network ID also) and ends at 65.60.191.255 ( the b'cast address).  The default gateway must be in this range.  This means the static configuration for eth0 would be
 ```

auto eth0
iface eth0 inet static
        address 65.60.189.59
        netmask 255.255.248.0
        network 65.60.184.0
        gateway 65.60.184.1 (or something greater up to 65.60.191.254)

```

This also means you potentially are sharing this subnet with someone else since you indicate that you only have control of 1 of the 2000+  IP addresses on this subnet.   You need a firewall on this host.

I'll ask again;  What is the IP address/subnet mask/gateway of the interface eth0 when you configure it to use DHCP?  I'm assuming that the DHCP server is maintained by WOWWAY as you have indicated that your host (the server) is directly connected to the MODEM via a switch.  Is this correct.

You also indicate that you have a router connected to this switch.  What is the IP address/mask/gateway on the WAN side of this device?  This should show the correct gateway for the 65.60.184.0 /21 subnet as both the router (WAN interface) and the server are in the same subnet at this point.

Installing the desktop version of Ubuntu won't gain you anything.  The static addressing would be the same whether you use Network Manager or the same conf files you are using now.

The 2 interfaces are separate from each other and can be configured using different methods as you probably know by now.

---

### Post by Doug S on 2013-05-19
> My server has two ethernet ports. From my cable modem I go to a netgear  switch. From that switch I go directly to eth0 on my server box. Also  from the switch I go to a netgear router. From one of the outputs of the  router I go to eth1 on my server box. My cable company, WOWWAY, sells  me one static ip address at 65.60.189.59 which I have configured to be  the first NIC on the server box.Your setup does not make sense to me. What IP address does your netgear router get? It has to be different than 65.60.189.59. For the public side, I have the same setup as you, but I have two static IP addresses, one used by my Ubuntu server and the other one used by the router. And while I have static public IP addresses, my ISP requires that I still use DCHP to get them.

Yes it is O.K. to have a static IP address on one NIC and a DHCP address on the other.

@redmk2: I had not seen your reply of a few minutes before mine. Note that the netmask implies a sub-net size of 2048 not 8. As far as I know it is common for netmasks given from ISPs to encompass a larger subnet than one client has. In my case my netmask is 255.255.255.0, but I only have two IP addresses, not sequential, but both within the same sub-net.

---

### Post by redmk2 on 2013-05-19
> **Doug S said:**
> ... And while I have static public IP addresses, my ISP requires that I still use DCHP to get them.
The battle rages on. LOL 

Static addressing connotes the use of a configuration file (i.e. interfaces) to configure the addresses.  DHCP means that the address is defined dynamically (via a DHCP server) even if the address is immutable (unchanging).  It is a small point, until you are diagnosing a problem.  ;-)

---

### Post by Doug S on 2013-05-19
> **redmk2 said:**
> The battle rages on. LOL Static addressing connotes the use of a configuration file (i.e. interfaces) to configure the addresses.  DHCP means that the address is defined dynamically (via a DHCP server) even if the address is immutable (unchanging).  It is a small point, until you are diagnosing a problem.Of source you are right. I was referring to what my ISP calls "static" and charges me a bunch of extra money for. Perhaps the OPs ISP requires similar, just a thought.

---

### Post by redmk2 on 2013-05-19
> **Doug S said:**
> 
@redmk2: I had not seen your reply of a few minutes before mine. Note that the netmask implies a sub-net size of 2048 not 8. As far as I know it is common for netmasks given from ISPs to encompass a larger subnet than one client has. In my case my netmask is 255.255.255.0, but I only have two IP addresses, not sequential, but both within the same sub-net.
You are right I thought of the 248 in the last octet.  In that case the gateway would be in the subnet.

Sorry for the misinterpreted subnet mask.

---

### Post by redmk2 on 2013-05-19
> **Doug S said:**
> Of source you are right. I was referring to what my ISP calls "static" and charges me a bunch of extra money for. Perhaps the OPs ISP requires similar, just a thought.

I think we are both trying to understand the topology of the OP's network at this point.  I have followed your posts in the past.  You provide great answers.  The ISP sounds like a cable provider with such big subnets.

---

### Post by n8nt on 2013-05-19
> **redmk2 said:**
> [COLOR=#0000FF]Edit:  The below is edited after @Doug_S's excellent catch. [/COLOR]
It's not at all clear what your settings are or are supposed to be,  The IP address 65.60.189.59 with a subnet mask of 255.255.248.0 means that the range of IP addresses is 2048.  This starts at 65.60.184.0 (the Network ID also) and ends at 65.60.191.255 ( the b'cast address).  The default gateway must be in this range.  This means the static configuration for eth0 would be
 ```

auto eth0
iface eth0 inet static
        address 65.60.189.59
        netmask 255.255.248.0
        network 65.60.184.0
        gateway 65.60.184.1 (or something greater up to 65.60.191.254)

```

This also means you potentially are sharing this subnet with someone else since you indicate that you only have control of 1 of the 2000+  IP addresses on this subnet.   You need a firewall on this host.

I'll ask again;  What is the IP address/subnet mask/gateway of the interface eth0 when you configure it to use DHCP?  I'm assuming that the DHCP server is maintained by WOWWAY as you have indicated that your host (the server) is directly connected to the MODEM via a switch.  Is this correct.

You also indicate that you have a router connected to this switch.  What is the IP address/mask/gateway on the WAN side of this device?  This should show the correct gateway for the 65.60.184.0 /21 subnet as both the router (WAN interface) and the server are in the same subnet at this point.

Installing the desktop version of Ubuntu won't gain you anything.  The static addressing would be the same whether you use Network Manager or the same conf files you are using now.

The 2 interfaces are separate from each other and can be configured using different methods as you probably know by now.

Thanks everyone who replied to this. Had to run to church and then go off and run a bunch of errands but back now and will give you summary of my successful results.

First of all I did change my configuration to use DHCP and then rebooted the machine. When I did that I saw in the ifconfig report:
ip = 65.60.189.59
netmask = 255.255.255.224
broadcast = 65.60.189.63

With that configuration I tried to ping that address from an outside computer. (I use my verizon hotspot connected to my laptop to get a totally isolated internet connection) and when I did this I was able to get a response. I also ran my ssh client on the laptop and was able to connect.

Based on that I changed my interfaces file to the following:
[COLOR=#0000ff]# The loopback network interface[/COLOR]
[COLOR=#0000ff]auto lo[/COLOR]
[COLOR=#0000ff]iface lo inet loopback[/COLOR]
[COLOR=#0000ff]
[/COLOR]
[COLOR=#0000ff]# The primary network interface[/COLOR]
[COLOR=#0000ff]auto eth0[/COLOR]
[COLOR=#0000ff]iface eth0 inet static[/COLOR]
[COLOR=#0000ff]address 65.60.189.59[/COLOR]
[COLOR=#0000ff]netmask 255.255.255.224[/COLOR]
[COLOR=#0000ff]gateway 65.60.189.33[/COLOR]
[COLOR=#0000ff]network 65.60.189.32[/COLOR]
[COLOR=#0000ff]broadcast 65.60.189.63[/COLOR]
[COLOR=#0000ff]dns-nameservers 64.233.222.2 64.233.222.7[/COLOR]
[COLOR=#0000ff]#[/COLOR]
[COLOR=#0000ff]#[/COLOR]
[COLOR=#0000ff]auto eth1[/COLOR]
[COLOR=#0000ff]iface eth1 inet dhcp[/COLOR]

To make a long story short, after seeing the data that the ifconfig reported on my eth0 when I set it up to be DHCP, I could see that it was getting a different netmask and a different broadcast address than what wowway had told me the first time I spoke with them. I had again spoken to wowway yesterday and asked them to confirm that the gateway, netmask and broadcast address that they had given me earlier was in fact correct. They said they "thought" it was correct. When that didn't work and you suggested I try the DHCP to see what resulted, I remembered a while ago when I first got the static ip address that they told me that the gateway was 65.60.189.33 but then said, no, that was wrong and it should be 65.60.160.1.

I'm thinking that they were confused and just gave me the wrong information. That same day we were discussing why my Netgear router was not working. It gets a different netmask, gateway and ip address as is shown here:

[COLOR=#0000ff]ip: 65.60.160.51
netmask: 255.255.248.0
gateway: 65.60.160.1[/COLOR]

Perhaps when I spoke with them they thought I meant that network instead of the one for the static ip.

In the past when I've purchased an IP address from them I get a block of 5 for one price. I'm thinking that wowway must have set aside small blocks like this for reserving ip static addresses. I only bought one. They do ask for the mac address or they ask to connect only to that device so they can pick up the mac address.

By the way, I found a lazy man's site which will calculate the broadcast address of a given ip address and net mask. It will also give you the network address. I assume that the gateway is "usually" the first address after the network address  - which is what I used to verify the gateway for my particular IP address. Here's the link:

 [http://www.tech-faq.com/calculate-broadcast-address](http://www.tech-faq.com/calculate-broadcast-address)

Again, thanks to everyone who responded to my query.
Bob

---

### Post by redmk2 on 2013-05-19
> **n8nt said:**
> Thanks everyone who replied to this. Had to run to church and then go off and run a bunch of errands but back now and will give you summary of my successful results.
I'm guessing all is well now.> 

First of all I did change my configuration to use DHCP and then rebooted the machine. When I did that I saw in the ifconfig report:
ip = 65.60.189.59
netmask = 255.255.255.224
broadcast = 65.60.189.63

With that configuration I tried to ping that address from an outside computer. (I use my verizon hotspot connected to my laptop to get a totally isolated internet connection) and when I did this I was able to get a response. I also ran my ssh client on the laptop and was able to connect.


Yes, this looks better.  There are 30 usable addresses in this subnet.  The range is 65.60.189.32 (Net ID) to 65.60.189.63 (b'cast).
> 

Based on that I changed my interfaces file to the following:
[COLOR=#0000ff]# The loopback network interface[/COLOR]
[COLOR=#0000ff]auto lo[/COLOR]
[COLOR=#0000ff]iface lo inet loopback[/COLOR]
[COLOR=#0000ff]
[/COLOR]
[COLOR=#0000ff]# The primary network interface[/COLOR]
[COLOR=#0000ff]auto eth0[/COLOR]
[COLOR=#0000ff]iface eth0 inet static[/COLOR]
[COLOR=#0000ff]address 65.60.189.59[/COLOR]
[COLOR=#0000ff]netmask 255.255.255.224[/COLOR]
[COLOR=#0000ff]gateway 65.60.189.33[/COLOR]
[COLOR=#0000ff]network 65.60.189.32[/COLOR]
[COLOR=#0000ff]broadcast 65.60.189.63[/COLOR]
[COLOR=#0000ff]dns-nameservers 64.233.222.2 64.233.222.7[/COLOR]
[COLOR=#0000ff]#[/COLOR]
[COLOR=#0000ff]#[/COLOR]
[COLOR=#0000ff]auto eth1[/COLOR]
[COLOR=#0000ff]iface eth1 inet dhcp[/COLOR]

To make a long story short, after seeing the data that the ifconfig reported on my eth0 when I set it up to be DHCP, I could see that it was getting a different netmask and a different broadcast address than what wowway had told me the first time I spoke with them. I had again spoken to wowway yesterday and asked them to confirm that the gateway, netmask and broadcast address that they had given me earlier was in fact correct. They said they "thought" it was correct. When that didn't work and you suggested I try the DHCP to see what resulted, I remembered a while ago when I first got the static ip address that they told me that the gateway was 65.60.189.33 but then said, no, that was wrong and it should be 65.60.160.1.

I'm thinking that they were confused and just gave me the wrong information. That same day we were discussing why my Netgear router was not working. It gets a different netmask, gateway and ip address as is shown here:

[COLOR=#0000ff]ip: 65.60.160.51
netmask: 255.255.248.0
gateway: 65.60.160.1[/COLOR]

Perhaps when I spoke with them they thought I meant that network instead of the one for the static ip.

In the past when I've purchased an IP address from them I get a block of 5 for one price. I'm thinking that is still the case but that they didn't tell me I had that many. I have no idea if someone else has the other 4. But, I will be calling them again.

By the way, I found a lazy man's site which will calculate the broadcast address of a given ip address and net mask. It will also give you the network address. I assume that the gateway is "usually" the first address after the network address  - which is what I used to verify the gateway for my particular 

The gateway can be any address in the network range.  It is the nearside IP address of the router (LAN interface) the packets are then forwarded to the  upstream WAN interface and on to the Internet.  Your assigned subnet must have at 4 items at minimum: 1. a Network ID,  2. a broadcast address and 3. a gateway address along with 4. your own hosts address.
> 
IP address. Here's the link:

 [http://www.tech-faq.com/calculate-broadcast-address](http://www.tech-faq.com/calculate-broadcast-address)

Again, thanks to everyone who responded to my query.
Bob

I never trust the ISP initially.  The rep you talk to is usually a beginner and has not a clue as to how this all works,  Someday, but not today. ;-)

---

