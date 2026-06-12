---
title: "Yes another Wifi?"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by staticpunk84 on 2011-02-24
so I have been seeing this issue all over but everything is different. So I have a loptop x32 bit vista and I installed ubuntu by usb flash drive but Im trying to get wifi to get connected the wifi card is built in.

---

### Post by TBABill on 2011-02-24
Since it's built in can you open terminal and enter ```
lspci
``` and then paste the entire output back here? That's LSPCI in lower case. That will tell us what type of hardware you have by chipset make/model. 
 
And you'll probably be asked to also do the same for ```
sudo lshw -C network
``` so may as well get that in early as well.

---

