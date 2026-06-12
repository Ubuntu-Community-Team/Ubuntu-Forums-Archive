---
title: "Manual wireless not working in 9.04"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by MrCode on 2009-07-30
Hi, all.  I'm trying to get my desktop machine (that has 2 OSes, Windows XP and Ubuntu 9.04) to connect to my home wireless network manually.   I'm using a Netgear WN111v1 USB adapter with NDISwrapper and the Windows drivers, and I'm using Ubuntu's default NetworkManager applet to try and get connected.

The wireless network is WPA2 encrypted, if that makes any difference.  The thing is, I can seem to get a router connection, but I'm unable to ping anywhere, even the router itself.  If I try to ping anywhere, it just comes back "Destination Host Unreachable".

Here are the settings:

DNS Servers: 208.67.222.222, 208.67.220.220 (these are the OpenDNS IP addressses)

No matter what I do to these settings, it simply won't get a net connection.  What else am I supposed to do??  Is there a command line tool that I need to use?

Also, it is *because* I'm using a desktop machine that I'm *inherently* unable to connect?  I've heard a lot more success stories from laptop users than desktop users...although I don't see why it would really make much difference.

EDIT: The adapter works perfectly in XP, that's how I'm posting this... :mad:  I hate it when no one provides native Linux support for wireless...  The Windows software installs this "Netgear Smart Wizard" software that gets you connected...Maybe I should try installing the Smart Wizard thing under Wine?  Although I would be very surprised if it worked, seeing as how Wine isn't exactly complete...

EDIT EDIT: Err...I guess you're not supposed to post your personal IP address on an online forum...  Deleted.  But I assure you that I have the correct settings.

---

### Post by Crafty Kisses on 2009-07-30
What are the results of the following?
```
route
```
Depending if you're using DHCP, you might need to run:
```
dhcpdcd -d eth1
```
Try running that and see if that works.

---

### Post by MrCode on 2009-07-30
The output is as follows:

route output:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```dhcpcd -d eth1 output:

```

info, eth1: dhcpcd 3.2.3 starting
err, eth1: ioctl SIOCGIFHWADDR: No such device
info, eth1: exiting

```Although this doesn't surprise me, considering I'm using wlan0, not eth1.

I had to install dhcpcd before I could do the second one.  Also, I'm using a manual connection, not DHCP.  I can't get DHCP to work at all for me.  It keeps sending DHCPDISCOVER requests only to receive nothing, and drops out after attempting.

---

### Post by Iowan on 2009-07-30
What is the router address - 192.168.1.1?

---

### Post by MrCode on 2009-07-30
Yes, I believe so.  Is that just a default or something?  Is there something that I need to determine manually that I haven't already got?

I have the computer's IP, the netmask, the DNS server(s), and (I think) the gateway.  Isn't the gateway the address of the router?  Or is it something different entirely?

Perhaps I should also mention that the router is a Netgear as well, if that makes any difference.  According to the packaging and user guide, though, the router is Linux-friendly (supposedly).

---

### Post by Iowan on 2009-07-30
> **MrCode said:**
>   Isn't the gateway the address of the router?  Or is it something different entirely? My guess would have the router as the gateway...

---

### Post by MrCode on 2009-07-30
Ok, that's about what I figured.  As for the netmask, it's usually all 255's except the last octet, right? As in 255.255.255.0.  And I'm really not sure about what you're supposed to put for the IP address, but I figure it would be in the format 192.168.1.x, right?

---

### Post by MrCode on 2009-07-30
Ok, I've determined that it can't be that my configs are corrupted, because the exact same thing happens in the Live CD.  Is there something that I need to install other than ndiswrapper?

---

### Post by MrCode on 2009-08-01
UPDATE:  I've been noticing a slight trend:  I can *sometimes* get connected, but only sometimes.  Then when it disconnects me (probably from lack of network activity), it reconnects, but I can't ping, but after a while, it disconnects again, then reconnects, still can't ping, disconnects, etc., etc., until it finally comes back to a full connection again.  I'm noticing that it takes a substantially shorter time to connect when it gets a full net connection.  I'm thinking what I'll do for now, until someone can offer me a better, more permanent solution, is to have a constant ping running in the background, just to the router, to keep the network activity from dropping to zero.

Is this a phenomenon that other people have experienced?

---

### Post by MrCode on 2009-08-04
bump...help...please?  Does anyone have the same thing happen to them or similar?

---

