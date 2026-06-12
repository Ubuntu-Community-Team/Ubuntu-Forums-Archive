---
title: "Wireless Randomly stopped working on Toshiba C655D"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by mjquest on 2011-12-03
I've been running Ubuntu fine on this laptop for over a year. Last night my wireless was working. I powered down, went to bed, woke up and booted this morning and it won't connect to any wireless networks.

I know the router isn't the problem because other devices are connected to it with excellent signals right now. 

The wireless menu shows all the available networks. But it won't connect to any. And it shows poor signal strength for my network even tho I'm sitting right next to the router. 

Also, my wired connection works perfectly.

Any ideas? I'm hoping it's something I can fix, but if it turns out to be a hardware problem it might be a good excuse to just buy a better laptop.

---

### Post by praseodym on 2011-12-03
Hi,

please show

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
sudo iwlist scan
route -n
cat /etc/resolv.conf
```

---

### Post by mjquest on 2011-12-03
Never mind. Just as quickly and randomly as it stopped working my wireless has started working again. Thanks anyway.

---

