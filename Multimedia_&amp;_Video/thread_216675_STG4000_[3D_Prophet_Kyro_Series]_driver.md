---
title: "STG4000 [3D Prophet Kyro Series] driver"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by da85 on 2006-07-15
I everyone!

I am a comlete Linux newbie so I would be grateful if someone could help me with a problem I am having with my video card drivers.

The graphics of linux on my computer is really laggy compared to windows. I think this is because the correct drivers for my video card are not installed. My video card is an STG4000 [3D Prophet Kyro Series].

Could anyone possibly tell me how to install the driver for this video card in Ubuntu so that I can get my graphics working properly?

Any help would be much appreciated.

---

### Post by AR_Kozz on 2006-09-29
Well you posted this a few months ago and I suppose if there's an answer you've found it by now...

but I'm in the same situation more or less, only used Linux a few months, and trying to get a Kyro II card to work.

From the company there is nothing for linux version 2.6 or above, their download site gives only documentation; I've found a few scraps of code written by 3rd parties but have no clue if it's usable or how to install;

there is a Kyro module in /root/lib/module/drivers/video, but it either is not effective or I don't know how to install it;

If you've figured this out maybe could you reply with details?

---

### Post by usewisdom on 2007-02-21
Apparently this video card is no longer actively supported by Xorg. The card works, but in very slow motion.

In a terminal (Applications | Accessories | Terminal), if you run this command:
```
lspci
```
you will get something like this:
VGA compatible controller: STMicroelectronics STG4000 [3D Prophet Kyro Series] (rev 01)

For those stumbling across this problem, there's a [related thread here]("http://ubuntuforums.org/showthread.php?p=2172605").

---

