---
title: "Blocked ports with jaunty"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by thumper13 on 2009-04-25
Greetings.

I've just upgraded to jaunty, and everything went without a hitch.. However.. I am a WoW player, and I play other games as well (mostly through Wine) and I am having an issue with the ports being closed that the online play needs.

For example, installing the patches for WoW (rather large files) has been a headache. I contacted blizzard about this, and was told that 6112, 3724, and 6881 through 6999 need to be open ports. I used a tool at [www.canyouseeme.org](www.canyouseeme.org) which tells me if the port is available and open. The IP address listed is mine, and if I try to look up any port, it says the port is closed still.

I do not use a router, however my router/modem combo that my stupid ISP sent me has my computer on DMZ mode (I've also tried manually inputting the ports and forwarding to my machine, to no avail). My other computer (running Xubuntu intrepid, as I haven't got around to updating) is working fine, and [www.canyouseeme.org](www.canyouseeme.org) says the ports i have forwarded are open. I also spoke to 2line about this lovely piece of... "equipment" earlier today, and they believe the issue is not with the router (of course, since I use linux...) and it's the operating system... (That irritates me... blame the pc, not the garbage equipment, because it's DIFFERENT!.. another rant for another day).. 

And so, Ubuntu community, I turn to you for support. 2line is convinced the problem is ubuntu, and they arent gonna help unless i consult ubuntu.

I have tried using gufw (as well as Firestarter) to disable the firewall completely (if I can get the ports opened with the fw disabled, i'll start on that fish later). 

When I type in "sudo ufw status" it returns:

Status: Inactive

I'm no computer expert, but it makes logical sense that if the firewall is disabled, it matters not what is in the iptable. However, the following is the result of punching in "sudo iptables -L" at the terminal.

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Another interesting thing is that I've had no problem with intrepid while playing wow, etc.. Rather than just update the os, I chose to format the pc and reinstall jaunty clean.. This is the only reason I'd think the issue is jaunty and not my hardware..

Currently, I'm working on getting WoW and Warcraft III working, and as posted above, it requires these ports open. 


Any suggestion is greatly appreciated.

--Thumper

---

### Post by thumper13 on 2009-04-27
Bumped for great justice! Anyone got an idea?

---

### Post by omelette on 2009-04-30
For what it's worth, after a fresh install of Jaunty, I got the same "inactive" when querying UFW's status.  However, both Hotmail and Yahoo mail-services were completely screwed-up, whereas they worked ok with Intrepid.  I initially thought this had something to do with my WEP-enabled internet share, However, long-story-short, having got up the courage to re-install Firestarter firewall front-end again - this time on top of a working WEP connection - I find that both Hotmail & Yahoo-mail have magically started working properly again!  I basically just added the shared-IP address and every service on offer in both the inbound and outbound policy menus.

Thing is, even with Firestarter installed and the firewall active, UFW still returns as "inactive" from the terminal, so maybe it is more than a front-end for UFW.  One thing for sure, UFW does appear to have been 'interfering' somehow, despite being "inactive", and Firestarter appears to have sorted my problems out...

---

