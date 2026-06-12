---
title: "Infiniband mellanox configuration on ubuntu 9.10"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by erpupone10 on 2009-11-19
Hi all,

This is the first time I write in this forum.

I just built and installed a custom 2.6.32 kernel on a ubuntu 9.10 server amd64. I installed Infinband support in the kernel configuration but I cannot start Infiniband network.

The card is:

```
InfiniBand: Mellanox Technologies MT26428 [ConnectX VPI PCIe 2.0 5GT/s - IB QDR / 10GigE] (rev a0)
```I configured ib0 interface in /etc/network/interfaces:

```
root@xc263:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
auto eth1
auto ib0
iface lo inet loopback
iface eth1 inet static
        address 172.31.1.23
        netmask 255.255.192.0
        gateway 172.31.1.17
iface ib0 inet static
        address 172.31.65.23
        netmask 255.255.192.0
        gateway 172.31.65.17
```At boot the only module loaded that refers to infiniband is "ib_iser" and the mlx4_core module is loaded

but when I try to start the interface:

```
root@xc263:~# ifup ib0
SIOCSIFADDR: No such device
ib0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
ib0: ERROR while getting interface flags: No such device
Failed to bring up ib0.en I try to start the network it gives me this error:
```

Any suggestions?

Thanks

Giovanni

---

### Post by racmar on 2010-03-08
I'm sure you've already figured this out, but for others with this problem.

You need to load ib_ipoib

```
modprobe ib_ipoib
```

---

### Post by connectBrandon on 2011-04-28
As for InfiniBand, are you refering to cables? like this one??
[http://blog.connectzone.com/bid/63261/what-is-an-infiniband-cable](http://blog.connectzone.com/bid/63261/what-is-an-infiniband-cable)

Let me know asap

---

### Post by anothracc on 2012-03-29
I have ib_ipoib displayed by $modprobe, and have similar entries in my /etc/network/interfaces, yet $ ifup ib0 continues to give me:

Cannot find device "ib0"
Failed to bring up ib0.

Could there be something else missing?  $ modprobe shows I have the following ib modules loaded:
$ lsmod | grep ib
ib_uverbs              42625  0 
ib_umad                17863  0 
ib_sdp                140618  0 
rdma_cm                43090  1 ib_sdp
ib_addr                14142  1 rdma_cm
ib_ipoib               87099  0 
ib_cm                  46840  2 rdma_cm,ib_ipoib
ib_sa                  49078  3 rdma_cm,ib_ipoib,ib_cm
ib_mthca              137036  0 
ib_mad                 47259  4 ib_umad,ib_cm,ib_sa,ib_mthca
ib_core                73428  10 ib_uverbs,ib_umad,ib_sdp,rdma_cm,iw_cm,ib_ipoib,ib_cm,ib_sa,ib_mthca,ib_mad
libahci                26861  1 ahci

Still no joy!

---

### Post by Techi50 on 2012-09-19
Any luck with this problem?
I have the same problem using the same cards with CentOS 5.7.
I have noticed in my case that both led are not lit in both cards! Is it the same with you?

---

### Post by anothracc on 2012-09-19
> **Techi50 said:**
> Any luck with this problem?
I have the same problem using the same cards with CentOS 5.7.
I have noticed in my case that both led are not lit in both cards! Is it the same with you?

Yes; none of my cards are lit up.  I've made no progress I'm afraid but have put no more time into it either.  I am still interested, however.  If you get anywhere, please post!

---

### Post by Techi50 on 2012-09-19
It works for me now :)
It was my mistake that I inserted the cable in the wrong way. Once I reverse the cable the led lit up and then the subnet manager was able to discover the other machine.

---

