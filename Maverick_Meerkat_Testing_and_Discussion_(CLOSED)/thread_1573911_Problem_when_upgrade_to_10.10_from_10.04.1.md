---
title: "Problem when upgrade to 10.10 from 10.04.1"
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ffjjkk on 2010-09-13
Hello!

I upgraded my ubuntu from 10.04.1 to 10.10 but i can not log in to my account (GUI is not start).

I used NVIDIA driver, not ubuntu default VGA driver.

Many thanks!

---

### Post by Elfy on 2010-09-13
moved to maverick forum

---

### Post by brydonhunter on 2010-09-13
I had the same issue with my ATI drivers. I removed the ATI drivers 
apt-get from the CLI. When I rebooted, the GUI came up using the standard video drivers.

Hope this helped.

Scott

---

### Post by ffjjkk on 2010-09-13
Thanks brydonhunter!

But how to know the package name to remove. I installed NVIDIA 256.44 driver.

Thanks!

---

### Post by ffjjkk on 2010-09-13
I solved this problem. By that way

Go to Low graphic mode (in recovery mode on boot menu) download and install newest NVIDIA driver (version 256.53 for my geforce 9400GT)

Reboot and everything is okay!

Thanks!

---

