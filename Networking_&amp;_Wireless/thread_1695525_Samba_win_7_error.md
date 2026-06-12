---
title: "Samba win 7 error"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by w_breen on 2011-02-26
Ok so i'm setting up my home fileshare and i intended to use ubuntu+samba but when i share he folders using the smb.conf file windows shows me the folder but then when i click it, it says i spelled it wrong

all the data i want to share is on sda1 in the specified folders.

Heres the smb.conf file


[global]
        workgroup = WORKGROUP
        netbios name = NETWORK
        security = share
        auth methods = guest
        domain master = no
        wins support = no
  
[Audio]
        comment = Musac
        path = /media/sda1/Audio
	browsable = yes
        read only = no
        guest ok = yes

[Videos]
        comment = MOVIES!
        path = /media/sda1/Videos
	browsable = yes
        read only = no
        guest ok = yes

[Pictures]
        comment = Imagey stuffs
        path = /media/sda1/Pictures
	browsable = yes
        read only = no
        guest ok = yes

[Storage]
        comment = Backup
        path = /media/sda1/Storage
	browsable = yes
        read only = no
        guest ok = yes

---

