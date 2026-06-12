---
title: "Control Centre crash - Propritary Codecs"
date: 2007-11-11
forum: Mythbuntu
---

### Post by Sir_Ty on 2007-11-11
Running latest 7.10.
Using the Mythbunutu Control Centre Proprietary Codecs tab.  I've checked the "Enable w32 Codecs" and clicked Apply.  It throws up a status bar and downloads file 1 of 3.  Updates to Downloading at 53.8kb/sec, churns for a few seconds, then the status bar and the Control Centre disappear completely.  Problem is repeatable, even after reboots.  I was however able to get the libdvdcss2 installed by itself.  Not sure if there's a log file for the control centre that I can look for to try and research the problem, doesn't seem to be under /var/log/mythtv/.

TYIA for any info.

---

### Post by tgm4883 on 2007-11-11
Is this a 32-bit system or 64-bit system?

---

### Post by roseway on 2007-11-11
Use Synaptic to install w32codecs. This fixed the problem for me. When I used Synaptic I was asked to insert the installation CD to install some of the dependent packages, and I guess that this is the bit which the Control Centre utility can't handle.

---

### Post by Sir_Ty on 2007-11-11
32bit system.  

I may try the workaround Roseway has posted, but I'd like to try browsing the logs myself also.  For my knowledge you see. :)

---

### Post by Sir_Ty on 2007-11-12
Does anyone know where the log from this type of crash would go?

---

### Post by superm1 on 2007-11-12
Reported already:
[https://bugs.edge.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/156471](https://bugs.edge.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/156471)

Put your mythbuntu CD in, and it installs a few things from there in the process.

---

