---
title: "How to stop DHCP discover"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by chenatu on 2013-02-05
I have two NIC eth0 and eth1. I want to do an experiment which needs to delete the IP layer information and stop DHCP. So I use ifconfig to delete the IP info of eth1. However, how to stop dhcp serivice or the process of DHCP discover process of the certain NIC such as eth1. I can not kill the dhcpd because I have to keep eth0 for SSH.

---

### Post by PowerBarry43 on 2013-02-05
Hi

if you run either

```
sudo gedit /etc/network/interfaces
```

or if you're used to vi

```
sudo vi /etc/network/interfaces
```

then you should see something like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static


the important part here is the last line. As long it says static not dhcp then dhcp is disabled for that interface.

Hope this helps!

Barry

---

### Post by chenatu on 2013-02-05
I just see the configuration of lo
auto lo
iface lo inet loopback

and I append
auto eth1
iface eth1 inet static

The I "service network restart"
and I use tcpdump to listen eth1
However I also capture the frame which means dhcp discover

Should I input some other commands after I change the file /etc/network/interfaces?

---

