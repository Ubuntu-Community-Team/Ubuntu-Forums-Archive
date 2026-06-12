---
title: "Router Setup in a different way(I think)"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by Sicarus on 2010-07-15
Hello...
 
I'm trying to install an Ubuntu machine as a router. The setup i need seems to be rather different, considering i can't find ANY help on the interwebs to manage my perticular setup...
 
[LEFT]I'm looking to set it up as follows: Modem/Internet -> LAN1 + Server -> LAN2[/LEFT]
 
[LEFT]LAN 1 is connected to our gateway, along with the Ubuntu server. LAN 2 is then connected to the server.[/LEFT]
LAN1 and the server are on the same subnet, and should both be able to access the internet. LAN 2 is on a different subnet, but should also be able to access the internet, but the 2 LAN systems must not be able to comunicate with each other. The server conects to the gateway through eth0 and to LAN2 through eth1. Is this possable? I'm not sure if i'v explaind it clearly... If more details are needed, please let me know what to add, as i'm rather new to the hole "forum thingy"... Thanks in advance!

---

### Post by YesWeCan on 2010-07-15
Hi.
Just to clarify: you want to have two separate subnets, each with access to the internet through the same modem. Is that right?

I am not sure you can share the modem among PCs without a router. One solution is to use 2 routers, router1 connects to the modem and provides subnet1 (for LAN1) and router2 connects to router1 and supplies subnet2 (for LAN2). This is probably the easiest way to do it because the routers will automatically take care of all the dhcp and dns stuff and have multiple ports so you don't necessarily need separate switches.

If you want to make router2 using a Ubuntu PC this would be a fun project. It will need 2 NICs and you'll need to read up on iptables, dns and dhcp and linux routers [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router). You'll need an external switch to accommodate multiple LAN2 PCs.

---

### Post by Sicarus on 2010-07-20
Hello. Thanks for the speedy reply...

After discusing it with my boss, it turns out I had the wrong idea...

What we have currently is our LAN on range 192.168.0.xxx connected to our gateway which has the IP 192.168.0.253. What we need is another network range, connected to the linux machine, to be able to access only the gateway(and the internet) and not the rest of the network. So it can't access 192.168.0.1 - 192.168.0.250. I've found a few forums that might help, but they all sugest using DHCP and that's not what I want to do. Do I need to setup DNS and stuff like that too? Where? And what address should I give it. Sorry for the noob questions, I'm new to servers and networking... Thanks.

---

### Post by YesWeCan on 2010-07-20
Ok. The existing network uses subnet (address range) 192.168.0.0/24. The /24 just denotes that the first 24 bits of the base address are fixed. The gateway address is 192.168.0.253 and this is the address that a network PC sends packets to that are not within the subnet range. So a PC may have a browser application running on it that wants to send a packet to 72.33.45.18 (made up) and the PCs operating system has a switchboard that checks whether this address is within the LAN subnet or not. If it is not, then it defaults to sending the packets to the device at the gateway address which is in the subnet. The PC can only send packets out to the LAN to addresses within the subnet range. The PCs network interface card (NIC) won't let it do otherwise. So a gateway is a device that has a local subnet address but can forward packets to a different subnet (eg, the public internet).

A router is a gateway provider. Think of a router as a device for making connections between different subnets. This is what you want to do. You want to have a second subnet for your linux PC, but you want to use a gateway for internet access that is part of the existing subnet. In short, you need a gateway on your linux subnet that routes packets to the gateway on the existing subnet (but not to any other addresses on the existing subnet).

Suppose your linux subnet were 1.0.0.0/24. The gateway for this subnet needs to be an address within the subnet range. Let's say you chose 1.0.0.1. So you need a router that connects between the two subnets that forwards packets it receives at 1.0.0.1 on the linux LAN to address 192.168.0.253 on the existing LAN.

DNS is a address book service that PCs use to find out the IP address for a url name. So when you type "www.google.com" in a browser the PC has to find out what IP address this url has so that it can send packets to that address, or to the gateway address if it isn't within the PCs subnet. The PC needs to know the address of the device that provides DNS so it can ask it. Normally, the DNS device is at your ISP.

How does the PC find out about the ISP DNS server IP address? Either you find out what that IP address is and manually tell your PC or your PC uses DHCP to automatically get told it by your router. DHCP is a sort of automatic configuration service for all devices on a network. The router takes care of telling all the PCs the DNS server IP address(es), because the router can ask your ISP directly.

For your linux LAN you do not have to have DNS and DHCP capability. But it will be inconvenient because you will have to manually tell each PC what the ISP DNS server address is and the routers gateway address. This is a pest because if you connect a new PC to the network it won't be able to access the internet automatically.

