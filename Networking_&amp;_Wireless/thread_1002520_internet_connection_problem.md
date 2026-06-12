---
title: "internet connection problem"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by tchicou on 2008-12-05
Hi everyone!
I'm having problems getting connected to the internet, can somebody help!!!!!!!
I was runing Windows XP pro, and I decided to switch to ubuntu 8.10, Now I find out that I cannot connect to the internet.
I tried some of the solutions found in ubuntu forum hoping to fix my problem, but still I can't figure it out.
Do I need to dowload a driver? or to buy a network card?
Please can you help!!!!!!!!
Thanks for your time.:lolflag::lolflag:

---

### Post by Kevbert on 2008-12-05
Welcome to Ubuntu.
How are you trying to connect to the internet ? dialup, wireless or wired ?
You may need to download a driver.  Please go to Applications-Accessories-Terminal and enter the following commands
```
lspci
ifconfig
iwconfig
```
For each output highlight the text with your mouse and press Ctrl-Shift-C (to copy text) and open a new post and paste here with Ctrl-V (to paste). The first command list all pci devices, the second all comms interface devices and the last all wireless devices (and whether they're set up).

---

### Post by Iowan on 2008-12-05
> **tchicou said:**
> Do I need to dowload a driver? or to buy a network card? Was it on Internet as an XP machine?  If so, it *might* be a driver issue.  I'd ask about contents of */etc/network/interfaces* file, but the aforementioned information will be more useful to start with.

---

### Post by tchicou on 2008-12-05
> **Kevbert said:**
> Welcome to Ubuntu.
How are you trying to connect to the internet ? dialup, wireless or wired ?
You may need to download a driver.  Please go to Applications-Accessories-Terminal and enter the following commands
```
lspci
ifconfig
iwconfig
```
For each output highlight the text with your mouse and press Ctrl-Shift-C (to copy text) and open a new post and paste here with Ctrl-V (to paste). The first command list all pci devices, the second all comms interface devices and the last all wireless devices (and whether they're set up).

Thanks for that
 I am using a wired connection (broadband). I used the above information and this is what I've got.

Is there anything else to do?
Thanks in advance for your help.:confused:

---

