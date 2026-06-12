---
title: "Wireless card will not activate"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by Krackinjack on 2010-03-31
Broadcom sta driver is installed and listed in Hardware Drivers but will no activate.

It did activate and run perfectly when booting from USB FLASH DRIVE running UNR on HP MINI  it has a external networkcard  power off switch on the front of it if that matters

OH YES I AM A  NEW>>>>BE   to the wonderful world of LINUX

---

### Post by bkratz on 2010-03-31
> **Krackinjack said:**
> Broadcom sta driver is installed and listed in Hardware Drivers but will no activate.

It did activate and run perfectly when booting from USB FLASH DRIVE running UNR on HP MINI  it has a external networkcard  power off switch on the front of it if that matters

OH YES I AM A  NEW>>>>BE   to the wonderful world of LINUX

Welcome, did you have a wired connection when you tried to activate it?

---

### Post by Krackinjack on 2010-03-31
No I did not

---

### Post by bkratz on 2010-03-31
> **Krackinjack said:**
> No I did not

I believe you are supposed to.

---

### Post by 2hot6ft2 on 2010-03-31
> **bkratz said:**
> I believe you are supposed to.
Yep, same as a graphics driver it has to download it.

---

### Post by Krackinjack on 2010-03-31
Well just tried  But no go

---

### Post by 2hot6ft2 on 2010-03-31
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```
Then check
System > Administration > Hardware Drivers
and since you mentioned Broadcom
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by Krackinjack on 2010-03-31
Thank you.... 2HOT..... The link you sent had the answer and it worked  THE WORLD IS ALL GOOD AGAIN

---

