---
title: "ATI driver on kernel 2.6.20"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by DimaStranger on 2007-03-22
Guys, really need help.
I'm using Ubuntu 6.10, so when I installed it it had kernel 2.6.17 by default. So, I installed the ATI 8.36 driver and everything worked just fine. But I have interet connection thru VPN with mppc enabled, for which I had to rebuild the kernel (with support for mppc). I couldn't manage to do so with the 2.6.17 kernel, so I downloaded the new one, 2.6.20, from the Feisty repository. And it all went alright, kernel compiled ok. But now, with the new kernel, I cannot install the ATI driver once again, though I removed the previous one. When trying to build module fglrx-kernel... it just sais that the package cannot be built. 
P.S.: I was trying to install the same driver, 8.36.

Need help!

---

### Post by adam.tropics on 2007-03-22
Do you mean 8.34? Anyway, You need to make sure you have the kernel-headers for your currently used kernel installed. Basically, the second method [on this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") should do it, and take care of the headers etc. Just make sure to run it from your new kernel.

---

### Post by DimaStranger on 2007-03-22
Thanks... But this is what I've found on the page that you gave me a link to:

IMPORTANT: You have to recompile the kernel module after each kernel update! NOTE: the fglrx source code requires Linux 2.6.19 or lower. It is not yet prepared for 2.6.20.

OMG :( This sucks really bad...

---

### Post by adam.tropics on 2007-03-22
Try it anyway. Works for me!

---

