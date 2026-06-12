---
title: "Issues with PXE"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by alexbrooks on 2011-08-27
Hello everyone,

Currently I have a server setup with Ubuntu 10.04 Server Edition and I have setup DHCP on it. Right now this is the layout of the network :[INDENT]            Client Computer(s) ----> Babbage (My server) -----> Church (Prof. Server) ----> College Campus Internet
[/INDENT]I have been in the process of setting up Babbage so that the clients connected can PXE boot from him. I have been using the following tutorial:[INDENT][https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
[/INDENT]I am at the point where I am mounting the OS onto the server, however I am having issues. It will not let me mount to the server, no matter what I try. I get the wonderful ***mount.nfs: mount system call failed ***error. I am not sure why this is happening. (command : **sudo mount -t nfs -o nolock 192.168.0.100:/nfsroot /mnt**)

Here are some of the properties of the setup so far, to provide a little info/background.
[SIZE=3]
_**SERVER**_[/SIZE]

**/etc/hosts**
```

127.0.0.1     localhost
127.0.1.1     babbage
179.47.7.1    church

```**/etc/network/interfaces**
(eth0 --> church | eth1 --> client network)
```

auto lo
iface lo inet loopback
pre-up iptables-restore < /etc/iptables.rules

auto eth0
iface eth0 inet static
    address 179.47.7.2
    netmask 255.255.255.0
    gateway 179.47.7.1
    broadcast 192.168.0.255
    network 192.168.0.0
    up iptables -t nat -A POSTROUTING -o $IFACE -j MASQUERADE

auto eth1
iface eth1 inet static
    address 192.168.0.100
    netmask 255.255.255.0
    broadcast 192.168.0.255
    network 192.168.0.0

```**/etc/exports**
```

/nfsroot    192.168.0.0/24(rw,async,no_subtree_check)
/home       @babbageClients(rw,sync,no_subtree_check)
/usr/local  @babbageClients(rw,sync,no_subtree_check)

```**iptables -L**
```

Chain INPUT (policy ACCEPT)
target    prot opt source        destination
ACCEPT    all  --  anywhere    anywhere
ACCEPT    tcp  --  anywhere    anywhere    tcp dpt:ssh
ACCEPT    tcp  --  anywhere    anywhere    tcp dpt:www
ACCEPT    all  --  anywhere    anywhere    ctstate RELATED,ESTABLISHED
LOG       all  --  anywhere    anywhere    limit: any 5/min burst 5 LOG level debug prefix 'iptables denied: '
DROP      all  --  anywhere    anywhere
ACCEPT    tcp  --  anywhere    anywhere    tcp dpt:33926
ACCEPT    tcp  --  anywhere    anywhere    tcp dpt:57066
ACCEPT    tcp  --  anywhere    anywhere    tcp dpt:sunrpc
ACCEPT    tcp  --  anywhere    anywhere    tcp dpt:nfs

```**rpcinfo -p**
```

  program vers proto  port
   100000    2   tcp   111  portmapper
   100021    1   udp 36385  nlockmgr
   100021    3   udp 36385  nlockmgr
   100021    4   udp 36385  nlockmgr
   100021    1   tcp 46843  nlockmgr
   100021    3   tcp 46843  nlockmgr
   100021    4   tcp 46843  nlockmgr
   100003    2   udp  2049  nfs
   100003    3   udp  2049  nfs
   100003    4   udp  2049  nfs
   100003    2   tcp  2049  nfs
   100003    3   tcp  2049  nfs
   100003    4   tcp  2049  nfs
   100005    1   udp 33926  mountd
   100005    1   tcp 57066  mountd
   100005    2   udp 33926  mountd
   100005    2   tcp 57066  mountd
   100005    3   udp 33926  mountd
   100005    3   tcp 57066  mountd
   100000    2   udp   111  portmapper
   100024    1   udp 49103  status
   100024    1   tcp 39746  status
   100007    2   udp  1003  ypbind
   100007    1   udp  1003  ypbind
   100007    2   tcp  1004  ypbind
   100007    1   tcp  1004  ypbind

```**netstat -plntu**
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address    Foreign Address        State    PID/Program Name
tcp       0      0 0.0.0.0:57066     0.0.0.0:*              LISTEN   1103/rpc.mountd
tcp       0      0 0.0.0.0:1004      0.0.0.0:*              LISTEN   13123/ypbind
tcp       0      0 0.0.0.0:111       0.0.0.0:*              LISTEN   3228/portmap
tcp       0      0 0.0.0.0:46843     0.0.0.0:*              LISTEN   -
tcp       0      0 0.0.0.0:2049      0.0.0.0:*              LISTEN   -
tcp       0      0 0.0.0.0:39746     0.0.0.0:*              LISTEN   3256/rpc.statd
udp       0      0 0.0.0.0:49103     0.0.0.0:*                       3256/rpc.statd
udp       0      0 0.0.0.0:1003      0.0.0.0:*                       13123/ypbind
udp       0      0 0.0.0.0:111       0.0.0.0:*                       3228/portmap
udp       0      0 0.0.0.0:888       0.0.0.0:*                       3256/rpc.statd
udp       0      0 0.0.0.0:2049      0.0.0.0:*                       -
udp       0      0 0.0.0.0:33923     0.0.0.0:*                       1103/rpc.mountd
udp       0      0 0.0.0.0:36385     0.0.0.0:*                       -
udp       0      0 0.0.0.0:67        0.0.0.0:*                       2728/dhcpd3
udp       0      0 0.0.0.0:69        0.0.0.0:*                       762/in.tftpd

```_**[SIZE=3]CLIENT[/SIZE]**_

**/etc/hosts**
```

127.0.0.1    localhost
127.0.1.1    ubuntu-3
192.168.0.100    babbage

```**/etc/network/interfaces**
```

iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.103
        netmask 255.255.255.0
        gateway 192.168.0.100


```If there is anything else I should paste up here to help solve the issue, please let me know. I am willing to change just about anything to get it to work.

Thank you in advance for all of the help!

---

### Post by alexbrooks on 2011-08-27
Also, after getting the mounting error, I checked the syslog and here is what came up

```

Aug 27 18:59:17 ubuntu-3 kernel: [118865.140031] mount: server 192.168.0.100 not responding, timed out

```

I don't understand why the server isn't responding, because they are communicating correctly (I can ping 192.168.0.100 (Babbage) from the client)

So confused.....

---

### Post by alexbrooks on 2011-08-29
I am also willing to start completely over and follow a different tutorial if anyone has a better one. I just want PXE booting setup and working with a DHCP/NFS server. If you have any input at all, please let me know.

---

