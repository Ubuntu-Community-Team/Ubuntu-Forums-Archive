---
title: "Problem:Mounting Rootfs via NFS"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by md.touqeer on 2010-02-17
Hi,
I am using ubuntu 8.10
Board AT91SAM9263-EK
I am trying to mount my rootfs using nfs,my rootfs directory is /rootfs
i have put 
Host address(machine addr) - 10.0.0.10
Target Address (Board addr) - 10.0.0.20
Subnet Mask - 255.0.0.0
I have connected eth0 with my board
and eth1(NIC card) with my PC

Problem what i am facing is that when Kernel try to mount root file system form host
it is showing in minicom that host is not responding and link is down but at that time if i check 
the connection in my host system the connection is perfectly fine

The ouput of minicom i put as an attachment
Early response is highly appreciated

---

