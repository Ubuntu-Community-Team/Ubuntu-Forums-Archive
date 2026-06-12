---
title: "How could i solve the network problem in ubunut 9.04"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by vaiocliehk on 2009-06-14
I'm a newbie for linux and ubuntu

I have 3 NICs in my ubuntu 904
1) RTL8111/8168B
2) Intel 82540EM
3) Intel 82544EI
first 2 of them is ok, could get ip from DHCP
but the (3) one could be identified by ubuntu 904 but the MAC Address of it being 00:00:00:00:00:00
therefore i could not get ip from it.

Please give me a helpful hand on it
Thanks

---

### Post by jonobr on 2009-06-14
Could you post the results of your ifconfig this should show the mac address reported on the device
Also, if you could remove the device it may have the mac address printed on a lable on the card and you may be able to set the mac address manually

---

### Post by Iowan on 2009-06-14
**lshw -C network** *should* also provide a wealth of information about yournetwork devices.

---

