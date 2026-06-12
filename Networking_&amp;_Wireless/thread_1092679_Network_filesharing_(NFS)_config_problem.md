---
title: "Network filesharing (NFS) config problem"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by bocajuniors12 on 2009-03-10
Ive set up my two computers both running Intrepid. Both can ping each other.

Gateway 192.168.0.1

comp1 : (/etc/network/interfaces)

```
auto lo eth1
iface lo inet loopback
iface eth1 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1
```



comp2 : (/etc/network/interfaces)

```
auto lo eth1
iface lo inet loopback
iface eth1 inet static
        address 192.168.0.3
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1

```

comp2 has this in /etc/export

```
/public 192.168.0.0/255.255.255.0(async,insecure,subtree_check,no_root_squash,rw,nohide)

```
both can ping each other.

I create directory /boca for test mounting, ls -la gives:

```
drwxr-xr-x   2 root root  4096 2009-02-24 05:34 boca
```

and public:

```
drwxrwxrwx   2 root root  4096 2009-02-25 13:41 public
```


When I test the NFS export I run this on comp2 :

```
sudo mount 192.168.0.3:/public /boca
```

and I get this error:

```
mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered
mount.nfs: internal error
```


I have no idea what to do? Anyone know where I've gone wrong?

Cheers in advance

Mungo

---

### Post by 47_MasoN_47 on 2009-03-11
After you setup the NFS export did you run the following 2 commands on the server?

```
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a
```

BTW here's a link to the thread I used to get my NFS servers working properly.

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

