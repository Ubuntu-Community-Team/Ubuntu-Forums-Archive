---
title: "very slow and unstable wireless connection under 11.04"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by fredlovecdl on 2011-09-05
Lenovo thinkPad T410 running under dual boot with Win7 and Ubuntu 11.04.
 
Problem: Under Win7 wireless connection is fine. However, with Ubuntu it is very slow and 
some time after the initial connection was established it is simply not working 
any more. 
 
network controller: realtek RTL 8191SEvB wireless LAN Controller (rev 10)
 
can anyone suggest a solution here? 
I really appreciate your help! Thanks!

---

### Post by praseodym on 2011-09-05
Hi,

the network-manager often has some problems with mixed WPA/WPA2-encryption. Better use WPA2-AES instead if possible.

Can you show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
dmesg | grep r8
```

---

### Post by pythonscript on 2011-09-05
Maybe look at this entire thread too: [http://ubuntuforums.org/showthread.php?p=11163026#post11163026](http://ubuntuforums.org/showthread.php?p=11163026#post11163026)

The Lenovo Thinkpad's, specifically the Realtek wireless chips they're often using now, have been having problems with Ubuntu 11.04.

---

