---
title: "how to fix wireless issue with 2.6.30-rcx kernel on the jaunty"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by nokuta on 2009-06-07
When I updated the system to 9.04(jaunty) on my laptop(intel inside), I found graphic performance sucks.

I found a thread there [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582") and fix the intel graphic issue by following its guild.

after I updated my Linux kernel to 2.6.30-rc8, I found it works smoothly with my intel graphic card. But a big issue is: no wireless available!

I google it and now I know two things:

1. My wireless card is Intel PRO/Wireless 3945ABG.
2. kernel 2.6.30-rcx does not contain Intel PRO/Wireless 3945ABG driver.

So I really want to know how to install Intel PRO/Wireless 3945ABG driver on the kernel 2.6.30-rc8? I did some homework but still don't very sure how to install iwl3945 drivers. All results from google just told me some way to install iwl 3945 drivers on the old kernel like 2.6.14, and they said there is no need to install this driver after kernel 2.6.24.

please help me, thanks!

---

### Post by kenyab2009 on 2009-06-07
how do you even scan for wireless connections??

---

### Post by Crafty Kisses on 2009-06-07
> **kenyab2009 said:**
> how do you even scan for wireless connections??

```
sudo iwlist wlan0 scan
```

---

### Post by PatrickVogeli on 2009-06-07
well, that's just plain wrong. The .30 kernel includes the iwl3945 drivers for sure, since I have the same card and it's working just fine.

Could you please attach the result of doing dmesg, lsusb and lspci?

---

