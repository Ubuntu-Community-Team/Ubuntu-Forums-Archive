---
title: "Wired networking not working at work, fine at home..."
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by pombe on 2010-08-24
Solved by upgrading the networkmanager as per instructions [here]("http://ubuntuforums.org/showthread.php?t=1560027")

________

Hi all.  I just started having a problem with my 10.04 laptop a few days ago, maybe Thursday, last week.  When the computer is plugged into my home network (standard 192.168.1.1 sort of IPs) it works fine, but when I try to connect to my work network (130.15.90.XX) I am unable to pick up an IP.  The router in my office is working fine, all the windows boxes can connect.  

No idea where to start troubleshooting.  Any help would be appreciated.

Edit: I've also noticed that when the computer is plugged in at work the notification icon for the networking indicates it is looking for a wireless connection (rather than the normal up/down arrows), even if wireless is deactivated

Edit2: I can set a static IP in /etc/network/interfaces and everything works, so it seems to be a DHCP problem?

---

### Post by Iowan on 2010-08-24
I've marked your thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). If it isn't, you can follow the instructions to mark the thread "unsolved" (remove the [SOLVED] tag).

---

