---
title: "Can't start rpcbind service"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by ElvisTheKing on 2013-04-12
I'm going slightly spare here, I've got an almost new Ubuntu 12.10 server installation (reasonably standard install OpenSSH, LAMP, only weirdness is XFS) and I'm trying to get XFS to share over NFS working on it. That seesm to work but I wanted to check wityh showmout if it had worked. So i install nfs-kernel-server and that installed rpcbind and nfs-common as well. However when I try showmount:
```

elvis@Microserver:~$ showmount -e localhost
clnt_create: RPC: Program not registered

```
OK fine rpcbind isn't started so I try to start it.
```

elvis@Microserver:~$ sudo service rpcbind start
[sudo] password for elvis:
rpcbind: unrecognized service

```

Hmm maybe it wasn't installed after all, lets try again.
```

elvis@Microserver:~$ sudo apt-get install rpcbind
Reading package lists... Done
Building dependency tree
Reading state information... Done
rpcbind is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 107 not upgraded.

```

So it's installed I just can't start it.
I've spent about 1/2 googleing various things i can think of and so far I've drawn a blank.

---

### Post by steeldriver on 2013-04-12
I don't think rpcbind shows up in the service list - what does netstat say?

```
$ service --status-all 2>&1 | grep rpc
 [ ? ]  rpcbind-boot
$ sudo netstat -nlpt | grep rpc
tcp        0      0 0.0.0.0:47406           0.0.0.0:*               LISTEN      743/rpc.statd
**tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      631/rpcbind**
tcp        0      0 0.0.0.0:46579           0.0.0.0:*               LISTEN      16375/rpc.mountd
tcp        0      0 0.0.0.0:57306           0.0.0.0:*               LISTEN      16375/rpc.mountd
tcp        0      0 0.0.0.0:53955           0.0.0.0:*               LISTEN      16375/rpc.mountd
tcp6       0      0 :::53189                :::*                    LISTEN      16375/rpc.mountd
tcp6       0      0 :::38379                :::*                    LISTEN      743/rpc.statd
**tcp6       0      0 :::111                  :::*                    LISTEN      631/rpcbind**
tcp6       0      0 :::41817                :::*                    LISTEN      16375/rpc.mountd
tcp6       0      0 :::45698                :::*                    LISTEN      16375/rpc.mountd
```

---

### Post by ElvisTheKing on 2013-04-13
Hmmm OK so it is running:
```

elvis@Microserver:~$ sudo netstat -nlpt | grep rpc
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1006/rpcbind    
tcp        0      0 0.0.0.0:48881           0.0.0.0:*               LISTEN      1025/rpc.statd  
tcp6       0      0 :::48766                :::*                    LISTEN      1025/rpc.statd  
tcp6       0      0 :::111                  :::*                    LISTEN      1006/rpcbind

```

But yet showmount stil dosn't work:
```

elvis@Microserver:~$ showmount -e localhost
clnt_create: RPC: Program not registered

```

---

### Post by steeldriver on 2013-04-13
Hmm... well I don't know what that error means exactly, but are you sure that the nfs-kernel-server package installed correctly? it's the same error I see on systems without that package i.e.

```
$ apt-cache policy nfs-kernel-server
[B]nfs-kernel-server:
  Installed: (none)[/B]
  Candidate: 1:1.2.5-3ubuntu3.1
  Version table:
     1:1.2.5-3ubuntu3.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packa                                                              ges
     1:1.2.5-3ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
$
$ sudo netstat -nlpt | grep rpc
[sudo] password for theharv:
tcp        0      0 0.0.0.0:44001           0.0.0.0:*               LISTEN                                                                    1011/rpc.statd
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN                                                                    708/rpcbind
tcp6       0      0 :::52014                :::*                    LISTEN                                                                    1011/rpc.statd
tcp6       0      0 :::111                  :::*                    LISTEN                                                                    708/rpcbind
$
$
$ showmount -e localhost
**clnt_create: RPC: Program not registered**
$
```

You can check the package status with dpkg e.g.

```
$ dpkg -l nfs-kernel-server
```

if it shows as anything other than 'ii' then maybe try reinstalling it?

---

### Post by ElvisTheKing on 2013-04-13
No it's there:
```

elvis@Microserver:~$ sudo apt-cache policy nfs-kernel-server
nfs-kernel-server:
  Installed: 1:1.2.6-3ubuntu2
  Candidate: 1:1.2.6-3ubuntu2
  Version table:
 *** 1:1.2.6-3ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
elvis@Microserver:~$ dpkg -l nfs-kernel-server
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nfs-kernel-ser 1:1.2.6-3ubu amd64        support for NFS kernel server
elvis@Microserver:~$

```

---

### Post by steeldriver on 2013-04-13
Well since  netstat is not showing rpc.mountd it doesn't even look like the nfs server is running? what does

```
service nfs-kernel-server status
```

say? how about if you manually try to restart the service? any error messages?

```
sudo service nfs-kernel-server restart
```

---

