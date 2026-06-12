---
title: "Nfs"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by tommy1987 on 2009-01-28
I am trying to mount some shares from my Debian server.

I am getting the following message:
mount.nfs: access denied by server while mounting

I have been able to mount these in the past on FreeBSD. It seems that I cannot mount them on my new Ubuntu install. I logged into the server and it seems that I get the same denial when trying to mount the share on the server itself. What could have gone wrong?

Any suggestions?

Cheers,
Tom

---

### Post by keenboy on 2009-01-28
1.Check that portmapper is running on the server.

2.Check /etc/exports to make sure the networking rules are correct.

3.Run exportfs -a if you edited the above.

4.Then finally run /etc/init.d/nfs-kernel-server restart.

---

### Post by tommy1987 on 2009-01-28
```
/home/user1/shared 192.168.1.*(ro,sync)
/home/user2/shared 192.168.1.*(ro,sync)
/home/user3/shared 192.168.1.*(ro,sync)
```

My /etc/exports file is as above. Can anybody spot something wrong?

hosts.allow and hosts.deny are empty.

Portmap is running and I have restarted nfs. Still no joy :-s

Cheers,

---

### Post by keenboy on 2009-01-28
Have you got the nfs-common tools installed on the nfs client machine?

---

### Post by tommy1987 on 2009-01-28
Yeah I do.

---

### Post by tommy1987 on 2009-01-28
I have got news on my problem.

I am able to get it working if I eliminate the wildcard (and specify directly the IP of the client) in the /etc/exports file. Does anyone know why this is?

Cheers,

---

