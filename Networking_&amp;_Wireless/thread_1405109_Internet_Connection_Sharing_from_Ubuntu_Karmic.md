---
title: "Internet Connection Sharing from Ubuntu Karmic"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by paraplegicpanda on 2010-02-12
Okay, so I'm trying to set up my internal network to use my Karmic computer as a gateway to get my girlfriend online, but I'm having some issues. I've seen a few tutorials online and saw Firestarter mentioned, since it was supposed to do what I wanted, I figured I'd give it a try.

I went through the setup wizard, set wlan0 as the internet connection and set eth0 as the network to which it should share my internet connection. Unfortunately when I started it up I got the error that eth0 wasn't ready... So here's my configuration:

Cable modem connected to wireless router (A) upstairs;
Ubuntu Karmic connected (wirelessly) to wireless router (A) on wlan0;
Ubuntu Karmic connected (wired) to downstairs wireless router (B) on eth0;
Windows XP connected (wirelessly) to downstairs wireless router (B).

I know it's a bit complicated but she doesn't want to haul her computer upstairs or to the other side of the house to connect to the upstairs router nor does she want to buy a better antenna like mine, and I don't want to route ethernet cable through the house because I'm lazy. Since I know this can be done through software with the setup I have, I want to do it.

Anywho... I think one problem has to do with too many DHCP servers (both wireless routers have DHCP on and I can enable it on my desktop, but I'm not sure which ones to turn on or off) and I think somewhere in this network I need to set a static IP for her at least desktop if not both desktops...

So I've been through a few configs and I haven't had any luck so far but none of them were necessarily according to howtos, rather they were how I gathered it should all be setup from research. Now that I'm absolutely baffled, I need some help. Anybody?

One more thing, I have access to my web admin for the both routers, router A is a Linksys WRT54G and router B is a Belkin F5D7230-4 (basic Belkin and Linksys wireless routers) if that helps at all with the configuration.

---

### Post by Iowan on 2010-02-12
Is [this]("http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/") one of the tutorials you used?

---

### Post by paraplegicpanda on 2010-02-12
It wasn't, but I think it ALMOST fixes me up... I think setting it to share my connection to eth0 is done and turning off DHCP in my router should do the trick, I just need to get eth0 working again! It seems that no matter what I do I can't seem to get it up and working. Here's my ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:24:8c:a0:4f:81  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6400 (6.4 KB)  TX bytes:6400 (6.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:54:95:bb:c7  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe95:bbc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130476798 (130.4 MB)  TX bytes:14004268 (14.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-08-54-95-BB-C7-39-35-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

It's connected to the router but when I check the web admin from another computer it doesn't detect my desktop, nor does my desktop detect the router. I've also tried switching it out with a couple of brand spanking new ethernet cables, but I don't seem to be having any luck. Any suggestions?

---

### Post by paraplegicpanda on 2010-02-12
How exactly would I go about disabling it? I ran across [this]("https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5") but it's for an older version of NetworkManager so it didn't work. I REALLY don't want to uninstall it because I then won't have internet to reinstall it if it becomes necessary. Lugging my girlfriend's desktop and a monitor to the third floor isn't exactly my idea of fun.

Also: The router has to be able to see my desktop at least a little, because it lights up to show that the computer is plugged in. When I open the nm-applet under Wired Network it says 'device not managed'.

---

### Post by Iowan on 2010-02-12
I haven't gone through the tutorial I linked to. In olden days, Network Manager only managed one interface at a time - to have two active interfaces meant one needed to be defined in */etc/network/interfaces*. Interfaces defined there are/were (essentially) invisible to NM - so I'm not quite sure how the new ICS works. 
I'm still a bit confused how you plan to link the two wireless routers - or is that part already working?

---

### Post by paraplegicpanda on 2010-02-14
The two routers are separated. My computer connects to Router A wirelessly and to Router B with an ethernet cable.

---

