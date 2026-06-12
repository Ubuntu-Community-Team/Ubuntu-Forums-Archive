---
title: "Easiest / best way to quickly share files with Windows clients on the LAN"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by jago25_98 on 2010-12-13
Here I am editing /etc/samba/smb.conf and trying to remember what I should chmod the directory and the files to, then I think to myself

 there's probably an easier way. That way should be clear to the user. 

 There's dropbox and Ubuntu one but these are something slightly different, these sorts of things involving a cloud service or something needing to download to Windows clients, which is not what we want if we don't have an internet connection. 

 So, is there a better way? Something to aide making smb.conf and permissions perhaps?

---

### Post by pricetech on 2010-12-13
How about a way that doesn't involve manual editing at all?

Install, via Synaptic, system-config-samba which will install not only Samba itself but a nice GUI tool to configure Samba with.

You'll find the toll in System - Administration - Samba.

Configure everything there.

Piece of cake.

You might run into an issue I've seen a few times where, for whatever reason, you have to go to a command line and enter;

```
sudo smbpasswd useername
```

then give it the password for "username" before it starts working.

Not sure what causes this nor why it doesn't affect every install.

---

