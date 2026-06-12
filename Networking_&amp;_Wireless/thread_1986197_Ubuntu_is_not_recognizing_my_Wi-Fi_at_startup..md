---
title: "Ubuntu is not recognizing my Wi-Fi at startup."
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by TigrisAltaica on 2012-05-24
Hello! I have a small problem. At start-up, ubuntu will not pick up my wi-fi. It will pick up all the neighboring networks but not mine. After some random amount of time, it will finally see my network and connect as normal. How could I fix this? Thank you.

---

### Post by praseodym on 2012-05-24
Hi,

which Ubuntu version do you use? Did you tick "available to all users" and "connect automatically"? Which hardware is in use?
> 
lspci -nnk | grep -iA2 net
lsmod,please.

---

