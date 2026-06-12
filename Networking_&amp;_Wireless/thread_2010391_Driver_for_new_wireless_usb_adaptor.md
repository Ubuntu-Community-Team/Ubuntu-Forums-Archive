---
title: "Driver for new wireless usb adaptor"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by ZippyBubba on 2012-06-25
I got a new wireless device thats linux compatible and it doesnt work on ubuntu.its a netis wf-2116.  and advice?

---

### Post by wildmanne39 on 2012-06-25
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by chili555 on 2012-06-25
I always lose the coin toss and get the unusual devices! Please open a terminal and run and post:```
lsusb
lsb_release -d
```Thanks.

EDIT: I guess the Wild Man lost the toss. Sorry!

---

### Post by haqking on 2012-06-25
drivers and guides here [http://www.netis-systems.com/download.asp?pdtid=142](http://www.netis-systems.com/download.asp?pdtid=142)

---

