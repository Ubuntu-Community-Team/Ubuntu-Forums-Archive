---
title: "Video problems - cannot install 12.04.4. Please help."
date: 2014-02-09
forum: Multimedia Software
---

### Post by victor_sk on 2014-02-09
Hello everyone,I've got Dell Inspiron 17R with 4200U processor.  ```
lspci | grep VGA
```Gives```
VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
```When I am in Live Desktop using Ubuntu 12.04.4 Live DVD, I am experiencing very distorted colors.  Everything is purple and green.  The screen is blurry and distorted.  I cannot install Ubuntu under these circumstances.Could someone please suggest what action I should take to fix this problem?Thank you.

---

### Post by victor_sk on 2014-02-09
Great joy and happiness!  I finally was able to install the appropriate version.  After reading Ubuntu's website with Dell-related content, I downloaded Version 12.04.1 for Dell machines.  Although my laptop version, Inspiron 17R 5737 was not on a list, the kernel that this Ubuntu version came with, 3.2 worked great with my video card.  I've updated it now to kernel 3.2.58 and it works fine too.

I then installed wireless support using information from this thread:

[http://askubuntu.com/questions/379440/wifi-not-working-on-ubuntu-12-04-dell-3521](http://askubuntu.com/questions/379440/wifi-not-working-on-ubuntu-12-04-dell-3521)

And I even now have wireless working too!  This was another problem I was facing because I could never get wireless to work with this kernel version.  Now it does, and I am very happy :D

---

### Post by cschroter on 2014-02-09
[http://www.ubuntu.com/certification/catalog/](http://www.ubuntu.com/certification/catalog/)

Thanks for the info.

Happy is good.

---

