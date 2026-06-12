---
title: "Wireless problem with Lenovo Thinkpad Edge E430 (Intel® Centrino® Wireless-N 2230)"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by bharathhk on 2013-06-15
I want to enable wireless in my Lenovo Thinkpad Edge E430 3254 machine, having Intel Centrino Wireless-N 2230. I'm running Ubuntu 11. Also I'm not able to find downloads of compat wireless old @ wireless.kernel.org. Can anyone tell me what's the new location? Please help me out.

Thanks in advance.

---

### Post by chili555 on 2013-06-15
Here? [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

I suggest you try to match your downloaded version to your running kernel version as close as you can:```
uname -r
```You might also look in Synaptic for linux-backports-modules-cw.

---

