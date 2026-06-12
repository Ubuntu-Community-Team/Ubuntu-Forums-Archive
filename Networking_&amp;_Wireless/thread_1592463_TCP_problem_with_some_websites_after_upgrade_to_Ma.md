---
title: "TCP problem with some websites after upgrade to Maverick"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by snmishra on 2010-10-10
I am having trouble connecting to [http://talkingissues.economist.com/](http://talkingissues.economist.com/) from my Dell D620 laptop running Ubuntu Maverick. Before the upgrade, things seemed to work OK. I can connect to the same website from Windows XP running on the same laptop inside VirtualBox using bridged networking.

Looking at the TCP packet dumps in wireshark, everything looks OK, except the Ubuntu side never generates an ACK. I tried reading forums and playing with various net.ipv4.* parameters using sysctl to no avail.

I am attaching a merged dump for TCP connections from Ubuntu (192.198.97.253) and Windows XP (192.198.97.254) to the above website.

I humbly ask for any help or pointers on how to debug this.

Edit:
I just got it to work by disabling the "Block traffic from reserved addresses on public interfaces" option in Firestarter->Advanced Options.

Satya

---

