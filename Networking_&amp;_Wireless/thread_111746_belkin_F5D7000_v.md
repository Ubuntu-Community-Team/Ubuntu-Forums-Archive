---
title: "belkin F5D7000 v?"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by baldy1324 on 2006-01-02
hello i am trying to get my belkin F5D7000 working. (1)i am not sure how to tell which version i have-so could someone tell me how to tell which version i have. (2)which drivers would this version use? i know some versions use chipsets with reverse engineered drivers and some need to use ndiswrapper.
someone please help!!!

---

### Post by lubod on 2006-01-04
As far as I can tell (nice of the manufacturers to keep everyone in the dark with their "proprietary secrets, huh?)

There are 5(?) versions of this card, with at least 3 different chipsets! Each chipset requires different drivers.

The v1000 and v2000 were Broadcom chipsets, meaning they work easily in Mac OS X and Windows, but in Linux only NDIS Wrapper and the windows drivers are of any use, Broadcom is Open Source hostile and refuses to release information to make legal drivers possible.

v3000 (and maybe v4000 too?) use Ralink chipsets. They are relatively Open Source friendly, their official driver download page lists both Mac OS X and Linux as supported systems.

I got stuck with a v5000 thinking I was buying one of the above, and it has an Atheros chipset. They are supposed to have Linux native support, and a Mac OS X driver (3rd party - Orangeware). So far neither of those has gotten me connected to anything.

One of the other threads mentions wireless info, somewhere here on the Ubuntu site.

Supposed to have info on which chipsets and drivers work best.

Here is the thread:

[http://ubuntuforums.org/showthread.php?t=105704&highlight=belkin+f5d7000](http://ubuntuforums.org/showthread.php?t=105704&highlight=belkin+f5d7000)

---

### Post by legatodnl on 2006-01-14
I never managed to get this card working. I resorted to a 11mbps card that I had lying around. Now i find it to outperform the fast belkin running on a windows laptop. strange

Dan

---

### Post by wclaps on 2006-01-14
What drivers have you tried already?  I can send you the ones that I found to work.

---

