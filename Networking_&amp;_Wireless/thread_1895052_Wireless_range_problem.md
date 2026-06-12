---
title: "Wireless range problem"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by hmmmmmm new on 2011-12-13
Hello, I just recently installed Ubuntu 11.10 on my laptop. I'm relatively new to Ubuntu altogether, so any help is appreciated. My problem seems to be a problem with the range on my wireless adapter. My wireless will pick up my router, but won't connect until I get closer. I want to be able to connect from my bedroom, which I can do on windows, however I need to be at about half that range to be able to connect to the router. If you need any more info, let me know.

Thanks in advance.

---

### Post by praseodym on 2011-12-14
Hi,

please show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
iwlist chan
```

---

