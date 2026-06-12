---
title: "Huawei E1550 connection problem in 11.04"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by marcoslai on 2011-06-12
Hi,I'm using Ubuntu 11.04 32bit on HP Mini 1000,wireless work,wired work,but now having problem with mobile broadband.
Huawei E1550 detected & show on network manager,but not connected,the connecting animation keep going so long but it seems couldn't get connection.
Any solution?

[IMG]http://i694.photobucket.com/albums/vv303/marcoslai/s1.jpg[/IMG]

Output of lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 003: ID 05c8:0202 Cheng Uei Precision Industry Co., Ltd (Foxlink)

---

### Post by superduperlinuxperson on 2011-06-12
run lspci -vnn | grep 14e4

---

### Post by marcoslai on 2011-06-12
> **superduperlinuxperson said:**
> run lspci -vnn | grep 14e4

Output:

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

My problem is mobile broadband,not wifi.

---

### Post by marcoslai on 2011-06-12
> **superduperlinuxperson said:**
> run lspci -vnn | grep 14e4

Output:

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

My problem is mobile broadband,not wifi.

---

### Post by superduperlinuxperson on 2011-06-12
very sorry
you may be missing the driver, try googling for it

---

