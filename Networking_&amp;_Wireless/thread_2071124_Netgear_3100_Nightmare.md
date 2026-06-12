---
title: "Netgear 3100 Nightmare"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by xavieranderson on 2012-10-14
Hello fellas.

Just a forewarning, I am a novice to Linux. I am exited however into getting into Ubuntu.

I ran into the misfortune into owning one of the few netgear adapters that is not supported by linux. I do not have an ethernet option, my only source of internet is through this adapter.

I am running Ubuntu 12.04, 64 Bit.

[http://imageshack.us/a/img15/7413/sc1e.png](http://imageshack.us/a/img15/7413/sc1e.png)

I installed a terminal-based ndiswrapper that came with the ubuntu live cd. After I read from Chilli555's posts about a 64bit version of bcmnxx64. 

However, I am stuck as I do not know how to proceed, and I do not see any wireless options for connections at all!

---

### Post by xavieranderson on 2012-10-14
Ok, after much headache, I solved the problem. In-case anyone else has this problem, I did the following :

I had to uninstall the 32 bit driver, and I ran the following commands...

> sudo depmod -a
sudo modprobe ndiswrapper
dmesg | grep ndis
iwconfig

---

