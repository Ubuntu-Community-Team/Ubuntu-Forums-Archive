---
title: "Home Network :unable to see &quot;share&quot; in network browser is Lisa daemon required ?"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2009-09-09
Afternoon folks,
I have a Fedora box which is running a Samba server and I can access a specific share with no problems. My usual method is :
```

unclec@unclec-desktop:~$ smbclient //192.168.**.**/fedora-share
Enter unclec's password: 
Domain=[FEDORA] OS=[Unix] Server=[Samba *********]
smb: \> 


``` 

Or I can go into nautilus and enter the following in the location bar :

```
smb://192.168.**.**/fedora-share
```

My question is, if I click on Panel --> Places--> Network I cannot see my Fedora box or fedora-share, even when I have mounted the share. Do I need to install the Lisa daemon to allow for network browsing or recognition of my other networked computers via nautilus network browser ? Perhaps I need to make adjustments on my Fedora box ( smb.conf file) so it can be "seen" on my Ubuntu. I can ssh / ping  between both machines.

Thanks.
C

---

