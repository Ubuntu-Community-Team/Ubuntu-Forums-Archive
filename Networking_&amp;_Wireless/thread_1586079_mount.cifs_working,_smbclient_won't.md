---
title: "mount.cifs working, smbclient won't"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by luvshines on 2010-10-01
Came across a strange Samba server setup to which I can connect using 'mount -t cifs' command without any issues

But smbclient -L fails with error:
Domain=[MYGROUP] OS=[Unix] Server=[Samba 3.0.28-0.el5.8]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: NT_STATUS_ACCESS_DENIED

Also, I can't access the share through my windows machines

Is there anything I can try changing from client side ??
Can nebody give any pointers as to what can be wrong

The server is at remote location and I would have a hard time checking the smb.conf file settings and changing them.

---

### Post by Morbius1 on 2010-10-01
Try adding what the error message suggests to your own smb.conf:
In the [global] section add:

```
client lanman auth = Yes
```

---

### Post by luvshines on 2010-10-14
> **Morbius1 said:**
> Try adding what the error message suggests to your own smb.conf:
In the [global] section add:

```
client lanman auth = Yes
```

I wish I could do that, but the issue is that I don't have access to the server.
It is at some remote location, on the office network and owned by someone else

I was just wondering, what magic mount.cifs is doing which smbclient and windows machine are unable to do
So I was thinking of some tweaks on the client side itself to make it work

---

### Post by Morbius1 on 2010-10-14
The server , for whatever reason, is asking for a lanman type encrypted password. "client lanman auth" is something you add to the client to allow it to authenticate to a server requesting a lanman password. Without it the password sent by the client will be encrypted in a format the server does not understand.

That's the way I understand it anyway.

---

