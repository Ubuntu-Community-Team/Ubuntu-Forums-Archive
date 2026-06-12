---
title: "How to automount nfs shares"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Savita Eli on 2009-08-03
[SIZE=2]Hi I want automount nfs shares.

Here are the details:
Server:
---------
Share contents: /dir1/dir2/sub1, /dir1/dir2/sub2 & so on
Server /etc/exports:
/dir1/dir2 *(rw,sync)

Client:
--------
1) mount sub1 in [/SIZE]  [SIZE=2][COLOR=Red]/dir1/sub1 (Not as /dir1/dir2/sub1)[/COLOR][/SIZE][SIZE=2]

This should be done using autofs.

How to do this???[/SIZE]

---

### Post by dmizer on 2009-08-03
Have a look here: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by Ozdemon on 2010-01-31
> **dmizer said:**
> Have a look here: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Yes I have looked at that and get stuck at
NFSv4

> If your NFS shares use NFSv4, you need to tell autofs about that. In such a case, the above line would appear as follows:

server   -fstype=nfs4   server:/ 

I do not know what to put here.  For example do I enter

IP of server   -fstype=nfs4 server directory holding file e.g. /home/Videos

Without an actual example I cannot work out what the help page means

I am able to manually mount the required directory on the client machine.  I just want to be able to have that automount as the machine is my daughter's and she is not up to terminal commands yet.  

I have spent nearly 2 hours trying to work this out, so I hope someone can help.

---

### Post by dmizer on 2010-01-31
According to the howto, the format is: {mount point} [{mount options}] {location}

So your /etc/auto.nfs file would look like:
```
mount-name -fstype=nfs4 server.ip.address.here:/path/of/shared/directory/on/the/server
```

Where "/path/of/shared/directory/on/the/server" matches the path located in the /etc/exports file on the nfs server.

---

