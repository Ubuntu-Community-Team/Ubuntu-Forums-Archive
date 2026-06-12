---
title: "Blacklisting b43-pci-bridge"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by Idefix82 on 2009-05-13
How do I stop the driver b43-pci-bridge from loading? I have blacklisted ssb, b43 and b43-legacy but the said driver still takes control of the wireless card, instead of ndiswrapper.
Thanks in advance!

---

### Post by Idefix82 on 2009-05-14
I am sure that the answer to my question must be well-known to the gurus here, so bump.

---

### Post by Idefix82 on 2009-05-15
Bump 2.0

---

### Post by t0mppa on 2009-05-15
Same thing happening here (on my friends laptop), after each reboot, have to run the same old commands. Even though ssb is blacklisted and ndiswrapper is on /etc/modules, where it should get automatically loaded. ```
sudo rmmod ssb
sudo depmod -a
sudo modprobe ndiswrapper
``` Guess making a shell script for those and executing it during login would work, but seems a bit of a workaround instead of a fix.

---

### Post by Idefix82 on 2009-05-16
So it does seem to be a genuine problem. Strange!

---

### Post by padibona on 2009-11-04
Yes I have the same problem, b43-pci-bridge still pops up after blacklisting it.

---

### Post by padibona on 2009-11-04
OK fix for me was to run the Hardy fix at

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix)

Hope that works!

---

### Post by Ayuthia on 2009-11-04
You might try:
```
sudo update-initramfs -u
```
It should update the system so that it will not load the b43 modules when the system starts up.

Hope that helps.

---

### Post by sergeantkeg on 2010-08-19
> **Ayuthia said:**
> You might try:
```
sudo update-initramfs -u
```
It should update the system so that it will not load the b43 modules when the system starts up.

Hope that helps.

I was having the same problem and this finally fixed it, among other things.  Thanks!

- Linux SuperUltraN00b

---

