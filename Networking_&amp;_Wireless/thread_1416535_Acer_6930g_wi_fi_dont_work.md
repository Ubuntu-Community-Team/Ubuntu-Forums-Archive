---
title: "Acer 6930g wi fi dont work"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by vlc_marcos on 2010-02-26
HI people, i have a acer 6930g, and yestarday i have install the ubuntu 9.1, but now the buttun of the wireless doesnt work so i cant find any connections. I dont now if i need the drivers or something like that the same is with the graphic card, a ati 4650 ddr2. Where can i find the drivers and what are the steps to install the them????

Sorry about my english

---

### Post by vlc_marcos on 2010-02-26
any one?????

---

### Post by chili555 on 2010-02-26
We need to find out what kind of wireless card you have. Please open Applications -> Accessories -> Terminal and enter:```
lspci -nn | grep Network
rfkill list
```Thanks.

---

