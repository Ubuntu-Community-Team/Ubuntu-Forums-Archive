---
title: "Laptop-mode and suspend"
date: 2010-09-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by manequin on 2010-09-14
I have upgraded to Maverick lately and noticed, that if I want to install laptop-mode-tools I have to remove pm-utils package. But, without this package I can't suspend my latop. I get an error:
```
Computer failed to suspend.

Failure was reported as: Failed to spawn: Failed to execute child process "/usr/sbin/pm-suspend" (No such file or directory), stdout:(null), stderr:(null)
```
I want to install both packages to have better control on power saving when on battery and to be able to suspend.

---

### Post by cariboo on 2010-09-14
According to synaptic, pm-utils is a recommend for laptop-mode-tools, but when you try to re-install it, it removes laptop-mode-tools, I would suggest reporting a bug.

---

### Post by dannyboy79 on 2010-09-16
i have not yet ran ubuntu soley on a laptop. well i recently picked up a gateway t-1625 for $150 cause the co-worker i bought it from couldn't get vista back on it after a melt down of virus's so she just bought a new laptop. 
AMD Turion TL-60 2GHz
2GB DDR2
250GB Hard Drive
DVD±RW
10/100 + 56k + 802.11g
HDMI Output, Radeon X1270 Video

anyway, i downloaded the desktop verison of 10.10 beat and it installed just fine, all hardware is happy and working. BUT, WOW, the battery only lasts about 2 hours, if that. It was fully charged and I took it off AC power around 7:30 pm and around 9 pm it said it only had 17 mins left. So i need to either download and install the netbook version OR investigate what I need to do to get decent power usage. Probably install laptop-mode or pm-utils. I found this thread and will investigate these software packages. If I need to report a bug I will.

My question and probably not appropriate in this thread but i'll ask anyway, does netbook version run on laptops as well. I figured the netbook version only really is that due to instead of having the 3 pulldowns at the top left, it has like a cairo-dock selection thing for apps. Will it fill the 14" screen? Anyone who has any knowledge of using netbook version on laptops i'd love to hear your usage stories. Good or Bad. thanks

---

