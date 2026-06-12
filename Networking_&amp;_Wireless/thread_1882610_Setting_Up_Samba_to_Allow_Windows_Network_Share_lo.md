---
title: "Setting Up Samba to Allow Windows Network Share logins with User and Pass"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by shaxs on 2011-11-17
Hello,

 I built a media server using Ubuntu 11.10 to share files to my two windows based HTPCs running XBMC. My first thing I need to do is transfer all my media files from my Windows main computer to my Linux media server. I was hoping to do that through the network.

 So I installed SAMBA and using this guide here, [http://kimbriggs.com/computers/computer-notes/linux-notes/samba-setup-guide-ubuntu.file](http://kimbriggs.com/computers/computer-notes/linux-notes/samba-setup-guide-ubuntu.file) I setup my smb.conf file. I want to be able to access this share with no user name and password.

 While a few Windows 7 machines can see the linus box on the network, anytime I try to access it, it is requiring a username and password.

 Here is what my smb.conf looks like.

```
[global]
workgroup = WORKGROUP
server string = SambaServer
security = share
name resolve order = hosts lmhosts
usershare owner only = False

[TV]
        comment = Media Server TV Files
        path = /home/****/Videos/tv
        force user = ****
        force group = ****
        read only = no
        guest ok = yes
        create mask = 0755
```

Obviously **** is replaced with my linux username. 

Any ideas why I cant get this to work?

---

