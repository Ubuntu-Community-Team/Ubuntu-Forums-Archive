---
title: "XP won't find my Ubuntu machine"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by flash722 on 2010-01-25
Hi everyone,

New to linux networking.  I think I'm missing something small though.  I have a home LAN running a desktop with XP, another laptop with XP, a network storage HD, and this Dell C640 laptop running Ubuntu 9.04.  Ubuntu system can successfully do the following:

- find/utilize both wired an wireless network adapters
- find/utilize the printer connected to my XP loaded desktop
- find/access the Windows WORKGROUP systems, shared drives, and files.

Ubuntu drive is set up for sharing.

Two issues:  1. the Ubuntu system can only WRITE to a network drive intermittently (i.e. sometimes it works and sometimes not)

2. The XP systems in the WORKGROUP cannot find the Ubuntu system.


This has got to be a newbie error...  grateful for suggestions.


Best,

Adam

---

### Post by johnson.d on 2010-02-01
Please explain the following for more clarity on your setup.

1) How is the network drive mounted in the Ubuntu system? When you face the problem of access, please check if the drive is really mounted or not.

2) What file sharing method is used to share the files in the Ubuntu machine (Samba or NFS)? Please check if Samba and samba-common-bin are installed. Without these, creation of share from Nautilus would fail.

---

### Post by Iowan on 2010-02-01
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To *might* help with some of the sharing problems.

---

### Post by mudguts on 2010-02-01
quick question.. is it XP home or XP Pro?

I don't think that XP home has the networking capabilities that XP Pro does

interesting (tho older) blog post on the differences.
[link]("http://www.williamaford.com/XPHomevsXPPro.php")

---

### Post by hookzilla on 2010-02-11
I'm not an expert, but I do have a home network with both wired and wireless WinXP Home and Ubuntu machines working fine, but I had trouble initially.  You might check these things...

For WinXP to find the Ubuntu machines on the network, the workgroups must match. The default Windows workgroup is "workgroup".  When you setup your wireless router, it probably setup a different workgroup name. 

Also, your firewall must allow the addresses for the Ubuntu machines and router to pass.  This is the one that I missed.

Hope these help.  BTW, there are older posts from more knowledgeable folks that give a better explanation than I have given you here.

---

