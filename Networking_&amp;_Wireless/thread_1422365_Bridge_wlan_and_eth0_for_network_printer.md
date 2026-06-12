---
title: "Bridge wlan and eth0 for network printer"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by aceracer24 on 2010-03-05
I have searched and searched for some sort of fix for my issue and nothing I have tried has completely worked out. 

Here is the setup so far:
Main PC running Ubuntu 9.10 with one wireless card and one built in nic. PC is connected to DLink router by wireless connection. 

HP network Printer/scanner connected to Main PC by built in nic using normal cat 5, not a crossover cable.

What I want to happen:
I want to be able to connect to the printer from all of the computers on my network. All other computers are Windows computers. 

What is actually happening:
By using Network Manager, I can get the Ubuntu PC to see and use the HP printer when I tell Network Manager to set eth0 to "share with other computers". However, when I do this, it sets the IP of eth0 to 10.42.43.1 and I have to set the Printer to the same sub net of 10.42.43.X. 

None of the other computers on my network are able to find the Ubuntu PC much less the printer. The subnet for all of the other PCs in the house, including the Ubuntu PC are 192.168.0.XXX. The Ubuntu PC can see the other Windows PCs and can connect to the internet just fine. 

Now using what I know from the above, I told network manager to set eth0 to manual and changed the IP address to 192.168.0.2 and changed the printer back to 192.168.0.103. This still works to the point that I can still print to it from the Ubuntu PC however, this method prevents any traffic from getting beyond the ubuntu PC. I can't ping outside of it unless I disable eth0. The wirless card shows still being connected but no traffic can get past it to the router. 

What I did previously to installing Ubuntu:
This Ubuntu PC had Windows 7 RC. WHen i expired I installed Ubuntu. Anyway, when it was Windows 7, I bridged the wlan and eth0 and that "just worked". I want this to "just work" now with the Ubuntu PC.

---

### Post by aceracer24 on 2010-03-05
Bumpin for some help still.

---

### Post by r939ick on 2010-03-05
[http://www.faqs.org/docs/Linux-HOWTO/Ethernet-Bridge-netfilter-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Ethernet-Bridge-netfilter-HOWTO.html)

Section 3.

Roughly:
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 wlan0 (or whatever your wireless card is)
ifconfig br0 192.168.0.2 up
If that works out, you'll have to edit /etc/network/interfaces to make the changes survive a reboot.

Seems like and odd topology, though.  Wouldn't it be easier to plug the printer into the dlink and have it just route the other machines to the printer?

---

### Post by aceracer24 on 2010-03-06
> **r939ick said:**
> Wouldn't it be easier to plug the printer into the dlink and have it just route the other machines to the printer?

Yes it would if I had a place to put the printer and be able to route a cat 5 to the dlink without being obvious or in the way. If that was the case I wouldn't even bother with a bridge :) Thank you for the help though. I will give it a shot.

---

### Post by aceracer24 on 2010-03-06
This didn't work. This is also very frustrating. It was so simple on a win box, why must it be so cryptic and difficult on linux?

---

### Post by r939ick on 2010-03-06
> **aceracer24 said:**
> This didn't work.
Can you say a bit more about what you tried and the behavior you observed?

> This is also very frustrating. It was so simple on a win box, why must it be so cryptic and difficult on linux?In general, because the networking options are far more varied and flexible than can be supported by a simple check box.  This makes the learning curve a little steeper for the rarer cases but also makes Linux suitable for a wider variety of applications.

---

