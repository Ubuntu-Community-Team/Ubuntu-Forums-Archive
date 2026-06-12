---
title: "Where are the iptable rules loaded from (after a bootup) ?"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by erajsri on 2009-12-26
I am a n00b on Ubuntu, and generally linux. I jus got hold of a PC with Ubuntu 8.04 pre-installed on it, a few days back. I want to run this PC headless so that I can connect over SSH and work via VNC. However, each time it reboots, the firewall blocks all traffic to the box, limiting me from doing anything remotely. I have to physically login to the machine and then flush the iptable rules to run this unit headless.

When I run iptables -L after booting it up, it gives a list of rules (which is the cause for the firewall). I want to know **if these rules are loaded from a script somewhere or are the defaults from Ubuntu 8.04 ?** If so, where is the script for these rules located ? I can maybe add / edit these rules so that SSH port and a few others are accepted after a boot up ?

thanx to all, hope i get a reply soon.
erajsri

---

### Post by memilanuk on 2009-12-26
Try 'sudo ufw status' to see if ufw is running.  It may have been setup with a default policy of 'deny' which may be whats keeping you out.  You can either continue to run ufw and add access for ssh ('sudo ufw allow ssh') or disable ufw entirely ('sudo ufw disable') which will shut it down and flush its rules from iptables and not restart it again next time you boot.  Once its turned off, ufw should stay pretty much out of the way i.e. you don't really need to uninstall it.  It does work pretty well and is fairly easy to work with for simple firewalls, so it might be worth keeping around.  Try searching the Ubuntu Community Docs for more detailed info on ufw configuration.

HTH,

Monte

---

### Post by erajsri on 2009-12-26
I have disabled ufw long time ago (that is a few bootups  ago), and the status command returns the following.
> Status: not loaded

Searching the net I found scripts that load the iptables in the init.d directory etc and was wondering if my PC came with one such as default and Im unable to override it ? Right now I use that script [http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html#comment-152501]("http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html#comment-152501") by physically logging into the machine and running from the prompt.

---

### Post by memilanuk on 2009-12-26
Hmmm... I don't suppose there's any chance you can simply ask whoever pre-installed Ubuntu for you?  Otherwise I imagine there is probably a script that runs iptables-save on shutdown and iptables-restore on boot to save and reload the firewall.  How exactly they went about doing (i.e. where they placed the script, and where they referenced it from) that could vary considerably.

---

### Post by erajsri on 2009-12-27
FOund out the bug. I had installed Firestarter in my haste to get SSH, VNC up and running and accidentally set ALL incoming TCP traffic as "not permissive by default" (or something to that effect). Stopped firewall in Firestarter and ran iptables -L to return with no rules. 

thanx for the help.
eraj.

---

### Post by memilanuk on 2009-12-27
Cool.  Perhaps it would be appropriate to change the title to [SOLVED]?

---

