---
title: "nfs permissions problems/same username different uid/gid"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by graysky on 2009-03-13
I have two boxes on my network sharing files via NFS.  Let's call them server and client.  My problem is the permissions on the client are messed-up.  I think it is because my user has a different uid/gid on the server than it does on the client.  

Here is my /etc/passwd on the **server**:
```
squeeze:x:100:102::/home/squeeze:/bin/sh
```
Here is my /etc/exports on the **server**:
```
/share	192.168.1.3(rw,anonuid=1000,anongid=1000)
```
Here is my /etc/passwd on the **client**:
```
squeeze:x:1000:1000::/home/squeeze:/bin/bash
```
Here is my /etc/fstab on the **client**:
```
192.168.1.2:/share /mnt/share nfs defaults,auto,noatime 0 0
```
Here is a listing of the share mounted on the client:
```
$ ls -lh
drwxrwxr-x 10  100  102  138 2009-02-15 11:28 share
```

As you can see, the permissions aren't 'squeeze:squeeze' they are '100:102' which don't exist on the client and as such, some of my scripts aren't functioning properly.  As you can see in my server's /etc/export, I have tried using the anonuid/anongid options, but they don't seem to be translated to the client.  Is there a work-around via the way I am mounting/exporting the share?

---

### Post by graysky on 2009-03-14
Finally got it figured out.  Make the uid/gid match the user ON THE SERVER and add the 'all_squash' option.

Here is my /etc/exports on the **server**:
```
/share	192.168.1.2(rw,all_squash,anonuid=100,anongid=102)
```

Now I can rw to the nfs share... the owner still appears as 100:102 but oh well.

---

