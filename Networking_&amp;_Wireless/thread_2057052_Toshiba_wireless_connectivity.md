---
title: "Toshiba wireless connectivity"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by Kilted on 2012-09-12
I have this same computer and wireless card, I can see my wireless network, but can't connect to it (it just tries to connect infinitely)I'm fairly certain this is a driver problem. How can install the drivers without an internet connection?

---

### Post by Kilted on 2012-09-12
If it makes any difference, my ethernet controller is an AR8162 instead of the AR8152.

---

### Post by lisati on 2012-09-12
*Thread moved from [http://ubuntuforums.org/showthread.php?t=2055245](http://ubuntuforums.org/showthread.php?t=2055245) to **Networking & Wireless**.*

Sometimes machines from the same manufacturers have different hardware, which can result in different solutions to what at first sight looks like the same problem. My main laptop, a Toshiba as well, has a different chip again!

---

### Post by Kilted on 2012-09-12
I know that, i checked my wireless hardware against the original posters. we have the same except for one minor difference noted above.

---

### Post by Kilted on 2012-09-12
Oh whoops my mistake, my computer is the satellite **C855**

---

### Post by lisati on 2012-09-12
It wasn't obvious from your question if you had tried the solution mentioned in the other thread, and if so, what level of success you had.

---

### Post by varunendra on 2012-09-13
Didn't look at the thread *lisati* pointed to (I'm on a limited gprs connection plan), would be better if you post some details here including following outputs:
```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
iwlist scan
```

and when it is trying to connect (for a while):
```
dmesg | tail -20
```

---

### Post by Kilted on 2012-09-13
okay, I've seemingly moved from one problem to another. 
I've successfully installed ndiswrapper and ndiswrapper-utils but now my internet connection drop after a few minutes and i get a package system is broken error in update manager.
 How can i remedy theese new issues?

Here's the details of the report:
The following packages have unmet dependencies: 

python-glade2: Depends: libglade2-0 (>= 1:2.6.1) but 1:2.6.4-1ubuntu1.1 is installed 
               Depends: libglib2.0-0 (>= 2.15.0) but 2.32.3-0ubuntu1 is installed 
               Depends: python (< 2.6) but 2.7.3-0ubuntu2 is installed 
               Depends: python-gtk2 (= 2.12.1-0ubuntu1) but 2.24.0-3 is installed 
               Depends: python-support (>= 0.7.1) but it is not installed

EDIT: used the instructions in lisati's link and my internet connection appears to me consistant and stable. But i still get the package system is broken error

---

