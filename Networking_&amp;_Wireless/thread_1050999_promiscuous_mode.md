---
title: "promiscuous mode"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by minie on 2009-01-26
computer: asus eeepc 901
distro: eeebuntu standard (wasn't a prefix option, but i believe its just ubuntu with eee drivers)

i'm having trouble with wireless packet capture in wireshark. when i check my wifi mode in terminal, it says i am indeed in promiscuous mode, but i can only collect traffic i generate from my eeepc and router. i send irc and http packets from another computer while connected to the same router, but my eee doesn't see them.
i've heard that the chipset used in netbooks (mine included) don't support packet injection. could this affect promiscuous mode? could promiscuous mode not be the issue?
and a thank you in advance.

---

### Post by puppywhacker on 2009-01-26
promiscuous mode means that the networkcard will not discard information it receives which is not intended for it. So with wireshark you can look at all packets that are on the wire.

A router however will only route packets intended for you on the wire, so you will never capture packets between to other nodes.

packet injection has to do with sending and promiscuous with receiving.

---

### Post by minie on 2009-01-27
yes, i know what promiscuous mode is.
both the eee and the computer i am trying to generate packets on are connected wirelessly

---

### Post by sedawk on 2009-01-27
I never tried this with wireless LAN, but is it possible that you
cannot see "foreign" packages, especially if your WLAN is crypted.
What you might need is another low-level driver to
capture all wireless traffic, not simply promiscious mode.
You might search for "wardriving ubuntu" on the web but keep in mind
that you might be crossing the border between legal and illegal actions 
depending on what country you live in!

---

### Post by timcredible on 2009-01-27
are you running wireshark as root?  if not, it won't work.  go to a terminal and type ```
su wireshark
```

---

### Post by jonobr on 2009-01-27
> su wireshark

hey you missed the do

su will try to switch user wireshark

should be > sudo wireshark

:-)

---

### Post by minie on 2009-01-28
ya, i'm root. it actually wont let me see my interfaces unless i'm root

---

### Post by minie on 2009-01-29
bump

---

### Post by jonobr on 2009-01-29
Hello

I had to go back to my windows machine to see if I was doing something wrong.,

When you go to capture->interfaces in wireshark,
Im guessing you see the interface- wired and wireless.
Do you see the packets incrementing in teh Packet Packets/s fields before you hit start?
DOes IP show an IP address or unknown?

Are all 3 fields greyed out?

WHen you select options Do you have Capture packets in probiscous mode checked or unchecked?

I just checked my wireless version of wireshark and it captures the packets when its unchecked and doesnt when its checked

---

### Post by blkmax on 2009-01-30
Hi, not sure about WireShark as I run SNORT. In order to be able to sniff all packets on your network, your switch Port (The port you sniffing computer is on) needs to be set as a SPAN port so that all packets can flow through. Otherwise, you will only sniff what is on your local network up to your switch.


Regards

Marc

---

### Post by patrickk on 2009-07-21
Hey guys,

I have an eee pc 901 with a nice clean install of ubuntu netbook remix on it (9.04) and I'm having a bit of trouble using it to capture packets in promiscuous mode. I was playing around with it and remembered using Wireshark while in school so I installed it just to relive the days of pulling down massive amounts of network traffic.  Unfortunately, I haven't been able to get the darn thing to pull promiscuously.  I have tried manually enabling promisc mode via a shell and via the menus within wireshark.  I ran tcpdump and had the same problems.  I can see the broadcast traffic of the 2-3 other wireless devices on my home wireless network, but no TCP traffic (I'm running general web traffic on a laptop next to the eee and I'm not seeing any of it).

Any ideas?  Not that it's the end of the world, but I refuse to be beat by a cute little eee.  Am I missing something?

---

