---
title: "Trouble accessing Windows 7 PC via Samba"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by Andrash on 2010-12-22
Linux newbie here... Installed Linux Mint on my laptop, trying to enable file sharing with my Windows 7 desktop. Installed Samba and performed basic configuration (set up workgroup name to be the same as on Windows, added sharing to some folders).

The windows desktop can now access the shared Linux folders, read files, etc. However, when trying to access the (windows) desktop from the (linux) laptop, the system prompts for a username and password, and using my windows credentials doesn't seem to work. Note: the accounts on two machines have two different user names and passwords, but this doesn't seem to be the problem in the windows->unix direction!

Any thoughts? thanks!

---

### Post by dandnsmith on 2010-12-23
Interesting state. I haven't got to Vista/Win7, but so far have always found more problem getting Windows to see the linux filesystems than the other way.

It's often permissions and firewall actions at the root, and the Windows tools have always been less in evidence than the SAMBA/linux tools.

Have a look at nmbclient and smbclient - they are good tools, and there is some documentation referred to [in this site](http://samba.org/samba/docs/) - troubleshooting guides.

---

