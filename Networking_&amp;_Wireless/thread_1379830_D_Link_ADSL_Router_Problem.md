---
title: "D Link ADSL Router Problem"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2010-01-13
Hi, I use a wired Dlink Adsl Router GLB502T with its inbuilt dialer configured. Problem is it will not connect while computer is running.When I try to ping the local ip of the modem this is what I get "ping: sendmsg: Operation not permitted" and "/etc/init.d/networking restart" has no effect either.I need to restart my computer every time i want to connect to the Internet.I switch on the modem when the grub bootloader appears and the modem connects without any problem.This problem appeared when i installed Ubuntu 9.04.There was no problem with Ubuntu 8.04. What is the solution? 

OS:Ubuntu 9.04

Motherboard: Asus M2N68-AM
             NVIDIA Geforce 7025/nForce 630a
             RTL8211CL Phy Gigabit LAN
             ALC662 High Definition Audio 6 -Channel CODEC
             
Processor:AMD 64 X 2[PHP][/PHP]

---

### Post by linuxyogi on 2010-02-01
Nobody?

---

### Post by suseendran.rengabashyam on 2010-02-01
Hi,

May I know how you are assigning the IP address to your network interface? Is it via the /etc/network/interfaces file or via the Network Manager console? If the interface is managed by the NetworkManager, running ```
/etc/init.d/networking restart
``` does not have any effect.

You might get the "ping: sendmsg: Operation not permitted" message when the firewall on your computer or on the Router blocks the ICMP packets. Disable the firewall for testing and see if that makes any difference.

---

### Post by linuxyogi on 2010-02-01
> **suseendran.rengabashyam said:**
> Hi,

May I know how you are assigning the IP address to your network interface? Is it via the /etc/network/interfaces file or via the Network Manager console? If the interface is managed by the NetworkManager, running ```
/etc/init.d/networking restart
``` does not have any effect.

You might get the "ping: sendmsg: Operation not permitted" message when the firewall on your computer or on the Router blocks the ICMP packets. Disable the firewall for testing and see if that makes any difference.
 Thanks for your reply. I just installed Ubuntu 9.10 today.This version of Ubuntu has no problem with ethernet hotplugging. Thanks a lot.

---

### Post by superprash2003 on 2010-02-02
please mark this thread as solved , if your problem is solved

---

