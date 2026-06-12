---
title: "Related to networking using direct connection over ethernet crossover cable"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by ankit89 on 2009-06-17
anyone please help me out with this 

The problem is:

i am working on ubuntu 9.04 on the virtualbox. I have configured my machine IP address as 192.168.100.6 netmask 255.255.255.0 with ifconfig command  in linux over my ethernet port eth0...i have connected my ethernet crossover cable from my PC to an evaluation board whose ip is 192.168.1.62. So this is a direct connection. so when i ping the board with ping 192.168.1.62, it says host unreachable. Why is it so??

---

### Post by Iowan on 2009-06-17
Gateway setting?

You realize those two addresses (barring a typo) are not in the same subnet?

---

### Post by uidb4056 on 2009-06-17
> **ankit89 said:**
> anyone please help me out with this 

The problem is:

i am working on ubuntu 9.04 on the virtualbox. I have configured my machine IP address as 192.168.100.6 netmask 255.255.255.0 with ifconfig command  in linux over my ethernet port eth0...i have connected my ethernet crossover cable from my PC to an evaluation board whose ip is 192.168.1.62. So this is a direct connection. so when i ping the board with ping 192.168.1.62, it says host unreachable. Why is it so??

In order communication could be established both systems need to have their IP in the same range, so I suggest you to configure the IP of your Ubuntu as 192.168.1.x being x for example 6. Otherwise you will need a router device that connect both devices without crossover cable providing the appropiate routing between subnets 192.168.1.xxx and 192.168.100.xxx.

---

### Post by ankit89 on 2009-06-18
ok thanks guys...it works....also please  tell me that how to download and compile a C program on the evaluation board from ubuntu running on virtualbox? i have ELDK kit installed in my ubuntu...so how can measure TCP/IP performance of the board with this program? it will be so nice if u guys help me out

---

### Post by Iowan on 2009-06-18
Compiling will (probably?) require you to install build-essential (It's in the repos).

---

### Post by ankit89 on 2009-06-19
ok...Can u tell me how to change my MAC address of the ethernet port there on my board which is connected to PC?? only the board's MAC address need to be configured..is there any way to do that?

---

### Post by jhannah on 2009-06-19
You mean the MAC address of the interface on your PC? If so, you can use the below command:

```
ifconfig **eth0** hw ether 00:11:22:33:44:55
```

Of course, if this isn't for eth0, you will need to replace the interface name.
**[B]**[/B]

---

### Post by ankit89 on 2009-06-19
> **jhannah said:**
> You mean the MAC address of the interface on your PC? If so, you can use the below command:

```
ifconfig **eth0** hw ether 00:11:22:33:44:55
```Of course, if this isn't for eth0, you will need to replace the interface name.

Ya I did that and it works but it is in the RAMdisk so whenver I reset my board, it sets to the original default value....so wat should be done to make it permanent on the board?
i have seen the sysconfig file in the /etc folder but there isnt none in my board...so how do i need to rebuild my Uboot prompt and configure? and if yes, then how to do it?

---

