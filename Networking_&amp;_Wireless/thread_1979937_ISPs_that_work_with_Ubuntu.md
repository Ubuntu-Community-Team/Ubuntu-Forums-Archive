---
title: "ISPs that work with Ubuntu"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by cecilieaux on 2012-05-14
I'm considering a cable ISP called RCN (this is in USA). Their page ([http://tinyurl.com/bvooajv](http://tinyurl.com/bvooajv)) says the computer must run Windows or Mac systems.

1) Does anyone have experience running Ubuntu with an RCN connection? How?

2) Anyone recommend another ISP that is that fast (and cheap)?

---

### Post by roelforg on 2012-05-14
In my experience, they say "Mac/Windows only" because they don't want to support linux.
As long as the modem gives you a standard ethernet line (or WiFi) to connect to your computer, ubuntu should work just fine.

---

### Post by Frogs Hair on 2012-05-14
I would look at some reviews on that ISP before deciding. Unless there is a requirement for a specific PC or Mac software I agree with the first post.

---

### Post by shumifan50 on 2012-05-14
From the website you quote the PC needs an ethernet connection, which will be used to connect to the modem. This means that any router with an ethernet WAN port(not ADSL) or any PC running Linux will be able to connect. You will need to find out how they establish the legality of the connection, as some service providers authorise by MAC address and others require login using PAP or CHAP over PPPoE. These are the ones I have encountered, but there might be more variations out there.
I would recommend getting a router/firewall like a Cisco ASA(better class device) or netgear or any of the other home routers.

---

### Post by roelforg on 2012-05-14
> **shumifan50 said:**
> From the website you quote the PC needs an ethernet connection, which will be used to connect to the modem. This means that any router with an ethernet WAN port(not ADSL) or any PC running Linux will be able to connect. You will need to find out how they establish the legality of the connection, as some service providers authorise by MAC address and others require login using PAP or CHAP over PPPoE. These are the ones I have encountered, but there might be more variations out there.
I would recommend getting a router/firewall like a Cisco ASA(better class device) or netgear or any of the other home routers.

+1

My ISP has that same "no linux" policy.
Yet my 5 ubuntu pc's and linux ps2 can access the net just fine,
just make sure you never say "linux" or "ubuntu" to your tech-support and translate their instructions from windows to linux in your head.
For example:
> 
TS (Tech Support): Go to start->run, type cmd and run ipconfig and tell me the ip.
You (thinks/do): hit ctrl-alt-t, run ifconfig and tell him the "INET ADDR:"

Okay?
This worked fine for me (only needed it once... when their network blew out, i can usually fix my own stuff myself or with help from here and the internet)

---

### Post by TBABill on 2012-05-14
Normally the only limitation is that the ISP be able to see their equipment on the other end (or yours if you own the modem) so that their system registers the MAC address of the device used to connect you to them. Beyond that device is normally just an ethernet connection, which does not distinguish between operating systems. And you normally access your router/modem via any browser so even that is not a limitation.
 
One caveat to all that: they will not help you in any way with settings to help you communicate over the network. That's on you and normally not a big deal.

---

### Post by QIII on 2012-05-14
There may be cases where the ISP serves content on their website that is itself incompatible with Linux.  For instance, Xfinity serves its movies and TV on their website as Silverlight content.  Silverlight can't be installed on Linux and the Microsoft sanctioned open souce Moonlight (which is no longer under development -- I don't think Xamarin took it on when they took Mono) doesn't often work.

Edit:  Looks like Xamarin did take Moonlight.

---

### Post by hawkmage on 2012-05-14
In general I would not suggest connecting your PC regardless of the OS on it directly to the Cable/DSL device.  I would suggest that you place a Firewall in that position and then connect any PCs or other network devices behind the firewall.  

In most cases I have encountered an ISP providing residential internet access will support IP address asignment via DHCP, PPPoE, PPTP or L2TP over Ethernet.  Most ISPs using Cable modems use DHCP and most DSL use PPPoE.  

Doing a scan of their quick start documentation it looks like RCN uses DHCP so there should be no issue with putting just about any IP device on the connection.

---

### Post by roelforg on 2012-05-14
> **hawkmage said:**
> In general I would not suggest connecting your PC regardless of the OS on it directly to the Cable/DSL device.  I would suggest that you place a Firewall in that position and then connect any PCs or other network devices behind the firewall.  

In most cases I have encountered an ISP providing residential internet access will support IP address asignment via DHCP, PPPoE, PPTP or L2TP over Ethernet.  Most ISPs using Cable modems use DHCP and most DSL use PPPoE.  

Doing a scan of their quick start documentation it looks like RCN uses DHCP so there should be no issue with putting just about any IP device on the connection.

How about using 2 seperate physical firewalls? *laughes* (yes, i actually have those)

But seriously,
hawkmage has a good point.
Though routers are standard equipment nowadays as people want to use wifi-phones and wireless laptops.
But the ones build into modems tend to be very crappy (low range), so you're better off spending a few bucks on one with a descent range (and one that you can overclock w/o getting in trouble with your isp, most routers run at 60-80% power/range by default)

---

### Post by hawkmage on 2012-05-14
> **roelforg said:**
> How about using 2 seperate physical firewalls? *laughes* (yes, i actually have those)
I don't have multiple physical firewalls but I do have an entry level enterprise firewall with multiple ports to separate internal and DMZ traffic as well as multiple VLANs.

And yes this is for my home network.

---

### Post by jmore9 on 2012-05-14
I use comcast presently and also use Ubuntu 12.04.  When i installed the network automaticly configured itself and internet worked.

Before i got the internet i had to register my cable modem , it is mine not comcasts , with mac addy and serial.

other than that works just like in winsp no difference that i can tell.

---

