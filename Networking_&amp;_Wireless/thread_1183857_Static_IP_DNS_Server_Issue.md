---
title: "Static IP DNS Server Issue"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by kubrox on 2009-06-10
Hi All

Will give you a brief outline of what I have so far and what i want to achieve.

With my ISP I have multiple WAN IPs, I have a router which supports this (Zyxel Prestige) I have it setup using 1-1 NAT. so 'External IP1' directs to 'Internal IP1' etc etc

Currently I have a Windows SBS 2003 Server, running RRAS for the network. This has two NICs, one for the internal network for clients (10.x.x.x) and one for the external network which connects to the router (192.x.x.x). Which in turn is 'mapped' to a WAN IP to the router.

So basically, all the information for the 'External IP1' is routed to the SBS Server 'Interal IP1'

I want to setup a Ubuntu box as an Anti-Spam, Firewall etc etc. Using 'External IP2' which will eventually accept all the traffic for the network, HTTP, FTP, SMTP etc. and forward it on to the SBS Server.

I installed Ubuntu 9.04 Desktop Edition no problem, the NIC gained an IP in the range 192.x.x.x from the router using DHCP, internet access, pinging, package installation worked fine.

However I need to setup the NIC so it isnt reliant on NetworkManager, so I uninstalled it

sudo update-rc.d -f NetworkManager remove

And set my fixed IP in /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.x.2
netmask 255.255.255.0
gateway 192.168.x.1
network 192.168.x.0
broadcast 192.168.x.255

I set my DNS server to the router in /etc/resolv.conf

nameserver 192.168.x.1 (router address)

then I restarted the networking service to update the settings

sudo /etc/init.d/networking restart

However, now, I cannot ping any external domain (google etc) or internal IP
But from any other machine I can ping the Ubuntu machine and it works fine.

if I run host google.com 192.168.x.1 I get a list of domains

I swapped the DNS server from my router address to my ISP DNS server
However ping does not work and host google.com 'DNS Address' does not work.

When I set the NIC to DHCP in /etc/network/interfaces

it picks up an address fine, but still cannot ping or browse the web.

Seems like I'm missing something as when using NetworkManager with DHCP it works fine
However when its disabled and using DHCP or Static IP ping etc does not work.

Sorry for the long post, its my first, go easy on me :)
Thought I better put too much info rather than too little!

K

---

### Post by jonobr on 2009-06-13
I would recommend using wireshark to trace the packets when its working fine to see where it is actually resolving to.

Run wirehsark and then do an nslookup on pingpoltter.com or whichever to get a dns lookup going .

Match that to what you set your resolv.conf, I think you mentioned 192.168.1.1

Some devices use 192.168.0.1 as the DNS and not the 192.168.1.1
however, comparing the good wireshark should show something interesting.

If that doesnt work, doing the wireshark on any dns lookups may yield fruit also.

If you don't want to use wireshark you can use

sudo tcpdump -vvv port 53 (If I remember rightly) on the terminal to see the dns packets

When you do any web stuff, you should see a packet go out and hopefully some response

---

