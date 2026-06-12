---
title: "Internet connection sharing by the numbers?"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by mercenary on 2006-06-12
Does anyone know of a by the numbers setup up for Internet connection sharing?  I've been at this a while and can't seem to get it right.  I don't know if I'm getting information from 5.10 and 6.06 confused (some isn't labeled) or if there is even a difference.  The wiki seems to imply no change.

I've read the Firestarter web page front to back and have installed Firestarter.

I've got 2 NICs in my firewall/dhcp server machine, eth0 is connected to a DSL modem and I have access to the internet.  I added a card which presented it self as eth2.  (Eth0 appears to have remained unchanged since I still have interenet access.)

I have eth0 set up for DHCP to communicate with my ISP.

Eth2 is manually configured with IP 192.168.0.1, mask 255.255.255.0 and no Default Gateway entered.

I setup Firestarter checking the box for Enable Internet connection sharing, but the Enable DHCP for a local network was grayed out so I had to go into preferences to set it.  I believe I Have the 2 NICs setup correctly because I can still access the Internet from the server.

One forum I was reading mentioned editing dhcpd.conf but I wasn't sure if that was needed.  It appeared to contain the range I configured in Firestarter.  (It didn't look like the examples from ubuntu wiki.)  The post also mentioned creating a symbolic link to dhcpd.conf (I think because ubuntu uses dhcpd3.conf and Firestarter wouldn't know where it was.)  All that made sense so I did it, but now I'm unsure and can't find that post.  The guy also mentioned editing another config file to include the NIC (eth2 in my case) that serviced DHCP requests.  I would have thought that Firestarter should have setup this up since I don't see the issue in any other documentation or maybe it doesn't need to be done.  It looked necessary at the time.  His post said you had to specify the name server as <dynamic> didn't work so I did.

So, It seemed that I had everything configured properly, but got a generic error message from Firestarter everytime I hit save.  The kicker was that the seemed to go active even though it gave me the generic "something is wrong with your config" error message.  I can still access the internet from my firewall/DHCP server machine at this point.

I haven't spent much time on the clients, they didn't connect automatically (they were connected to a Win98 connection share previously.)  I got hung up on the error message but now I wonder if it was a bogus message.  Should I have to change the clients?  I did shut down my old firewall/DHCP server.  The previous system was configured DHCP, had to upgrade because the old internal modem wasn't providing modern DSL speeds and the new modem is external.  Didn't know if Win98se could handle 2 NICs, wanted to try unbuntu anyway.

Anyway, I seem to be making this harder than it should be.  I've spent hours at it.  I have the exact configuration on page 1 of Firestarter's physical setup section so this is nothing new to anyone.  It seems ubunto may be a bit quirky, but this isn't rocket science.

If anyone could throw me a bone, I'd appreciate it.

---

### Post by kingedwin on 2006-06-12
I've been struggling with this for quite some time, and so far no one has come up with an answer.  All I can tell you is that the methods in the Wiki and what I've found on the forum haven't worked for me, either.  Nor has setting up both computers dynamically and statically, nor editing the dhcpd.conf to use the assigned addresses. :sad:

Internet connection aside, are you able to communicate between the computers, either by pinging or sending files back and forth?  If you look at the devices under network tools, is the proper IP address listed?

---

### Post by mercenary on 2006-06-13
Ain't that a kick in the pants?  I've been so impressed with unbuntu that I want to dump Gatesdos completely.

It's nice to hear that I'm not alone.

I haven't played around with just the DHCP trying to get machines talking to each other.  From what I read, I thought impementing Firestarter would be a cake walk and that it would take are of DHCP.  I think I put in a default gateway 192.168.0.1 and a client was able to get an address and ping the server but I had been at it all day and can't quite remember what I was doing/trying.

I found one post (someplace) where the guy seemed to come up with 2 critical issues.  Only, I can't find that post and I'm not sure that it was the full resolution.  (During part of my time I had a cable not plugged in, duh.)  Was getting so fustrated, I was installing/removing NIC cards just to try to see what was what.

I think I have the changes that the other guy recommended at home in the command line buffer.  I'll look for them tonight and post.  Maybe they will help you (kingedwin).  I can probably spend some time on it tonight, but am pretty busy in general.  My brother is anxious to get things up and running so we may just have to deploy an extra XP liscense we have (double argh.)

---

### Post by Slim Odds on 2006-06-13
[quote=mercenary]I haven't played around with just the DHCP trying to get machines talking to each other.  From what I read, I thought impementing Firestarter would be a cake walk and that it would take are of DHCP. [/quote] 
Firestarter works just fine.

Internet Connection Sharing requires a few things:
1) An upstream network connection to the Internet (static IP, DHCP, doesn't matter)
2) A downstream LAN (usually provided by running a DHCP server, but can be done with static IP and manual DNS and gateway).
3) IP forwarding must be enabled
4) NAT must be used on connections coming from LAN to upstream Internet (iptables)

You can do all this manually, or you can use something like Firestarter.

---

