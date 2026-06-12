---
title: "Suspend leaves fans running"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by guv999 on 2010-10-07
Hi
When I suspend in Maverick, the hard disk spins down, but the fans continue to run.   I would like to log a bug, but would have no idea what information would be needed to do so for this type of issue - if anyone could advise what to include or any logs etc that would be appreciated.   Thanks

---

### Post by 23dornot23d on 2010-10-07
Follow the instructions here for reporting bugs [LINK]("https://help.ubuntu.com/community/ReportingBugs")

First you need to join[ launchpad]("https://launchpad.net/%7Elaunchpad-beta-testers") .... we all do it ..... then its easy after that .....

I had a similar problem on one USB drive before ..... but it seems ok now ..... 

what is your kernel version ?

Type this in a terminal to see ........

uname -a

---

### Post by guv999 on 2010-10-08
Hi
I am running kernel

 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux

I have now logged a bug as well - thanks for your help

---

### Post by cariboo on 2010-10-08
Bug #?

---

### Post by guv999 on 2010-10-09
Hi
Bug number is Bug #657039

---

### Post by x-shaney-x on 2010-10-09
I know various USB devices can cause this.
I had a logitech wireless mouse and keyboard set and had the same problem when using that.

Only thing I could do was disable the legacy USB mode in the bios which made it suspend properly BUT I was unable to select anything from the grub menu.

---

### Post by guv999 on 2010-10-09
[QUOTE=x-shaney-x;9943185]I know various USB devices can cause this.
I had a logitech wireless mouse and keyboard set and had the same problem when using that.

Guess what I bought last week.....Logitech MK250 wireless keyboard and mouse!   Then installed the RC before using it.

Out of interest should I update the bug to confirm that I believe this to the cause?

Thanks

---

### Post by x-shaney-x on 2010-10-09
It would be worth adding it to the bug report I reckon.

I did eventually switch back to my wired keyboard at the time because I couldn't find a satisfactory workaround.

---

