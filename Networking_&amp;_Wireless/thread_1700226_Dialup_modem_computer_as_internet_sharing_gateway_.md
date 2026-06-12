---
title: "Dialup modem computer as internet sharing gateway to wireless access"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by LancerNZ on 2011-03-04
I am wanting a computer with an external dialup modem (ppp0 modem through a com port /dev/ttys1) to act as a gateway to the internet, forwarding internet traffic through ethernet (eth0 is set to static 192.168.2.2) to a router (the router is 192.168.2.1) where it will be broadcast to other wireless computers like my laptop (192.168.2.3). I've had this setup until recently when the gateway computer (the one with the modem) died. Now I'm replacing that machine with another box and an install of Ubuntu 10.10 but so far things aren't working for me.
[B]
Success so far:[/B]
[LIST]
[*]I have dialup access working on the new box. Took me a while to work out the configuration for getting dialup working, though the IP address is Dynamic (or it won't stay connected), "Check carrier line" is off, and "Ignore Terminal Strings (stupid mode)" is on in order to successfully connect and stay connected to my ISP. I also had to make my normal (non-root) user "lancer" a member of the "pid" group (the reboot) in order to use gnome-ppp as non-root.
[*]The laptop (192.168.2.3) is successfully connecting to the router (192.168.2.1) as I can see the router configuration page when I type [http://192.168.2.1](http://192.168.2.1) into the laptop's web browser. This setup is unchanged from how I had it before when this was previously working and I don't want to change how the router itself is set up. What I want is to know what to fix in the new box in order to get it connected to the router (through ethernet) and bridging the internet through.
[/LIST]

My problem is that whenever I plug in the eth0 from the gateway (192.168.2.2) to the router (192.168.2.1), Ubuntu's automatic plug-me-in network detection kicks in and I find my dialup no longer working through some kind of IP conflict (at least that's what I think it is). Maybe I don't have the "gateway" correctly assigned? (in the gateway computer for the ethernet connection, I had it pointing to itself as I don't know what to put for "gateway IP" as that is automatic).

So, just to check my connection, here I am pinging google (from the gateway computer which has the dialup modem) once a dialup connection has been made.
```
lancer@lancer-desktop:~$ ping www.google.com
PING www.l.google.com (74.125.237.17) 56(84) bytes of data.
64 bytes from 74.125.237.17: icmp_req=1 ttl=55 time=179 ms
64 bytes from 74.125.237.17: icmp_req=2 ttl=55 time=176 ms
64 bytes from 74.125.237.17: icmp_req=3 ttl=55 time=158 ms
64 bytes from 74.125.237.17: icmp_req=4 ttl=55 time=150 ms
```

...going well, so I plug in an ethernet cable to the router. This results in Ubuntu dropping the dialup connection. My modem still has all the lights etc, but...

```
:
:
:
From lancer-desktop (192.168.2.2) icmp_seq=17 Destination Host Unreachable
From lancer-desktop (192.168.2.2) icmp_seq=18 Destination Host Unreachable
From lancer-desktop (192.168.2.2) icmp_seq=19 Destination Host Unreachable
From lancer-desktop (192.168.2.2) icmp_seq=20 Destination Host Unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
:
:
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
^C
--- www.l.google.com ping statistics ---
40 packets transmitted, 4 received, +15 errors, 90% packet loss, time 61721ms
rtt min/avg/max/mdev = 150.767/166.156/179.321/11.924 ms, pipe 3
lancer@lancer-desktop:~$ 
```

As you can see, the dialup connection is now lost, although can be resumed by hitting "disconnect" and the "connect" in gnome-ppp to re-initiate the connection, but of course, this doesn't help me plug in / configure the router or the rest of the network.

What do I need to do in order to make Ubuntu of my gateway computer stay connected to my dialup but also simultaneously share an ethernet LAN to my wireless router and feed traffic to the other computers from there? I have googled this but some of the most promising instruction (e.g. [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)) call for packages like dnsmasq or ipmasq which seem defunct now in Ubuntu 10.10. Other pages seem to suggest dual-networks "can't be done" in Ubuntu [http://ubuntuforums.org/showthread.php?t=1525257](http://ubuntuforums.org/showthread.php?t=1525257) (what!?! I had it before my other gateway died)

Anyway - there's the problem and I have been googling before coming here. Can someone plese tell me how to config the replacement gateway computer working as it should?

---

### Post by LancerNZ on 2011-03-04
I've got it going, for now at least. :)

My problem was caused because I thought I was running two subnets, but with a dialup connection then going into a router, there are effectively three:
Subnet 1: Dialup connection to Gateway computer (Auto DHCP)
Subnet 2: Gateway computer to Router (Eth0 192.168.0.140 => Router 192.168.0.130)
Subnet 3: Router to clients (192.168.2.1 => 192.168.2.x)

The dialup has to start as DHCP, this is from the dialip ISP itself, always giving my "wider world" connection a random DHCP IP address. The ethernet card from this box (Eth0) is static at 192.168.0.140

This ethernet cable is connected to the wireless router, straight into the incoming modem plug (not as one of the 4 outgoing client plugs). Under the router settings, the router ISP gateway address is set to 192.168.0.140 (it's treating my gateway computer as though it's an ISP) and the IP address of the router itself is 192.168.0.130.

The LAN settings for the radio accessible network are a different subnet again. Under "LAN Setup" in the router control panel, the IP address of the router is set to 192.168.2.1, which is the address any radio client uses to access the control panel itself through a web browser. This means that the radio clients should each be assigned 192.168.2.x

A mistake I had been making was that I though everything after the gateway computer would be 192.168.2x, including the outgoing IP address of the gateway eth0 itself. I had not taken into account that the router, thinking it was dealing with an ISP would want to change the subnet once more.

I've been getting this going with nm-applet disabled (through kill command) because it's what I'm blaming for closing the dialup access. I'll now see whether I can get things going with these settings without disabling it.
Also note that I only got the gateway computer forwarding the traffic by running "firestarter" (get this through synaptic) and saying that Dialup PPP was the internet and should be shared to eth0, with Static addresses. This would have done a lot of the masquerading stuff I'm not well clued up on. At this point, the connections are all going.

Anyway, there it is for anyone reading this thread wanting a similar setup. I'm off to see if nm-applet can be left on when the settings are okay.

---

