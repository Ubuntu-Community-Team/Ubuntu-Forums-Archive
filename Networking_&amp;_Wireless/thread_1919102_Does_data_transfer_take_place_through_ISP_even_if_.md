---
title: "Does data transfer take place through ISP even if browser is idle?"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2012-02-02
The output of the ifconfig -a command gives something called RX bytes and TX bytes for eth0, lo, ppp0. Can anybody please tell me what these mean? I notice that even if my browser (firefox) is idle, these values increase after a few seconds. For example, for ppp0 these increase by 60 and 40 bytes resp. each 4 seconds. Are these normal? I am asking only to understand what these imply. Thanks.

---

### Post by jonobr on 2012-02-02
Hello


The rx and tx bytes in the ifconfig will show you exactly that, how many bytes  are sent or received on the interface.

Your interface will always be sending our packets even if every application was closed.

A good example is say a standard webpage which updates the ads that may be presented for you.
Although you have not done anything , packets will still come and go

The nic will always be sending or receiving updates, and seeing traffic which may be meant for it or not.

If you ant to see what is going on on the nic , you could type```
sudo tcpdump -i any -vvv
```

You will see all sorts of packets coming and going.

---

