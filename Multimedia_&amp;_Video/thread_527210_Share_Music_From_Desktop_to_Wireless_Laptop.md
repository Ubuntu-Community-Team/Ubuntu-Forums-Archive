---
title: "Share Music From Desktop to Wireless Laptop"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by moore.bryan on 2007-08-16
[I]could someone direct me to the best howto for doing this?  samba isn't an answer for me because, for whatever reason, it doesn't play nice on either of my machines.

specifics (as concise as i can):
machine 1: dell dimension 2350 hard-connected to netgear router, 1.6ghz processor with 1gb ram, running ubuntu server install with openbox, connected to external western digital 180gb external harddrive with the music folder i want to share.

machine 2: lenovo thinkpad z61e wirelessly connected to netgear router, 1.8ghz processor with 512mb ram, running ubuntu server install with openbox, want to connect to shared music folder.

if you need any extra info, just ask.[/I]

---

### Post by 1/0 on 2007-08-16
I would definitely install a NFS server. Check:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server)

---

### Post by moore.bryan on 2007-08-16
[I]thanks "binary," i'm trying it now.  is it normal for the nfs-kernel-server restart command to take FOREVER?

so... no dice.  my "client" tells me > mount to NFS server '192.168.1.24' failed: server is down
:mad: !!!
[/I]

---

### Post by 1/0 on 2007-08-16
It should restart quickly. What does take time is to mount the partitions, especially if they are large. That's why I've chosen not to automount.

---

### Post by moore.bryan on 2007-08-16
*well, the restart takes a long time (~4 minutes) and the mounting still fails with the error above.  any ideas?*

---

### Post by notwen on 2007-08-16
Does your server PC maintain it's ip address?  Be sure to set up a static ip in your router for your server PC.  I setup NFS maybe a week or two back using the exact same guide and I had this up and running in under 5min.

---

### Post by moore.bryan on 2007-08-16
[I]partial succes!!!  hmm... i don't know which of those words to focus on.  i suppose an optimist would focus on the latter and a pessimist the former; but, on what would a cynic focus?  ;-)

turns-out when i turn off my ubuntu-firewall on the "server" machine, everything works hunky-dory.  PROBLEM!  i don't want to turn it off.  so i checked all the nfs-related help guides and nothing mentions anything about firewall issues.  i read up on all the nfs port info and unblocked all of the ones which looked like they needed to be unblocked, but still nothing.

help?[/I]

---

### Post by moore.bryan on 2007-08-16
[I]COMPLETE SUCCESS!!!
thanks for your help/assistant folks... i binded (is that even proper grammar?) ports on the host machine, so as to allow me in.  sweet music to my ears![/I]

---

### Post by notwen on 2007-08-16
From what I've briefly reads NFS uses random ports for the actual data transfer.  [Here]("http://www.lowth.com/LinWiz/1.09/notes/nfs_help.php") is a page showing you how to tie NFS to specified ports.  It says it is written w/ reference to Red Hat 7.x and 8.x system, but should work fine w/ other Linux distributions.  This is probably alot more than you expected to do be doing, but fi you do go ahead and assign NFS to specific ports, please post back and let us know our progress/results.  As always, hope this helps.  =]

---

### Post by notwen on 2007-08-16
Lol, you got it working as I was posting, grats and I'm glad you got it to work, could you toss a link to show which ports you binded NFS to or was it pretty similar to the guide I linked to above?  Gratz again. =]

---

### Post by moore.bryan on 2007-08-16
> **notwen said:**
> Lol, you got it working as I was posting, grats and I'm glad you got it to work, could you toss a link to show which ports you binded NFS to or was it pretty similar to the guide I linked to above?  Gratz again. =]
[i]as with most port-security issues, i just randomly chose a number of ports and specified them in the /etc/default/nfs-common, /etc/default/nfs-kernel-server, and /etc/modprobe.conf files.
;-)
[/i]

---

### Post by moore.bryan on 2007-08-17
*okay, new "wrinkle:" when playing my music, there are regular "burps" when the music cuts-out.  my lappie is sitting DIRECTLY next to the router... huh?*

---

