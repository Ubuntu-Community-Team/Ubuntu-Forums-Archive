---
title: "what is/are iptables &amp; what I need to configure"
date: 2005-12-18
forum: Networking &amp; Wireless
---

### Post by ShirishAg75 on 2005-12-18
Hi all,
      I read the networking wiki & did the following steps :-
First gave a command ```
ifconfig up
``` & then```
shirishag75@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:08:A1:92:56:33
          inet6 addr: fe80::208:a1ff:fe92:5633/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:23 Base address:0xc800

shirishag75@ubuntu:~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok
shirishag75@ubuntu:~$ lspci | grep eth
shirishag75@ubuntu:~$ lspci | grep Eth
0000:03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
shirishag75@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
shirishag75@ubuntu:~$

```From the above AFAIK this means the Realtek driver which seems to be in the database got detected alright. The only thing seems to be some configuration in the iptables which need to be done. Am I right or wrong in the assessment. Any advice/help is welcome. Also searched the wiki but was not able to find any documentation on configuring iptables.Thnx in advance.

---

### Post by daschl on 2005-12-18
at first, iptables have "nothing" to do with your network adapter.

you can imagine iptables as a set of rules for which packages are allowed to pass your system and which are dropped.

theres an excellent tutorial for iptables:
[http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO.html](http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO.html)

good luck :)

---

### Post by jliedeka on 2005-12-19
Looks like you don't have an ipv4 address which is what you probably need.  Do you have a static IP you need to set.  If not run DHCP with:

sudo dhclient eth0

Then see what ifconfig -a gives you.

---