In short, to do what you want the easy way just buy a router. To do it the harder but more interesting way you must configure your linux PC to act just like a router. There's plenty of documentation around about how to do this, including DHCP and DNS services.

---

### Post by Sicarus on 2010-07-20
wow... firstly, awesome reply. Thank you very much!!

I'v managed to setup my linux machine so it has two NIC's, one with IP Address 192.168.0.205 and the other with IP Address 192.168.1.205. It's setup so that I can access it from both subnets... From my pc (192.168.0.17) i can ping my test pc (192.168.1.31) and vice versa (Both mine and the test pc can ping the linux machine). 

The Linux machine is setup so it uses our original Gateway (192.168.0.253) to access the internet, which works. If i set my pc (192.168.0.17) to use the Linux machine as a default gateway and DNS server (on address 192.168.0.205), I am able to access the internet, but if I do the same on my test pc (set the default Gateway and DNS to 192.168.1.205), it doesn't work. I'v tryd using the 1 range and the 0 range as the defaults, but it just wont connect... From what I am able to gather, it's because the test pc and the Original Default gateway are not on the same subnet. Am I correct? Is there a way around it?

To sum it up: 
LAN1 = 192.168.0.xxx
LAN2 = 192.168.1.xxx
Gateway = 192.168.0.253
Linux router = 192.168.0.205(eth0) AND 192.168.1.205(eth1)

---

### Post by YesWeCan on 2010-07-20
Good progress!

You now need to read the IP Masquerading section here: [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)
Please read this first because it is important that you learn exactly what is going on.


One problem you are having is rather simple. When your PC on LAN1 sends packets addressed to the internet to the linux box the server forwards them to the LAN1 router/gateway which forwards them to the public internet. These packets contain the source address of your PC. When a reply comes back the router remembers  the source address and forwards the replies to your PC. Everything works.

But when your test PC on LAN2 sends internet bound packets to the linux box their source is the test PC, a LAN2 ip address. The linux box forwards the packets to the router unmodified. When the router gets replies it does not recognize the LAN2 source address because it only knows about LAN1. It doesn't know where to send the reply packets so it discards them.

So what is needed is something with the natty title of "masquerading". This causes the linux box to substitute the source address for its own LAN1 address. It remembers what the true address was, your test PC, when it gets the replies from the router. Now the router is happy because it has to send the replies to the linux box on LAN1.

So enable IP forwarding
Add an entry to iptables to masquerade incoming packets from (-s = source) LAN2 bound for (-d = destination) LAN1 gateway.

sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -d 192.168.0.253/32 -j MASQUERADE

Try that.

Would you mind posting your kernel routing table here: 'route -n'

---

### Post by YesWeCan on 2010-07-20
Just a note on the masquerade. The way they do it in the tutorial is to masquerade everything from a particular source that goes out on a particular interface, eg: they use the '-o eth0' switch.

I recommend you don't do this because even a LAN2 packet bound for a LAN1 address will be masqueraded. And I think you mentioned that you want to keep the LANs from accessing one another. By specifying that LAN2 source packets will only be masqueraded if they are bound for the LAN1 gateway, then LAN2 source packets bound for other LAN1 addresses will be dropped.

But you had better test this to make sure I am right. :)

---

### Post by Sicarus on 2010-07-21
Thank you! Exactly what I wanted to know!! You rock!

I have tryd it, and unfortunatly it's not working YET. But I think that it could be because I've tryd too many things and used a program or two that might be conflicting. I think a clean, fresh install is in order... Thank you once again for your time and effort!! I'll post what it does once I've installed it again and set it up properly....

:popcorn:

---

### Post by Sicarus on 2010-07-21
> **YesWeCan said:**
> Would you mind posting your kernel routing table here: 'route -n'

sorry. i forgot... 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.253   0.0.0.0         UG    100    0        0 eth0

seems pretty default to me...

---

