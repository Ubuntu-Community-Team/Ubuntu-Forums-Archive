---
title: "NFS fails to work...."
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by jiapei100 on 2012-09-08
Hi, all:

Please help... Depressed to death....
Environment: Ubuntu 12.04

No matter what I tried, I failed to enable NFS even on my local computer. Command

> $ sudo mount -t nfs localhost:/nfs /mnt/nfs
only brings me
> mount.nfs: access denied by server while mounting

I seriously tried everything....

1) My /etc/exports is like
> /nfs    192.168.1.*(rw,sync,no_root_squash)
2) What's more:
```
$ sudo service portmap restart
portmap stop/waiting
portmap start/running, process 5571

```
3) And:
```
$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                                                              [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                        [ OK ] 
 * Exporting directories for NFS kernel daemon...                                                                 exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.*:/nfs".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

                                                                                                           [ OK ]
 * Starting NFS kernel daemon                                                                              [ OK ] 
```


Sigh... What else do I need to pay attention to?


Cheers
Pei

---

### Post by jiapei100 on 2012-09-08
Extremely weird...

When I change my **/etc/exports** from
> /nfs    192.168.1.*(rw,sync,no_root_squash)
to
> /nfs    *(rw,sync,no_root_squash)
it's now working....


My local network is of all IP addresses: 192.168.1.*
On my Host Computer (basically, now, Host and Client are the same computer running Ubuntu 12.04)
> $ifconfig
gives me
> inet addr:192.168.1.70 


Can anybody help to explain this please?


Cheers
Pei

---

### Post by steeldriver on 2012-09-08
I think it's because localhost resolves to 127.0.0.1 (via the loopback interface lo) which is outside your allowed 192.168.0.* range - try it with the LAN IP instead of localhost

EDIT: just tried it myself

```
steeldriver@htpc-01:~$ sudo mount -t nfs localhost:/var/lib/mythtv/pictures /mnt/localhost/pictures
mount.nfs: access denied by server while mounting localhost:/var/lib/mythtv/pictures
steeldriver@htpc-01:~$
steeldriver@htpc-01:~$ sudo mount -t nfs 192.168.1.65:/var/lib/mythtv/pictures /mnt/localhost/pictures
steeldriver@htpc-01:~$ ls /mnt/localhost/pictures/
family misc

```

---

### Post by papibe on 2012-09-08
> **steeldriver said:**
> I think it's because localhost resolves to 127.0.0.1 
+1

Nevertheless, note that the correct syntax for a subnetwork would be:
```
/nfs  **192.168.1.0/24**(rw,sync,no_root_squash) 
```
Regards.

---

### Post by jiapei100 on 2012-09-08
Wow. Hi, papibe:

Thanks...
But what does "0/24" mean? 


Thanks papibe...

Pei



> **papibe said:**
> +1

Nevertheless, note that the correct syntax for a subnetwork would be:
```
/nfs  **192.168.1.0/24**(rw,sync,no_root_squash) 
```
Regards.

---

### Post by papibe on 2012-09-08
```
192.168.1.0/24
```
Indicates both the network address (192.168.1.0) and the netmask (24 bits, equivalent to 255.255.255.0).

You can also use explicitly the netmask:
```
192.168.1.0/255.255.255.0
```
Does that help?
Regards.

---

