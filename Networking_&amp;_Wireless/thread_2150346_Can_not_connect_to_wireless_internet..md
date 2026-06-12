---
title: "Can not connect to wireless internet."
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by KioFox on 2013-05-31
So I got Wubi quite a while ago and I am trying to install Ubuntu on my laptop how ever after I install Ubuntu I am unable to any thing internet related. The wireless icon on the top right implies that I am connected to the internet how ever when I try to visit a website or update Ubuntu to the latest version it says that I am not connected.

Sorry if the above is a little confusing, and I hope some one can help a forum first timer, and an Ubuntu noob.

---

### Post by praseodym on 2013-05-31
Please open a terminal with CTRL+ALT+T and show the outputs of the commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

