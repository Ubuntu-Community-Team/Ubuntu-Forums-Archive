---
title: "Jumbo Frames on Realtek RTL8111/8168B (9k MTU) fails poor performance"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Francisco on 2010-11-22
Hello

I am having issues with my Ubuntu server - Windows and Opensolaris drivers allowed the network card to use JUMBO FRAMES (9k MTU). Ubuntu it seems like it is not working.

I have a gigabit LAN at home, and on the other operating systems I used to be able to push data at 60MB/s rates. Today 20MBPS.

I found the problem by querying eth0 it had MTU = 1500. So I tried to enable 9k mtu as my windows computer so I can transfer files.

The MTU will not go any higher than 7000, this is a problem because I was able to set it to 9000 and I know its supported.

Here is the information, thanks in advance:

> giovanni@Gserver:~$ lspci -v | grep Gigabit
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
giovanni@Gserver:~$ modprobe r8111
FATAL: Module r8111 not found.
giovanni@Gserver:~$ modprobe r8168
FATAL: Module r8168 not found.
giovanni@Gserver:~$ ethtool -i eth0
driver: r8169
version: 2.3LK-NAPI
firmware-version: 
bus-info: 0000:04:00.0
giovanni@Gserver:~$ ethtool -k eth0
Offload parameters for eth0:
rx-checksumming: on
tx-checksumming: off
scatter-gather: off
tcp-segmentation-offload: off
udp-fragmentation-offload: off
generic-segmentation-offload: off
generic-receive-offload: off
large-receive-offload: off
ntuple-filters: off
receive-hashing: off
giovanni@Gserver:~$ 


giovanni@Gserver:~$ modprobe r8169
giovanni@Gserver:~$ ifconfig eth0 mtu 9000
SIOCSIFMTU: Operation not permitted
giovanni@Gserver:~$ ifconfig eth0 
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:98:26:ca  
          inet addr:192.168.0.254  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe98:26ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:7000  Metric:1
          RX packets:290016576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168049038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:401221331399 (401.2 GB)  TX bytes:44396953701 (44.3 GB)
          Interrupt:46 Base address:0xe000 

giovanni@Gserver:~$ 


root@Gserver:/home/giovanni/Downloads# lsmod | grep r816
r8169                  42222  0 
mii                     5261  1 r8169
root@Gserver:/home/giovanni/Downloads# 



---

### Post by 65 mustang on 2011-05-04
I have the same problem on 3 different systems with 6 different network cards running 11.04 x64.

Will not go over 7000.

Is there a launchpad bug on this?

---

### Post by 65 mustang on 2011-05-04
Filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/777534](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/777534)

---

### Post by clickwir on 2012-01-08
For what it's worth, the limit is 7200 not 7000. I've not solved this, but mine is at 7200 right now and not performing like it should be. Sometimes I actually see better performance when set to 1500. 

Also, the bug report went stale. :-/ I know they get far more bug reports than they can handle, but just because no one has commented on it doesn't mean it's not still a bug.

---

### Post by P.Kosunen on 2012-04-15
> **clickwir said:**
> For what it's worth, the limit is 7200 not 7000.

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
```

This one can't do 7000, 6000 is ok.

(Old Asrock Vision 3d)

---

