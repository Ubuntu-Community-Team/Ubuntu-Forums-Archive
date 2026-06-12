---
title: "3 Problems: eth0 down/NFS/route"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by anasaz on 2009-10-22
Hi All

  I have Ubuntu server with the following distribution details:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

I have three problems related to networking.

First after I reboot, eth0 seems to go down. I need to manually write (#ifconfig eth0 up) to bring it up.

second, NFS mount does not auto-mount. although I have an entry like the following in /etc/fstab:
192.168.200.100:/data/mydata        /data   nfs     0       0

third, I need to add a static route, I have the following entry in /etc/network/interfaces:
up route add -net 172.0.0.0/8 gw 172.25.20.1 dev eth2

but it does not work automatically. so to make all these problems work, I have to run the following script manually after each and every reboot.
```

ifconfig eth0 up
mount 192.168.200.100:/data/mydata /data
route add -net 172.0.0.0/8 gw 172.25.20.1

```

Any idea! 

Thanx

---

### Post by BigBob on 2009-10-22
> **anasaz said:**
> Hi All

  I have Ubuntu server with the following distribution details:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

I have three problems related to networking.

First after I reboot, eth0 seems to go down. I need to manually write (#ifconfig eth0 up) to bring it up.

second, NFS mount does not auto-mount. although I have an entry like the following in /etc/fstab:
192.168.200.100:/data/mydata        /data   nfs     0       0

third, I need to add a static route, I have the following entry in /etc/network/interfaces:
up route add -net 172.0.0.0/8 gw 172.25.20.1 dev eth2

but it does not work automatically. so to make all these problems work, I have to run the following script manually after each and every reboot.
```

ifconfig eth0 up
mount 192.168.200.100:/data/mydata /data
route add -net 172.0.0.0/8 gw 172.25.20.1

```Any idea! 

Thanx

Maybe you can try this way :

In the /etc/network/interfaces :

```
auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
network xxx.xxx.xxx.xxx
broadcast xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
post-up route add -net 172.0.0.0/8 gw 172.25.20.1
```Obviously replace xxx.xxx.xxx.xxx by your personal values ...

A++

---

### Post by anasaz on 2009-10-22
Thanks for your replay

I will try and come back to you.

what about other problems.

Somebody HELP PLEASE

Thanx

---

