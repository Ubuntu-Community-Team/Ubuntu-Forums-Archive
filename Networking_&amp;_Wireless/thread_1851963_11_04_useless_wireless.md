---
title: "11 04 useless wireless"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by Jayhawker on 2011-09-29
My 11/04 is alongside WIndows Vista. 

While Ethernet is OK, the Wireless is not. It seems it works, once all passwords in, but neither browsing nor downloading are possible. 

Please, any idea to solve it?

Thanks

---

### Post by Jayhawker on 2011-09-30
Please, any help?

---

### Post by nothingspecial on 2011-09-30
Hi, post the details. :)

```
sudo lshw -C network
```

---

### Post by Jayhawker on 2011-12-14
Thanks for your attention. I've installed the last Ubuntu 11/10, and after following your suggestion, I still have the problem. Curiously, the Wi Fi've found other routers but not mine. Then,I've installed my router in Hidden Wi FI's. Now my router becomes detected and even hypothetically connected after a while, but it doesn't work at all yet. 

How to solve it?

Thank You
 
> **nothingspecial said:**
> Hi, post the details. :)

```
sudo lshw -C network
```

---

### Post by praseodym on 2011-12-14
Please show the output of that command plus

```
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
cat /etc/resolv.conf
route -n
```

---

