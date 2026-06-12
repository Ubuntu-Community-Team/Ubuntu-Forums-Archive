---
title: "Samsung N130 Netbook &amp; RTL8192E &amp; Wireless"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by Johnpr on 2010-11-30
[LEFT][LEFT]Has anybody been successful in getting a N130 with a RTL8192E wireless chip to access the internet? I’ve tried practically every suggestion quoted on this message board –downloading drivers, from Samsung and  Realtek which won’t open also linux versions with the same result, trying the Ubuntu compilation of Wine etc, etc. Am about to give up, which is a pity, because the Netbook version Ubuntu is very user friendly.  [/LEFT]
[/LEFT]

---

### Post by bkratz on 2010-11-30
Is this one of the ones you have tried?

[http://ubuntuforums.org/showthread.php?t=1383446&page=2](http://ubuntuforums.org/showthread.php?t=1383446&page=2)

---

### Post by Johnpr on 2010-11-30
[FONT=monospace]Many thanks for your prompt reply

[/FONT]Tried  "sudo apt-get install git-core
cd /tmp
git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/firmware.git

and got "The remote end hung up unexpectedly" 
Any thoughts?

Johnpr

---

### Post by tonyps on 2011-01-28
Evening,
Do not know if you are still working on this or if you have decided to use this as a door stop!! I have a Toshiba with the rtl8192e. The only reliable way I have ever found this to work, for me, is to use the ndiswrapper with the windows xp driver for this wireless device. It works great, no problems, as long as you can get past there not being linux support (reliable, that is) for the nic...
The best part with using ndiswraper and XP drivers is I do not have to reinstall after kernel updates....
Tony ...

---

