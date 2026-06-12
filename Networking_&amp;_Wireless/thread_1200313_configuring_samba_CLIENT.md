---
title: "configuring samba CLIENT"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by dermawan123 on 2009-06-29
Is there any way to configure samba CLIENT on ubuntu? This ubuntu system will not be sharing files, but it will access samba share on other servers.

Is there a way to configure the samba CLIENT? I need to remove the possibility of a user saving his user credentials on this public ubuntu client.

---

### Post by swerdna on 2009-06-29
> **dermawan123 said:**
> Is there any way to configure samba CLIENT on ubuntu? This ubuntu system will not be sharing files, but it will access samba share on other servers.

Is there a way to configure the samba CLIENT? I need to remove the possibility of a user saving his user credentials on this public ubuntu client.

If the other servers are using standard broadcast name resolution, then if you edit the file /etc/samba/smb.conf so it has these contents:
```
[global]
workgroup = WORKGROUP
netbios name = NETBIOS_NAME
server string =
name resolve order = bcast host lmhosts wins
preferred master = no
os level = 20
```
Then you will have a Samba client.
    Notes:
     &#8226; Before you edit smb.conf, back it up in case you want to revert to the original later
     &#8226; WORKGROUP must be common to every machine on the LAN. (check against the other computers)
     &#8226; Change NETBIOS_NAME to a unique name that will identify this computer on the LAN

---

### Post by dermawan123 on 2009-06-30
Thank you for your reply, swerdna.

First of all, I don't want to change the server, because there are other linux/windows systems on the network that need to remember password forever. Just a select public area computers will not need to remember password.

I have no problems connecting from any of the clients to the server. But I need this specific ubuntu client, with the specific user "public" to not be able to remember password forever. Another user on the same ubuntu machine, will need to remember password forever.

The samba configuration need to be user-specific on the same machine. Is this possible?

Also, would u care to explain what this code do:

```
[global]
workgroup = WORKGROUP
netbios name = NETBIOS_NAME
server string =
name resolve order = bcast host lmhosts wins
preferred master = no
os level = 20
```

---

### Post by swerdna on 2009-06-30
Samba client is an expression in samba parlance that refers to a machine that is configured to access a samba server. The code that I gave yo uwill configure a machine (not a person or a user) to be a samba client (machine).

If you want to make a special configuration for a user with the usename billybob, then add this line into the [global] stanza of smb.conf:
```
include = /etc/samba/smb.conf.%u
```
Then add a file called smb.conf.billybob into the directory /etc/samba/, and put the special conditions for billybob into that special file.

BUT -- regarding forgetting a password, I don't know anything about that, not heard of it before, maybe some others do.

---

### Post by dermawan123 on 2009-06-30
I see, so it is possible to differ samba configuration per user. I will not this for now. But what i want is to not be able to remember password. Thank you for the invaluable information you provided.

I will be back when I've found something regarding this.

---

