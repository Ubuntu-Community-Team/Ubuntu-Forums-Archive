---
title: "NSF4 Networking Issues"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by musendrophilus on 2011-06-16
I've been following the following Ubuntu wiki article for setting up nsf4 on my home server.

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

I've followed the instructions down to the NSFv4 Client section where I put that bit into /etc/fstab on the client computer.

I've rebooted both machines and tried to see if the network functions and it doesn't work.

First I got "Failed to retrieve share list from server".

The next time I got "DBus error, .org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already Registered"

I ran lsmod | grep nfs on the server and here's the output.
```

nfs                   274966  0 
nfsd                  241120  13 
lockd                  65605  2 nfs,nfsd
fscache                46361  1 nfs
nfs_acl                 2257  2 nfs,nfsd
auth_rpcgss            33937  2 nfs,nfsd
exportfs                3449  1 nfsd
sunrpc                193178  14 nfs,nfsd,lockd,nfs_acl,auth_rpcgss

```I ran nmap on the server from my client machine and got this output:
```

Host is up (0.00088s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs

```When I ran nmap against the client machine I got this:
```

Host is up (0.00081s latency).
Not shown: 999 closed ports
PORT    STATE SERVICE
111/tcp open  rpcbind

```Is there a finer point that I'm missing here? Running 10.10 Server + Desktop. I'm thinking the nfs client on my laptop isn't running?

---

### Post by musendrophilus on 2011-06-17
Bump

---

### Post by musendrophilus on 2011-07-02
Two week bump!

Wow, I'm surprised there's no help.

---

### Post by musendrophilus on 2011-07-09
Three week bump!

Did I offend or is this forum full of people who are using Ubuntu because they don't know anything about linux's nuts and bolts?

---

