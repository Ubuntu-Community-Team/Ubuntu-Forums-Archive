---
title: "S series sony laptop wireless not working in ubuntu 10.04"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by mmghd on 2012-05-13
Hi 

I have a new S series sony laptop.
I installed ubuntu 10.04 (CAELinux) on it and I found that it wireless doesn't work.
As chili suggested I got the output of these commands on terminal:
```
  lspci -nn | grep 0280
rfkill list all
```The output f the first line is:
```

02:00.0 Network controller [0280]: Intel Corporation Device [8086:0091] (rev 34)
```and the output of the second line is nothing.
Any thoughts?

Thanks in advance.

---

### Post by chili555 on 2012-05-13
That device is Intel Centrino Advanced-N 6230 BGN and is covered in later Ubuntu versions by the driver iwlagn or iwlwifi. We could try to force the driver to recognize your device with no guarantee of success. You could also just install Ubuntu 12.04, the newest LTS version, and be running in 20 minutes.

The Intel 6230 had not been introduced when 10.04 came out, so it's not covered in that two-year-old version.

What is your preference? I will be happy to help in either case.

---

### Post by mmghd on 2012-05-13
I have lots of applications on my Ubuntu and I want to keep them.
I am ready to force the driver to recognize my device.
Do you think upgrading Ubuntu 10.04 to 12.04 solve my problem too? Is upgrading possible?

---

### Post by chili555 on 2012-05-13
> Do you think upgrading Ubuntu 10.04 to 12.04 solve my problem too? Is upgrading possible?Yes and yes. [https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by mmghd on 2012-05-14
Many Thanks chili.

---

