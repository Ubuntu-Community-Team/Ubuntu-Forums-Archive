---
title: "Ethernet stops working"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by jordey24 on 2009-06-27
Hi,when i use internet on Ubuntu 9.04 for longer than about half an hour,no program can access the internet while ubuntu says i still have a connection.I tried creating an ad-hoc network and other devices could access the internet without problems.When i restart i got an  internet connection again.Any ideas how i can fix this so i dont need to restart my laptop every 30 minutes? Thanks,
-jordey24

---

### Post by cariboo on 2009-06-27
We need a lot more information. What version of Ubuntu are you using? How do you connect to the internet? What ethernet device are you using?

---

### Post by jordey24 on 2009-06-29
> **cariboo907 said:**
> We need a lot more information. What version of Ubuntu are you using? How do you connect to the internet? What ethernet device are you using?
Im using Ubuntu 9.04,im using a direct connection to the internet (no routers) and my Ethernet device is an RTL8101E/RTL8102E PCI Express Fast Ethernet controller by  Realtek Semiconductor Co., Ltd.

---

### Post by Iowan on 2009-06-29
**iwconfig** might help - as might **lshw -C network**.

Check some things  when it fails.  See if the address  (**ifconfig -a**), or gateway (**route -n)**, or DNS server (**less /etc/resolv.conf)** has changed.

---

