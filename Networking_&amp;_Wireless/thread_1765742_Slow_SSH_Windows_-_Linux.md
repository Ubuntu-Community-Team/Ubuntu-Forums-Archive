---
title: "Slow SSH Windows - Linux"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by puetti on 2011-05-23
Hi everyone,

this is not really an Ubuntu question but rather a general Linux SSH protocol one. However, I know there are a lot of competent guys round here, so I'm posting it here.

We've been discovering slow network speeds in our company when connecting from Windows PCs to Linux servers via SSH protocol. We have tried different clients like Putty and Windows SSH Secure Shell.

While between the Linux machines we achieve exactly our theoretical network limit of 100Mbit/s, the performance is only approximately 30 to 40% of that in the case of Windows/Linux connections. And very interesting: The speed may even go down to a few KB/s, if another Linux machine requests a file from the same server at the same time. Linux/Linux connections seem to be always preferred over Windows/Linux ones.

I have googled quite a bit on that issue and found that we are definitely not the only ones experiencing such problems. However, it surprises me that no one seems to know a fix, since such speed problems have been reported for years already. Is nobody working on solving these things?

Maybe, is there anyone around here who could give some hints on what to try to fix it? Could adjusting configuration of Windows SSH clients (or maybe also Linux SSHD) help to increase speed? I have tried activating compression with no success.
Besides, I'd be especially interested in where this apparent higher priority of Linux/Linux connections may come from. Any help would be greatly appreciated!

Ah, by the way: For simple file transfer, Samba works perfectly between Windows and Linux (i.e. 100% network speed). However, we need high speed connections via SSH for remotely running applications on the Linux machines.

Andreas

---

