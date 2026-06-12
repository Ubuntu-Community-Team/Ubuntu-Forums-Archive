---
title: "Can't use wireless"
date: 2012-03-29
forum: Networking &amp; Wireless
---

### Post by chris_popwell on 2012-03-29
So i just found an old laptop of mine that ran jaunty jackolope (9.04), and I put the hard drive in an enclosure to boot  the drive as an external on the laptop that I now have. It's an HP G56 129-WM. I know that the wireless card is a reltek card, but that's about as far as my knowledge of it goes. I can't seem to connect to any wireless connections at all. Please help with this issue.

---

### Post by wildmanne39 on 2012-03-29
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Bucky Ball on 2012-03-29
Plugged in a cable and gotten online and gotten updates?

---

