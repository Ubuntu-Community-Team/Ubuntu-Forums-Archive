---
title: "More than Unable to Mount location... Failed to retrieve share list from server..."
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by dabirds on 2009-11-03
Part of this post is a repeat from other posts, but I did not seem to see a good answer.  First from a an Ubuntu Perspective.

When I try to open my **Network** under the ***Places*** tab, I get the familiar message:
**Unable to mount location**
Failed tor retrieve share list from server 

Digging a little deeper (yes I know this is an Ubuntu Forum), on my Mac X, systems, the "Network Option" has vanished... I cannot see either of my 2 Linux Computers or my 4 PCs.  And on my PCs, I rarely can see another PC, and can never see the 2 Linux servers or the Mac.

All devices are "pingable" with IP addressing.  The PCs can access the Ubuntu shared directories by substituting the IP address for the server name.  PC to PC directory sharing sometimes works by computer name, although the names do not appear in the Network Neighborhood.   My Mac is an island.  

But all my computers can access the internet via my cable modem.

Everything worked perfectly last week.  This happened "overnight"  I shut down all of my devices and then restarted (it's like all of the computer names are blocked).  I have tried turning off all the firewalls and that was not an issue.  

This is what my network looks like:
Cable modem 
VOIP connection
Linksys  WRT110 Router (configured with up to 22 DHCP Users)
Linksys WRT54G Set up only as an access point (fixed IP, no DHCP)
Ubuntu Desktop with Samba (Fixed IP Address)
Old Fedora Desktop with Samba (Fixed IP Address)
2 TiVo Set top boxes (Fixed IP Addresses)
3 Network Print Servers (Fixed IP Addresses)
2 laptops (DHCP, both wired/wireless)
1 Max X (DHCP wireless)
2 PCs (DHCP wired)
1 xBox (Fixed IP Address)
1 Wii (DHCP wireless)
up to 4 iPhones (DHCP Wireless)

Again, I did nothing to change my network, when everything was working.  Any suggestions?  It's like the network, as a whole, will not resolve any local IP addresses (is the router supposed to do this?).

I know there are some work arounds (I edited the HOSTs file on one of my PCs), but that is not what I want to do.  I just want it to work like it did before.  

Any suggestions?

---

### Post by Iowan on 2009-11-03
[Here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1082148") is a similar thread - dunno if it really got solved. What works for some doesn't fix others.

---

### Post by dabirds on 2009-11-03
Thanks for the note.  the Find SMB only sees my Unix computers (Mac, Ubuntu and Fedora).  It does not see any of my PCs.

---

### Post by dabirds on 2009-11-03
I replaced a tattered Cat-5 cable connected one of the N/W switches directly to the router (instead of daisy chaining the switches), and everything was back to normal.  I suspect either the ethernet switch or the cable.  I will be replacing the switch this week, but for now, everything is working!!!!

---

