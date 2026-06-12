---
title: "Dell Inspiron 1520 - Ubuntu 12.04 LTS not picking up any internet"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by xSCCMx on 2013-02-09
So when I installed ubuntu, my wireless and wired connection stopped working, I am extremeally frustrated at the inability of Broadcom to make open source drivers that can work out of the box.

---

### Post by ahallubuntu on 2013-02-09
~

---

### Post by xSCCMx on 2013-02-09
[http://www.amazon.com/Intel-4965AGN-Next-Gen-Wireless-N-Network/dp/B000RFPBQQ/ref=cm_cr_pr_product_top](http://www.amazon.com/Intel-4965AGN-Next-Gen-Wireless-N-Network/dp/B000RFPBQQ/ref=cm_cr_pr_product_top)

Do you think this would be compatable? I've done some research on Dell's website.

---

### Post by mörgæs on 2013-03-20
In case someone finds the thread: 
```
sudo apt-get install linux-firmware-nonfree

```and a reboot solves the problem (if we are dealing with a Broadcom BCM4311).

---

