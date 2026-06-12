---
title: "NetworkManager failed after updating kernel"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by lmintfans on 2009-06-22
Hi, all.
I met a special case. Someone may help me.
This case existed in both LinuxMint V7 and Ubuntu 9.04.
 
[For LinuxMint V7]
My Wireless adapter is Intel wireless 5100.
My Mint is Version 7 32-bit and the orignal kernal is 2.6.28-11-generic.
Yesterday, I updated my kernel to version 2.6.28-13-generic.
Then, i couldn't start my wireless card via NetworkManager.
The wireless option was in gray and showed "wireless is disabled".
I try many solutions (including ifup/ifdown/iwconfig/revising interfaces) to connecting a wireless AP; however, I failed again and again. 
Interestingly, I tried to install "wicd". 
Finally, I connected to the wireless AP via wicd.
Namely, my wireless adapter was no problem.
I also tried to re-install NetworkManager; however, NetworkManager still failed to start the wireless.
 
[For Ubuntu V9.04]
I performed the abovementioned processes in 32-bit Ubuntu V9.04.
I met the similar condition: NetworkManager failed after updating kernel.
I also tried to compiled a new kernel (2.6.30).
However, the problem happened again.
 
So, does anyone meet this problem? 
How to solve this problem for NetworkManager?
Thanks for help.

---

### Post by neogarv on 2009-06-23
It really helps if you switch your drivers over to use ndiswrapper. I don't have an idea how to do that for your specific wireless adapter. Good luck! :D

---

### Post by lmintfans on 2009-06-24
This problem can be solved.
Please check this article: [http://ubuntuforums.org/showthread.php?p=7509647#post7509647](http://ubuntuforums.org/showthread.php?p=7509647#post7509647)

---

