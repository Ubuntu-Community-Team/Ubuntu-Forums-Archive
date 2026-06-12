---
title: "Wireless help - new HP"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by _gary_ on 2012-06-13
Hi fokks,

I just got a new HP MINI 311-1037NR and installed Ubuntu (well, really Backtrack 5r1) on there via USB stick. 
My issue is, I can't find the correct driver... for my wireless.  So, basically, I have a full install, but no wireless.  I had this issue once before on a HP mini but for this laptop, I think I just need to pre-load the correct driver or module in the kernel, finding the right one is the issue.

Backtrack is built on Ubuntu, so this is why I am asking here.

If anybody has had a similar experience with wireless with this HP mini on Ubuntu and know the correct drivers... I need to load, that would help me out a whole lot.

Any help would be hugely appreciated.

Thanks in advance.

---

### Post by wildmanne39 on 2012-06-13
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

