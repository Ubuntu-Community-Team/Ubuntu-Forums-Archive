---
title: "network card not working intrepid"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by markp1989 on 2009-05-21
the motherboard i am installing on used to be my torrentslave, till the cpu fan  got damaged, i just go around to setting it up again, i was using a nother macine as my torrentslave, before, and i just transferred the hard drives across to the old one, and now the network card isnt working. 

ifconfig only shows me the lo interface. 

lspci | grep net gives the following:

ethernet controller: VIA Technologies, Inc, VT6102 [Rhine-II] (rev 74)


how do i get the nic working?

Thankyou! 

Markp1989

edit: i ran dmesg|grep network and there was a line about eth0 being renamed to eht1, so i edited my /etc/network/interfaces file accordingly and its up and running now .

---

