---
title: "How to configure HUAWEI ets 2288 in Ubuntu 9.04"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by mjonyh on 2009-06-15
Here I have found the problem with my HUAWEI ETS 2288 modem with Dhaka Phone. I am not able to connect this modem from my ubuntu 9.04. What should I do?

with Thanks.


jony@megadeath:~$ lsusb
Bus 001 Device 004: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jony@megadeath:~$ sudo modprobe usbserial vendor=0x0451 product=0x3410
[sudo] password for jony: 
FATAL: Module usbserial not found.

---

### Post by GeorgeVita on 2009-06-15
Hi **mjonyh**, your modem is listed in many other NotSolved threads. Try a search using **2288** as a search string within ubuntuforums.org

For your question regarding 
> FATAL: Module usbserial not found. 
the answer is simple: **[http://ubuntuforums.org/showpost.php?p=7455154&postcount=4](http://ubuntuforums.org/showpost.php?p=7455154&postcount=4)**

This module is encapsulated (for the time being) into kernel. A future update will fix this. In above link you can find another fix (I did not test it).

For reference read also other threads in case you have a NEW idea!
[http://ubuntuforums.org/showthread.php?t=993888](http://ubuntuforums.org/showthread.php?t=993888)
[http://ubuntuforums.org/showthread.php?t=1187192](http://ubuntuforums.org/showthread.php?t=1187192)
[http://ubuntuforums.org/showthread.php?t=1154936](http://ubuntuforums.org/showthread.php?t=1154936)

You may also contact other users that they have the same modem and collaborate to find a solution.

Regards,
George

---

