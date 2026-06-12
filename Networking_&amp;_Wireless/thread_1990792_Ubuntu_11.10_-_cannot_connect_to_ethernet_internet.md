---
title: "Ubuntu 11.10 - cannot connect to ethernet internet"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by btddanger on 2012-05-29
my computer shows the wired connection 1 but it is not connected the connection. I tried downloading Ubuntu 12.04 onto a flash drive but the computer says vfat error when I plug it in. please help to connect my internet so  can upgrade to 12.04

---

### Post by Sularco on 2012-05-30
In order to assist we would need some more information about the nature of the problem, similar as in other network-problem related posts.
What is the output of the following commands run in a terminal:

ifconfig
lshw -C network
lspci | grep Ether

---

