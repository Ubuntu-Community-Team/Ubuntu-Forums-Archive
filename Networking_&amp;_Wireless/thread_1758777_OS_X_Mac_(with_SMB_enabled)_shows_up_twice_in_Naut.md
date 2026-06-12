---
title: "OS X Mac (with SMB enabled) shows up twice in Nautilus"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by jtfolden on 2011-05-15
I have a small issue that's annoying me greatly at the moment.

On my upstairs network I have two computers. One is a Mac running OS X 10.6.7 and the other is a dual-boot system with both Ubuntu and Fedora. I have enabled Windows sharing on the Mac (which uses a static ip address) and installed Samba under both Ubuntu and Fedora... connecting to shares in either direction works just fine.

The problem, however, is that the Mac system shows up twice under "Browse Network" in Nautilus as "MACMINI" and "macmini"... and both list the same shares. 

MACMINI seems to use the hostname - a shared location would be smb://MACMINI/ShareA
macmini seems to the the ip address - the same shared location would be smb://192.168.1.100/ShareA

In the network browser, if I click into "Windows Network" and then "Workgroup", I see just a single system as MACMINI.

Where is the lowercase 'macmini' in the root of Browse Networks coming from????

I've seen this under Ubuntu 10.10 and 11.04 using Gnome 2.x and also see it under Fedora with Gnome 3.

Any help would be greatly appreciated.

---

