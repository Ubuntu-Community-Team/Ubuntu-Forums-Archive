---
title: "LinkAggregation / Port Trunking with 8.04 LTS"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by batfastad on 2009-07-10
Hi everyone

Right this has been driving me crazy.
I'm looking to do mode 4 link aggregation (per this page [https://wiki.ubuntu.com/LinkAggregation](https://wiki.ubuntu.com/LinkAggregation))
My switch is a Netgear GS724T which apparently supports port trunking according to the manual and the web interface

However I'm getting very inconsistent results. With some computers only able to ping when 1 of the 2 ports are unplugged from the switch and other weirdness.
I've followed this guide... [http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly](http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly)

But I was wondering if anyone has any further more detailed guides?
The motherboard is a pretty recent Tyan model bought about 6 months ago with 2 Gigabit NICs.

I still need to do more testing on this but wondered if there were any other suggestions/guides out there with more info

Cheers, B

---

### Post by batfastad on 2009-07-12
The motherboard is a Tyan s5211 based on an Intel 3210 chipset [http://www.tyan.com/product_board_detail.aspx?pid=591](http://www.tyan.com/product_board_detail.aspx?pid=591)
From the specs in that link the LAN is 2 Intel 82573 ports.
In the manual it says 2 Intel i82573 GbE NICs (1*82573V+1*82573L) operating at independent PCI-E x1 interface.

Do these NICs/LAN controller support 802.3ad?
Do I need to dig out specific drivers for Ubuntu?

I havn't installed any chipset-specific drivers for this motherboard as the NICs appeared to just work out of the box once I installed Ubuntu.
I assume the NICs support it but do I need to install some specific Intel drivers to get this working fully?

Thanks, B

---

### Post by batfastad on 2009-07-13
Ok I had another play this evening once everyone had left for the day and can report further on the inconsistencies I was getting.
I removed the daisy chain switch completely and plugged everything into the new Netgear.

When I set up the bonding on the server, the server works fine. Can send and receive pings.
Other servers with static IP can send/receive pings on the bonded IP address (Windows Server 2003).
Our router firewall (IPCop) can send/receive pings to the bonded IP address.
My laptop plugged in via ethernet cable can send/receive pings to the bonded IP address.

However it all comes apart when I remove one of the bonded/trunked cables from the switch.
Everything continues to ping the bonded IP (apart from a 1 packet loss) with only 1 cable.
Restoring the cable again and everything continues to ping the bonded ip as expected... apart from my laptop and I get "request timed out" instead of a ping response (IP assigned through DHCP running Windows XP Pro SP3).
Trying to ping my laptop from the server with the bonded ip yields the same result.
But all other pings work fine... my laptop can ping all the other servers apart from the bonded ip. The server can ping everything else apart from my laptop.

Changing my laptop to static IP, renewing the DHCP lease, unplugging network cables... and still my laptop can't send/receive pings to the bonded ip.
Turning the switch off/on doesn't fix it
ifdown bond0 and ifup bond0 on the server doesn't do it.
The only way to get the laptop pinging the server again is to disable bonding/trunking and reboot the server with my regular eth0 settings.

It's not just my laptop that this happens with but also a Windows Vista laptop and a Windows XP Pro SP3 desktop machine. I'll try with a G5 mac tomorrow to see if it's an OS-specific thing.

So it appears any Windows machine configured by DHCP doesn't like the cables getting pulled out of the bonded ports on the switch.
A Windows 2003 Server and Windows 2000 Server with their IPs configured statically within windows continue to behave.

Anyone got any ideas what might be going on here?

I realise I've moved away from the original topic now but it's this inconsistent behaviour that caused me to question the daisy chain switch thing in the first place... now with the daisy chain switch out of the way I'm getting the same inconsistencies.

Any ideas?
I'd appreciate anything you can suggest!

Cheers, B

---

