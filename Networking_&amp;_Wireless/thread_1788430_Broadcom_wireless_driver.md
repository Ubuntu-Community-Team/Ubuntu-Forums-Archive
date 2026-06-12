---
title: "Broadcom wireless driver"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by elmar93 on 2011-06-22
Hi, I cant get my wifi to be working.. I tried searching all over the net for the answer and did many things but to no avail. I installed DKMS and bcmwl-kernel-source, my broadcom card is 432b rev 01

I was wondering if any1 could help me since I tried all the solutions i could find..

So far, it can detect all available wireless network, but it cannot connect, and there is also no driver at the aditional driver

First timer on ubuntu and using 11.04, dont have any wired internet connection

I also installed b43 fw cutter, and broadcom sta common.. tried to install broadcom sta source, but it states I need a dependancy and when I download the dependancy, it breaks with something..

---

### Post by jasonmanchu on 2011-06-22
the dependency should be in the iso file of the ubuntu disk. ill investigate more since it was a while ago.
which card do you have?

---

### Post by elmar93 on 2011-06-22
i installed dkms, my card is 432b rev01.

---

### Post by bkratz on 2011-06-23
This is a pretty good thread about the Broadcom devices

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by TBABill on 2011-06-23
You can try [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) and follow the instructions for no internet access. However, it's imperative you know both what card you have (it'll be a bcm43xxx or something like that) and which driver you want/need (STA or b43).

---

