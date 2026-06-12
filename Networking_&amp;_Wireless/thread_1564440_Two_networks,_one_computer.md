---
title: "Two networks, one computer?"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by SeanMacE on 2010-08-30
Hey guys. I have been watching the forum for a while, but this is my first post. (I think it's my first post in a forum actually... ever...) That said, I have run into an issue with networking that I can't seem to get around.

I have two networks, linksys and dlink. The linksys network is wired. On it I have one computer that is 100% Ubuntu, one laptop that is 50/50 Ubuntu/Vista, a desktop that is currently 100% Windows 7 64bit (going to set up some type of server with either Ubuntu or fedora on that one), my office printer/fax/scanner, and a 1TB NAS from western digital. The Dlink is wireless and is connected to our cable modem. Because of my office location I can't run Ethernet between the two networks and for security I need to keep the NAS off the, but it wasn't an issue b/c I have wireless cards in all the computers. The problem is that when I enable the Ethernet connection with the wireless network up, I can no longer get out on the internet. I can ping both routers, but that's all I can do. So I have been having to switch nic's on/off depending on what i'm doing. It's a pain to say the least. Is there any way to run both networks simultaneously?:confused::confused::confused:

Here are the specs on the networks:
Dlink (wireless)
IPV4: 192.168.0.103 
subnet: 255.255.255.0
gateway: 192.168.0.1

Linksys:
IPV4: 182.178.1.3
subnet: 255.255.255.120
gateway: 182.178.1.1

I was planning on assigning static IP's on the wired LAN. My other problem is I'm pretty new to the Linux world, so I'm not even sure where to start on the two Linux computers.

Thanks for any help anyone can provide. This has been driving me nuts for a while.

---

### Post by i.r.id10t on 2010-08-30
Only set one default gateway...

---

### Post by SeanMacE on 2010-08-30
> **i.r.id10t said:**
> Only set one default gateway...
Thank you for the quick response. Do you mean leave the gateway address blank in the Ethernet NIC's configuration settings, or should I try and use the same gateway for both configurations?

---

### Post by pricetech on 2010-08-30
Leave the gateway blank, or set to 0.0.0.0, on your wired NIC.

That's based upon my understanding of your description above.

---

### Post by Iowan on 2010-08-30
More than one gateway (even pointing at the same address) will probably confuse the beast (machine?).

---

### Post by SeanMacE on 2010-08-30
That seems to have done it. Thanks for the help!

---

### Post by glennvan on 2011-10-07
So I have the same idea, but different equipment and issues.
The wired is connected to a dlink 655 (with the wireless turned off) which had 2 WD MyBookWorld connected.  I only want my wired connection to access the dlink.  Fine and dandy, mostly works.
The wireless connection is the way to the internet and network printer.  This works fine and dandy if the wired connection is physically unplugged.  With the wired plugged in, sometimes the web works, other times not so much.
Its not a huge deal to get the wired working all the time, but I just would like it to be proper.  I have manually assigned my wired connection to get the dhcp address only, and in the routes setting, I have the ignore automatically... and Use the connection... both checked.
In the wireless both these options are unchecked...

---

### Post by glennvan on 2011-10-08
UGH, I fixed it. It works a whole lot better (like all the time) when the connections are on separate ip ranges...[-X[-X[-X

---

### Post by Iowan on 2011-10-08
From Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

