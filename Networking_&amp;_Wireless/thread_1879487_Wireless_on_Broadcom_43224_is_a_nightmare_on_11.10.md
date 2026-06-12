---
title: "Wireless on Broadcom 43224 is a nightmare on 11.10"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by Romu on 2011-11-11
Hi all,
My PC is a HP Envy 14 with a 43224 Broacom wifi chipset.

I didn't have any issue with wifi on 11.04. But on 11.10, it's pretty unusable. The wireless link gets down regularly or can work for hours but you can't be sure and it can cut every 2 mn. It's pretty unacceptable Ubuntu can be released with such a bad wifi.

I tried to removed the STA driver to get back to the free one (brcmsmac), and the situation is the same. So I found I just have to run "sudo service network-manager restart" to get working wifi for...I don't know, that's the surprise, 2 mns or hours.

I'm using Gnome-Shell, I don't know if this is the cause of the issue. But if someone can give to idea to fix the issue, I would greatly appreciated.

Thanks

---

### Post by praseodym on 2011-11-11
Hi, use the STA driver and blacklist the modules **bcma**, **brcm80211**, and **brcmsmac**. Reboot after that.

---

### Post by Romu on 2011-11-12
Thanks praseodym, I'll try this right now.

---

### Post by Romu on 2011-11-13
Kudo for praseodym, thanks a lot, that's perfectly fix my wifi!

---

