---
title: "fglrx on 3870, constant reboot loop"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by syngiun on 2008-03-31
Is there anybody who has successfully installed drivers for ati 3870 on hardy?

If so could you *please* tell me how you made it work.

ati 3870
hardy 8.04 beta, updated (installed from the 64-bit PC (AMD64) desktop CD)

I have tried the following
 Ubuntu how to
 EnvyNG
"Hardeare drivers" in the admin menu,
Manual download / install with "sh ati-driver-installer-8-3-x86.x86_64.run"
 
No matter what method I try, I always get 2 possible outcomes.

1) continuous reboot loop
OR
2) white screen after login

I have been able to log in to a failsafe session

---

### Post by comradekingu on 2008-04-13
I got the same problem. Havent looked into it yet, but i'll make sure to check this tread for fixes workarounds or post my findings.

---

### Post by sayems on 2008-04-29
"sudo apt-get remove xorg-driver-fglrx"

---

### Post by comradekingu on 2008-06-27
I managed to get it working on the i386 edition (32bit) Then i went back to AMD64 (64bit) because i thought the problem was inherrent in the early beta support of RV670 in fglrx 8.3 (?)

To my despair the problem was still there. Im now back to 32bit Ubuntu 8.04.

I think the problem may lie in 64bit drivers for the X48 southbridge. I have a Gigabyte GA-X48T-DQ6 mainboard.

So if you just want something that works i suggest you try the i386 version instead. I hope someone has a solution for AMD64 though. Feel free to ask questions, i'll answer anything if im able to.

---

### Post by comradekingu on 2008-06-29
I managed to provoke the WSOD on 32 bit aswell. It has to do with compiz. Since compiz is set to "normal" and not "none" by default that explains why this happens when the fglrx-driver is installed.

I might give the 64bit version another try, but im fairly sure i uninstalled compiz there too...

---

