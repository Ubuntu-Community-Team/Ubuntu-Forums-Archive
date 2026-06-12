---
title: "Bridging Internet Connections and OpenVPN"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by WilcoRogers on 2011-07-13
Hello again:

I'm trying to set up an openVPN server for a small office. I've gotten the server running, and configured keys, and been able to connect to the server. The trouble is that once I connect with my windows machine to the server, I am unable to bridge through to the www. I have combed through so many settings and tutorials, and I am confused as to how to set up the interfaces configuration file. Here's a sample of my routing table:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
XXX.XXX.XXX.0   *               255.255.255.128 U     0      0        0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
default         XXX.XXX.XXX.1   0.0.0.0         UG    100    0        0 eth0

```

How should I be configuring this so that when I'm in the VPN I can get through to the internet? Any help would be appreciated.

Thanks.

---

### Post by Jake.Debord on 2011-07-13
It may not be an issue in your bridged connections. Are you able to do things on the lan just not the internet? It may help to show us your server config settings, just the IP range stuff.

---

### Post by WilcoRogers on 2011-07-13
Here's what I can and can't do:

When client is connected to VPN:
From server to www is GOOD
From client to www is BAD

Here's my current internet configuration:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hell0 2
bridge_maxage 12
bridge_stp off

```

Right now I'm the only client hooked up to the VPN, so I'm not sure how I can test what's what.

There's another issue: I have a no-ip to point to the IP address. When I bridge it, I get a different IP address, while it still looks for the original one (it's configured to auto-update as needed - I'm pretty certain it works). In order to connect, I have to manually change the config file to point at the new IP address. That's fine for now but that needs to work eventually.

This is my first time getting a VPN going.. I knew this was going to involve some hair-pulling...

EDIT: I didn't post what you needed. Here:

```

server 10.8.0.0 255.255.255.0
push "route 10.8.0.2 255.255.255.0"
push "redirect-gateway"
push "dhcp-option DNS 10.8.0.0"

```

MOAR EDIT:

Okay, here's what I REALLY don't understand. Here's the current routing table:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
XXX.XXX.XXX.0   *               255.255.255.128 U     0      0        0 br0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
default         XXX.XXX.XXX.1   0.0.0.0         UG    100    0        0 br0

```

When I fire up the VPN, it seems to think the default gateway is 10.8.0.5, which is nowhere in sight, and doesn't get any response with a ping.
I can ping 10.8.0.0 no problem, but not 10.8.0.2. I also still have no internet traffic from the client.

From the server however, everything is just fine.

Am I just too tunnel-visioned on this? I'm a little over my head I feel.

---

### Post by Jake.Debord on 2011-07-13
One thing to try is disable use default gateway on remote network.
just edit the connection on windows and under tcp/ip properties somewhere under advanced tab there will be a box that says use default gateway on remote network.

Make sure your assigning IP's to users on the VPN that match the range your server is on.

EX: 
if server ip is 10.8.0.2
then make sure the range of ip's available to be assigned are in the same 10.8.0.0 network

if you assign 192.168.0.0 or anything else it will appear as a seperate network and will not communicate correctly.

---

### Post by WilcoRogers on 2011-07-14
Maybe I'm using the complete wrong approach. Here's what I'm trying to do, and maybe bridging is the wrong way to go about it.

So I have a server, with several VMs running on it. One of them will be a VPN server. With this VPN server, I want to be able to have all the computers in the office be able to talk to each other as if on a LAN, and be able to talk with all the VMs installed on the server, as if they were one big happy LAN family.

As for internet, I would prefer to route all the internet through one place (i.e. the VPN server). It seems to me that the idea then is to set up the VPN server essentially as a router, having it assign IPs to all the computers/VMs that connect to it, and then have all the internet traffic go through it.

Is this a feasible plan? Does it even make sense? How does one go about implementing it?

I've gotten openVPN up and running - but the routing doesn't work. I'm wondering why my client gets given a default gateway of 10.8.0.5 when there's no mention of that in any of the configuration I've done.

Any help would be appreciated :) Thanks for the replies so far.

---

### Post by Jake.Debord on 2011-07-14
Do you assign static IP's to everything in this test environment? Something may be getting that .5 IP and messing things up for you?

---

### Post by Jake.Debord on 2011-07-14
And yes. your plan is totally feasable. Your VPN Server vm will auto assign an ip to a client based off of a range designated by you. I'm not sure I follow why you want all internet traffic to go through your VPN but it is possible. I have my vpn setup to handle local traffic and let the clients handle Internet.

I use PPTP which is different from OpenVPN but the idea should be similar
this is an excerpt from my conf file

# (Recommended)
localip    10.0.6.103 #Ip for the Server of VPN
remoteip    10.0.6.50-60 #IP range to assign clients
listen    10.0.6.103

---

### Post by WilcoRogers on 2011-07-14
I figured out that .5 is what the VPN server assigns as a "virtual ip", and so the client picks up on that as the gateway.

To be honest, I'm not set on having all internet traffic go through the VPN, if that makes things simpler. The ultimate goal is this:

1. Have users able to see each other and the VM servers as if on a LAN
2. Have all users have internet acces.

I now have connectivity from both sides (server <-> client), there was a firewall issue. How can I force my client to only use the VPN for VPN related activities, and use whatever else for the internet?

---

### Post by Jake.Debord on 2011-07-14
Your clients are XP correct?

---

### Post by WilcoRogers on 2011-07-14
Yes, they are.

So I've managed now to have the client (unfortunately I only have one at the moment) have VPN traffic over the VPN, and internet traffic thru the internet. It was me being stupid and not restarting the servers, eventually. Now I've got to hook up a few computers and see if I can get things rolling.

---

