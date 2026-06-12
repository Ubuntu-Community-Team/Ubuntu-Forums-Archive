---
title: "Samba correct installed but not connection with Win XP client"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by kekovski on 2011-06-02
Hi,

I want to install a samba network with Ubuntu Server 10.04 and a Win XP client.

I did these steps:

I installed virtual box.
I installed Ubuntu Server 10.04 on VB and i did these configurations:
1: sudo apt-get install samba
2: /etc/samba/smb.conf 

> workgroup = WORKGROUP
 security = user

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
3: sudo mkdir -p /srv/samba/share
4: sudo chown nobody.nogroup /srv/samba/share/
5: sudo restart smbd
6: sudo restart nmbd
7: I checked my ip with  "ifconfig"

> inet adr: 10.0.2.15 Bcast: 10.0.2.255 Mask; 255.255.255.0  


Then I started my WinXP sp2 client op virtual box.
I checked my IP and workgroup 
cmd --> ipconfig 

> Ipadres: 10.0.2.15
Mask: 255.255.255.0

> werkgroep: WORKGROUP

Afther that I typed on my brower "\\10.0.2.15\share\". But I always get an error. The error says that he couldn'f find the path. :confused:

What am I doing wrong? 

Sorry for my bad English :)

---

