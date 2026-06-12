---
title: "Allow LAN only"
date: 2013-07-30
forum: Networking &amp; Wireless
---

### Post by 4TdpD3n on 2013-07-30
Hi, I'm interested in getting my machine to be only accessible through LAN, via static IP address.
A Google search told me that I simply need to not specify a default gateway in my interfaces file.
Doing so however, my machine has no network connection at all, and I'm unable to ping it.

These are the contents of my /etc/network/interfaces files:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.4
        netmask 255.255.255.0
#       gateway 192.168.2.1


# Example to keep MAC address between reboots
#hwaddress ether DE:AD:BE:EF:CA:FE


# WiFi Example
#auto wlan0



```

Am I missing something, or is there a better way to go about this?
Help would be greatly appreciated, thanks.

---

### Post by TheFu on 2013-07-30
There are many ways to accomplish this, but the best would be to use a firewall to block all external requests. If you have a router that serves as the gateway to the LAN, then blocking that IP will be necessary too, since some inbound connections will appear as from the router internal LAN IP.

The more secure way would be to have a different physical network that can only be used on the internal LAN, then 1 machine which serves as the gateway/proxy for all the others. 1 of the machines, the gateway, will need to have 2 physical network cards.

BTW, all machines on the same subnet CAN see each other if there is a connection, their IPs are different and the netmask shared is identical. No need for a router at all - but it is convenient to put all the IP/hostname lookups into a /etc/hosts file. My backup network works this way.

---

### Post by papibe on 2013-07-30
Hi 4TdpD3n.

The safest way I can think of is to put your machine behind a physical router/firewall and grant access only through a VPN.

Without assigning other resources, as TheFu suggested it, you can leave your network as default, and set up a firewall. For a powerful (and may be advance) tool, take a look [iptables]("https://help.ubuntu.com/community/IptablesHowTo"). There are other simpler (some GUI) firewalls, but note that most, if not all, use iptables underneath.

Let us know how it goes.
Regards.

---

### Post by 4TdpD3n on 2013-07-30
Thanks for the replies guys.

However, security is only one part of my concern.
The other part is painlessly connecting to different networks. The machine is meant to be headless, ideally I'd like to be able to plug it into various routers at different locations, and be able to access it through ssh without needing to reconfigure it's network properties, because I'll know it's static IP.

Thoughts?

---

### Post by TheFu on 2013-07-30
> **4TdpD3n said:**
> Thanks for the replies guys.

However, security is only one part of my concern.
The other part is painlessly connecting to different networks. The machine is meant to be headless, ideally I'd like to be able to plug it into various routers at different locations, and be able to access it through ssh without needing to reconfigure it's network properties, because I'll know it's static IP.

Thoughts?

Static IPs do not work well when you want to connect to different networks. That is what DHCP is for. On your own networking, you can setup a DHCP reservation so it will always get the same, internal, static IP. On someone elses' network, that can become troublesome - unless you completely control their network.

Remote access violates your first desire - LAN-only connections. Pick whether you want LAN-only connections OR if you want remote access possible through the internet.

Connecting to a remote machine over the internet will usually mean having to open a port on the edge router protecting that machine. In a corporate environment, that isn't usually possible.  If you brought a machine to my network and asked to leave it here AND asked me to open a port - I'd show you the finger. OTOH, if you are managing everything about the remote network, then anything is possible.

It sounds like you want everything, but have a few conflicting requirements. You have some decisions to make.  Or am I misunderstanding the requirements?

---

### Post by 4TdpD3n on 2013-07-30
I only intend to SSH when I'm on the same LAN, not from outside the network.
 Ideally, I wish that connecting the ubuntu machine to the router didn't give it Internet access, just local network that I can use to communicate with it while I'm there. I'll be moving this box around a lot, and really just don't want to have to connect a monitor to it each time I do.

---

### Post by Dennis N on 2013-07-30
> **4TdpD3n said:**
> I only intend to SSH when I'm on the same LAN, not from outside the network.
 Ideally, I wish that connecting the ubuntu machine to the router didn't give it Internet access, just local network that I can use to communicate with it while I'm there. I'll be moving this box around a lot, and really just don't want to have to connect a monitor to it each time I do.

I add a line to **/etc/ssh/sshd_config** under Authentication:

**AllowUsers *@192.168.1.***

Permits login by users only from machines whose IP addresses match (local machines). 

Your specific pattern may be different.

Is this what you are after?

---

### Post by TheFu on 2013-07-31
> **Dennis N said:**
> I add a line to **/etc/ssh/sshd_config** under Authentication:

**AllowUsers *@192.168.1.***

Permits login by users only from machines whose IP addresses match (local machines). 

Your specific pattern may be different.

Is this what you are after?

I suppose a firewall that blocks all inbound connections, except ssh, then limits sshd access to only local networks would be best.  However, local networks can have different subnets
* 10.x.x.x
* 172.16-32.x.x (check this one)
* 192.168.x.x

So you'd need to allow any machines on those to get in.
If you don't want a monitor, bring a serial cable and use the serial port connection with a minicom or similar client between the machine you move around all the time and whatever client machine you have.
Or you can put 2 NICs inside the machine and pick an odd 10.x.x.x subnet just for your needs, then ssh in and setup the other network information for each location as needed. If you got the information BEFORE arrival, you'd be able to preset it all.

I usually just leave it for DHCP, show up, ask what static IP I can have, switch the network over and I'm done.
Your situation will determine what is the best answer. Sorry we don't ahve a simple solution.

---

### Post by 4TdpD3n on 2013-07-31
No problems, really I just need to suck it up and get used to lugging this monitor around. Really do appreciate all the help and suggestions, I'll be implementing a bit of it.

---

