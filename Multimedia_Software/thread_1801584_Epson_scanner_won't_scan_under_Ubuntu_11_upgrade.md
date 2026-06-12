---
title: "Epson scanner won't scan under Ubuntu 11 upgrade"
date: 2011-07-10
forum: Multimedia Software
---

### Post by tribbleva on 2011-07-10
I have an Epson Perfection 1650 USB 2.0 scanner that worked fine under Ubuntu 9 with xsane and simplescan. I had some network problems after upgrading to Ubuntu 11, so I completely wiped my laptop and installed Ubuntu 11 fresh a few days ago. This scanning problem is therefore on a nearly virgin Ubuntu 11 install.

Both SimpleScan and xsane can't get the scanner to scan. Upon starting a scan or a preview scan, the scanner starts to scan, but almost immediately stops and returns to its "home" position. xsane gives a message saying that "operation was cancelled," and simplescan does not give any error but just a white image.

There are no messages related to scanning in dmesg or /var/log/syslog.

I tried the gksudo xsane command, but in that mode xsane would not even find the scanner.

I removed all of the xsane packages and related lib packages with synaptic, but simplescan continued to fail. 

I removed simplescan and re-installed xsane, but xscan continued to fail.

Please help!! It's depressing when things quit working after "upgrades." 

Thanks,
tribble

---

### Post by tribbleva on 2011-07-12
Ideas? Anyone?

---

### Post by Tweak42 on 2011-07-27
My 10.10 upgrade to 11.04 did the same to my Epson Perfection 1650 scanner.  I followed a tip in this post and it started working again.

[http://ubuntuforums.org/showpost.php?p=10593292&postcount=10](http://ubuntuforums.org/showpost.php?p=10593292&postcount=10)

---

### Post by tribbleva on 2011-07-29
Tweak42! You are a godsend! I made that edit... and it worked! I had gotten so far as to verify that the problem existed with the latest version of SANE on another current, popular distribution, but hadn't found that tweak. Now I will no longer have to reboot with my Ubuntu 8.04 live CD to scan things. THANK YOU!!! :-)

---

### Post by northrnlt on 2011-08-02
Thanks Tweak.....Same problem and it works great now!

---

### Post by step_god on 2011-09-08
Thanks worked for me.

---

