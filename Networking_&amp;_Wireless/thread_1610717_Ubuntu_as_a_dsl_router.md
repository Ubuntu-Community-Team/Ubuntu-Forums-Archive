---
title: "Ubuntu as a dsl router?"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by SoftwareExplorer on 2010-11-01
I would like to setup one of my ubuntu desktops as a dsl router. It has a wireless card and a ethernet port (and I can add another ethernet port with a pci card I have lying around).

Reasons my old router (An actiontec GT701-WG) isn't good enough:
Doesn't support ipv6.
Doesn't do NAT hairpinning.

What I would like to do:
Get a dsl adapter / modem that is not a complete separate computer (ie it has it's own address and runs an OS). (I would like to do this because I want my desktop to have the public ip, not the modem).
Set the "dsl desktop" up to connect to the ISP using PPPoe.
Make a 192.168 network out of the Wireless and atleast one ethernet port setting up a dhcp server the 192.168 network.
Set the dsl desktop up to do NAT if ipv4 (with hairpinning).
(I already have this basically done:Set up a firewall that drops packets except for a few ports.)
(I also already have this done:Set up the dsl desktop to get an ipv6 address/connection via teredo/miredo.)
The next ones would be nice and are if it can be done and probably after I get the basics working:
In addition to giving out ipv4 internal network addresses, give out global ipv6 addresses (I'm not sure if this is possible without a native ipv6 connection).
Possibly set up a debian package caching server.
Possibly serve Ubuntu PXE images.

I have telnet access to the router if that helps to see how the adsl and pppoe is set up. Looking at the modem configuration pages, it uses PPPoe, RFC 1483 Routed Encapsulation, LLC Bridged atm encapsulation, UBR Qos, and Mmode. My DSL provider is Qwest and my ISP is eoni.com.

So I guess I should start by asking how much of this is possible. How hard would it be to set up? Compiling stuff hard or just config files? How much would a (non-computer) dsl modem cost? Does anyone have any suggestions for a good modem? (I don't know where to start looking for one, I'm not sure how you tell if they are really their own computer.)

Edit:I tried it and found out that the dsl provider also supports G.dmt and T1413 instead of mmode.

---

### Post by lpitman on 2010-11-02
Place the modem into RFC14?? Bridging mode...this turns the router into a transparent bridge that is just a passthru and termination of DSL signal...the output (ethernet port) should connect to the input (outside firewall Ubuntu ethernet port) then configure the PPPoE on Unbuntu to perform the connection and authentication...QWest helped me with the config questions.

---

### Post by SoftwareExplorer on 2010-11-03
> **lpitman said:**
> Place the modem into RFC14?? Bridging mode...this turns the router into a transparent bridge that is just a passthru and termination of DSL signal...the output (ethernet port) should connect to the input (outside firewall Ubuntu ethernet port) then configure the PPPoE on Unbuntu to perform the connection and authentication...QWest helped me with the config questions.

Thank you so much! I'll try it tonight, when no one is using our connection.

---

### Post by SoftwareExplorer on 2011-01-06
Ok, so I did try it but had problems at first, but I eventually figured it out. 

So far, I have the following set up:
The desktop has the public IPv4 address and connects through the router in transparent bridging mode.
A ipv4 dhcp server and a 192.168.0.0/24 network, with NAT and hairpinning for forwarded ports.
A ipv6 tunnel from Hurricane Electric tunnel with a block of addresses allocated for my network, with Stateless autoconfiguration and DHCPv6 to give them out to the local network.
A firewall for the desktop computer with Gufw. For ipv4 all the other computers on the network are firewalled by the ipv4 NAT. For ipv6, I know how to make the firewall also work like NAT and firewall for the whole LAN, but I decided to not do that. If I want a firewall for my LAN machines, I'll run one actually on the machine.
Switching/bridging the network ports on my computer.

So thanks lpitman, I wasn't ignoring your reply, it just took me a while to make full use of it.

So, the stuff that's left:
Setting up a debian package caching server. Squid-deb-proxy won't work because it doesn't do IPv6. Apt-zeroconf doesn't seem to work since a couple of Ubuntu releases ago. 
Setting up serving Ubuntu PXE images. I haven't even started on this.

If anyone is reading this thread and wants to set up the same things I got working, just ask, I would be glad to help.

---

