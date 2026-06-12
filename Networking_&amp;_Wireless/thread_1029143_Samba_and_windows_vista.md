---
title: "Samba and windows vista"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by ravi.xolve on 2009-01-03
My friends on local LAN use windows Vista. I use Kubuntu 8.10.

I installed samba 3.2.3 on my machine and created the following smb.conf file:

```
[global]
workgroup = J358
netbios name = Ravi
security = share

[data]
comment = Music
path = /media/sda3/Music
read only = Yes
guest ok = Yes
```

I configured their local network to the workgroup name "J358" and turned on file sharing on their PCs from "network and sharing center" in conrol panel.

When I went to Start -> Network I couldn't find my machine listed there. I googled and found that Vista uses NTLM authentication and I need to change Vista's settings to LM and NTLN from secpol.msc .
But this article says different about the newer versions of Samba: [http://blogs.zdnet.com/Bott/?p=236](http://blogs.zdnet.com/Bott/?p=236)

Also I can't see Vista's shares on my computer. Please help me.

---

### Post by ravi.xolve on 2009-01-04
I figured out the problem a bit. I can use

smbclient -L <ip of win  vista pc> and see the services available there.

On windows vista pc I click on "map network drive" in my computer and create a drive M: with the folder path as 

\\<ip of my linux machine>\data\

However when I click on the networked drive at windows I get the access denied error. Why this is so as I have set the usage of my share in the sm.conf file to allow reads by anyone?

Also why I can't just use netbios names, why others can't see my compter directly in GUI on windows vista? These things are kinda hurting.

---