### Post by Sicarus on 2010-07-21
[QUOTE=sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -d 192.168.0.253/32 -j MASQUERADE[/QUOTE]

After reinstalling and re-reading this, I saw that I forgot to ask.. why is it 192.168.0.253/32? shouldn't it be 192.168.0.253/24?

---

### Post by YesWeCan on 2010-07-21
/32 means all 32 bits, reading from left to right, are fixed.
So 192.168.0.253/32 means only address 192.168.0.253

192.168.0.253/24 would not be a valid range. You would have to write 192.168.0.0/24 meaning 192.168.0.0 to 192.168.0.255.

Make sure you have set ip_forward = 1. It may have been reset when you rebooted.

If it still doesn't work (you cannot ping 192.168.0.253 from LAN2), please post outputs of
'route -n'
'sudo iptables-save'
'ifconfig'

---

### Post by Sicarus on 2010-07-21
It doesn't work :( i can't figure out why!! It works on my zero ip range, but not the one range...
here are the stats you askd for. I hope it's useful...

route -n::

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.253   0.0.0.0         UG    100    0        0 eth0

sudo iptables-save::

# Generated by iptables-save v1.3.8 on Wed Jul 21 16:32:38 2010
*nat
: PREROUTING ACCEPT [4768:473551]
: POSTROUTING ACCEPT [4376:435019]
:OUTPUT ACCEPT [297:22216]
-A POSTROUTING -s 192.168.1.0/255.255.255.0 -d 192.168.0.253 -j MASQUERADE
COMMIT
# Completed on Wed Jul 21 16:32:38 2010
# Generated by iptables-save v1.3.8 on Wed Jul 21 16:32:38 2010
*filter
:INPUT ACCEPT [4277:538587]
:FORWARD ACCEPT [57420:3858193]
:OUTPUT ACCEPT [7943:1035129]
-A FORWARD -s 192.168.1.0/255.255.255.0 -d 192.168.0.253/255.255.255.253 -j ACCEPT
-A FORWARD -s 192.168.0.253/255.255.255.253 -d 192.168.1.0/255.255.255.0 -m state --state RELATED,ESTABLISHED -j ACCEPT
COMMIT
# Completed on Wed Jul 21 16:32:38 2010

ifconfig::

eth0      Link encap:Ethernet  HWaddr 00:50:bf:73:99:74
          inet addr:192.168.0.205  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe73:9974/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5613060 (5.3 MB)  TX bytes:5820345 (5.5 MB)
          Interrupt:17 Base address:0xd800

eth1      Link encap:Ethernet  HWaddr 00:11:95:dd:7f:e2
          inet addr:192.168.1.205  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fedd:7fe2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17199 (16.7 KB)  TX bytes:13873 (13.5 KB)
          Interrupt:16 Base address:0xee00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17156 (16.7 KB)  TX bytes:17156 (16.7 KB)


(Just as a pointless sidenote: Someone should do something about that auto smiley thingy... certain things that need saying require using the "code" that the smileys do and it stuffs up the post...)

---

### Post by YesWeCan on 2010-07-21
Check that your test PC on LAN2 has its default gateway set to 192.168.1.205.

Try simplifying the routing:
replace the post-routing directive with this:
POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE
replace both forward directives with this single directive:
FORWARD -i eth1 -j ACCEPT

---

### Post by YesWeCan on 2010-07-21
I should confess that my post-routing command in post #6 is not quite correct. It successfully stopped masquerading of destinations other than the router but this also excludes internet addresses. So you would have been able to ping the router but no other addresses.

POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

ensures that all packets from LAN2 are masqueraded. Restricting cross-communication between the LANs, if you need this, can be done another way.

By now you will be able to ping all LAN1 and internet addresses from your text PC on LAN2. :D
If you still cannot then it will either be because the linux kernel ip_forward is not set to true...

sudo -s
echo 1 > /proc/sys/net/ipv4/ip_forward
exit

...or because the default gateway of the LAN2 PC is not set to 192.168.1.205.


You won't be able to browse websites using url names yet. You will be able to get [www.google.com](www.google.com) by putting 74.125.47.105 in the browser. This is because the LAN2 PC does not know where the DNS server is and without this it cannot look up the IP address for a url name.

It's a bit like a telephone system. I ask you to call John Brown and you have to make a call to Directory Enquiries to get his number. DNS is the enquiry service. You'll need to find out where LAN1 PCs get their DNS service.

---

### Post by Sicarus on 2010-07-22
If there's one thing I don't like about PC's, it's that you can struggle for 2 weeks on a problem, and once you get the solution you want to kick yourself 'cos it was such a simple thing to do....

Turns out all I had to do was the last post of yours. Three commands!! Can you believe it..... 

Thank you SO much!! It works 100%!! I can access the internet from both the One range and the Zero range... But I can't access file shares, etc between ranges. Which is perfect!!

You were a great help, and I wouldn't have gotten it without you! Thank you once more!! Have popcorn... :p:popcorn:

---

### Post by YesWeCan on 2010-07-22
Good stuff! \\:D/

You may want to put a firewall on the linux server: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Here's an example of setting up dhcp: [http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

And you need to read up on how to automatically restore your ip_forward setting and iptables rules after rebooting.

Brian

---

