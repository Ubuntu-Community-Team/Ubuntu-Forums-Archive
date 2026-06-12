---
title: "Ad-hoc wireless with samba share"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by e64462 on 2013-01-20
Dear friends,

As the title suggests, I'm trying to create a wireless adhoc network between my desktop (which I want to host a samba share), and other computers in my apartment to bypass my University's draconian networking policies. 

I've successfully established the adhoc network, and am able to ping and ssh between the two connected machines. I'm currently unable to setup a samba share between them though, so I'm wondering how to proceed. The relevant section of my smb.conf file is:

> [folder]
path = /home/nick/folder
available = yes
valid users = nick
read only = no
browsable = yes
public = yes
writable = yes

I then issue:
```
sudo services smbd restart
```

but when I try to connect to my desktop from my laptop with:
> smbclient //10.10.10.1/folder -U nick

I get the error
> Connection to 10.10.10.1 failed (Error NT_STATUS_CONNECTION_REFUSED)

I'm at a loss here, any help is appreciated.

Best
e

---

### Post by e64462 on 2013-01-20
Not that this is solved, but for my purposes I ended up hacking together a different solution that doesn't involve adhoc networks. 

Thanks anyway,

e

---

