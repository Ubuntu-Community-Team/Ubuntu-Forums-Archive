---
title: "B43 Driver"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by rickm1945 on 2012-09-08
I installed xorg edggers and lost my wireless. I need to install b43 driver. What is the command to identify the wireless adapter? Is there a way to install the b43 drive without internet connection?

---

### Post by chili555 on 2012-09-08
Unless you are running Ubuntu 1.10 Dangerous Dinosaur, b43 is already included. Please try loading it again:```
sudo modprobe b43
```If that didn't do it, we'll do some diagnostics:```
lspci -nn | grep 0280
rfkill list all
dmesg | grep b43
```Thanks.

---

### Post by rickm1945 on 2012-09-08
> **chili555 said:**
> Unless you are running Ubuntu 1.10 Dangerous Dinosaur, b43 is already included. Please try loading it again:```
sudo modprobe b43
```If that didn't do it, we'll do some diagnostics:```
lspci -nn | grep 0280
rfkill list all
dmesg | grep b43
```Thanks.
Got it thanks for the help.

---

### Post by chili555 on 2012-09-08
Got it? Got ittt??? Meaning that loading the module fixed it? Does it persist after a reboot? Do we need to take additional measures to be sure it does?

---

### Post by rickm1945 on 2012-09-09
> **chili555 said:**
> Got it? Got ittt??? Meaning that loading the module fixed it? Does it persist after a reboot? Do we need to take additional measures to be sure it does?
Yes, it's fixed. Sorry for not saying so. Everything works great ad thank you for the help. I had some other problems that presented themselves after installing a ppa to fix my graphics. So I had to install Ubuntu 12.04 again. What you helped me with did work.

---

### Post by chili555 on 2012-09-09
Glad it's working!

---

