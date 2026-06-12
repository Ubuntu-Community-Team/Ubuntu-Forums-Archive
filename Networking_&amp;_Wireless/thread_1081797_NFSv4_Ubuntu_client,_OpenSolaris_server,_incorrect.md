---
title: "NFSv4 Ubuntu client, OpenSolaris server, incorrect mount option was specified"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by waldobeer on 2009-02-26
Following the directions from [https://help.ubuntu.com/community/NFSv4Howto]("https://help.ubuntu.com/community/NFSv4Howto") I've been trying to use my 64-bit hardy system as an NFSv4 client.  However, I've been unsuccessful in mounting an nfs share from the opensolaris server.

```

root@client:~# mount.nfs4 192.168.1.6:/export /mnt/incoming -v
mount.nfs4: timeout set for Thu Feb 26 22:29:43 2009
mount.nfs4: text-based options: 'addr=192.168.1.6,clientaddr=192.168.1.7'
mount.nfs4: an incorrect mount option was specified
```

Taking a look at the network traffic while running this shows that the client isn't even attempting to connect to the server.  

The client is an up-to-date 64-bit hardy server.  I'm doing a non-Kerberos configuration.  I am able to mount the share on the client using NFSv3, but I need to use the ACL's provided in NFSv4.  I've also been able to mount the share using NFSv4 on another machine running OS X.

Anyone know what I'm doing wrong here?

---

### Post by jethro1138 on 2009-04-16
BUMP

This is happening to me too, connecting to an ubuntu server... anyone solve this yet?

---

