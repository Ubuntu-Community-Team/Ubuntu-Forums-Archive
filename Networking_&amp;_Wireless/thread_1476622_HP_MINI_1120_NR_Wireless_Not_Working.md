---
title: "HP MINI 1120 NR Wireless Not Working"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by redblood on 2010-05-08
Hello i just Installed Ubuntu 10.04 Netbook Edition in my HP MINI 1120 Nr everthing seem to be FINE but WIFI not showing i think the driver is missing, PLEASE HLEP i need to use WIFI Thanks.

---

### Post by zerobytes2003 on 2010-05-08
I'm not pro but I'll help if I can.

to start try running lspci to find out what card you have (or if it even finds the card) 
then try iwconfig which should show you any info about your wireless connection

---

### Post by aysiu on 2010-05-08
It's a Broadcom 4312.

This is a bug:
[bcmwl kernel source needs to be reinstalled for Broadcom 4312 to work](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/441492)

---

### Post by redblood on 2010-05-08
Thank you for your replys i have Fixed the issue Here is how for other ppl who don;t know

Connect your Netbook to Wired Connection 
Go to System Then Hardware Drivers
Download both of them and it works Perefect..

Now i can Enjoy New Ubuntu 10.4 on my HP Mini NETBOOK

Thanks.

---

