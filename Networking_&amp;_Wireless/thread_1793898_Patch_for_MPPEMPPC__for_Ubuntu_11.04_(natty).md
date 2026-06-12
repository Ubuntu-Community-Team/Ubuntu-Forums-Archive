---
title: "Patch for MPPE/MPPC  for Ubuntu 11.04 (natty)"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by muradcsc on 2011-06-30
Hi
 
I have got a Ubuntu 11.04 (Codename natty) Kernel Version : 2.6.38-8-generic-pae. I want enable PoPToP PPTP + MPPE 128bit Encryption + MPPC Compression VPN Server on that.
 
I am looking for patch for MPPE/MPPC support of the kernel 2.6.38-8 (Ubuntu 11.04 natty)
 
Can anyone help me 
 
regards
 
Murad

---

### Post by poolet on 2011-06-30
Check the following links:: 

[http://mppe-mppc.alphacron.de/](http://mppe-mppc.alphacron.de/)

[http://yablochkin.net.ru/mppc/](http://yablochkin.net.ru/mppc/)

---

### Post by muradcsc on 2011-07-01
Thanx for your reply. 
 
I am looking for patch kernel 2.6.38 and above links contains patch upto 2.6.32.

---

### Post by birdwes on 2012-07-05
After much desparation of not being able to find one I patched MPPC for Kernel 3.2.21 myself.  Here is the result:

linux-3.2.21-mppe-mppc-1.5.patch

[http://mailstation.co.uk/2012/07/patching-recent-linux-kernels-2-6-15-for-mppe-and-mppc-vpn/](http://mailstation.co.uk/2012/07/patching-recent-linux-kernels-2-6-15-for-mppe-and-mppc-vpn/)

Note that the files have moved into a ppp folder in the 3.2 kernels.  You'll have to check what is appropriate when you edit the patch file to the Kernel version that suits you.

---

### Post by wildmanne39 on 2012-07-05
Thanks for sharing, it is an old thread so it has been closed.

---

