---
title: "Slow networking?"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by tiffy1 on 2012-05-05
I'm running a wireless n connection off my asus laptop using KDE with backtrack installed and I've noticed that the network is a little slow and I know it's with ubunutu since I've not had problems before on Windows 7

Ideas as to what I should try?

---

### Post by wildmanne39 on 2012-05-05
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

