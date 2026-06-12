---
title: "Toshiba Satellite C855-S5343 - Wireless Keeps Dropping"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by BarfBag on 2012-12-30
Hello all!

I just purchased a Toshiba Satellite C855-S5343.  (Besides my operating system woes, I'm quite satisfied with it!)  I'm having a problem, though, that seems to be fairly common.  My wireless will drop randomly.  Now, the odd thing in this case is, the indicator will still show me as connected to the network.  The internet is what randomly drops.  I have ruled out issues with the router itself.  I've also tried all of the solutions I could find with a board search:

1.  Installing the linux-backports-modules-cw-* package made the Ethernet port start working - but it didn't make a difference in regard to the wireless.

2.  Attempting to compile the corresponding Realtec driver told me I was using the wrong kernel.  I'm currently using Ubuntu 12.10, and I could not find a source to compile for the 3.5 kernel series.

Is there something I'm missing?  I apologize if I left out some details (I'll provide anything upon request).  Thanks in advance!

---

### Post by Pjotr123 on 2012-12-30
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

... and please report which part worked for you (if at all).

---

### Post by BarfBag on 2012-12-30
> **Pjotr123 said:**
> Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

... and please report which part worked for you (if at all).

I have tried all of those solutions, apart from using the wrapper.  I'd prefer to use the native drivers, if possible.

---

### Post by BarfBag on 2012-12-31
Any ideas guys?

---

### Post by ahallubuntu on 2012-12-31
Did you look for a driver for the RTL8188CE on 

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

?

---

