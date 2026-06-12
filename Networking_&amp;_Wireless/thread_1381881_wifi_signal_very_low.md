---
title: "wifi signal very low"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by muddinyoreye on 2010-01-15
Hello all, I am very new to ubuntu and am having a slight problem with my wireless connection, I was running windows vista 32 bit (NOW UBUNTU 9.10) on my custom built pc with a TP-LINK TL-WN353GD wireless pci card, before on vista my wifi signal strength would be in the low 70% range with a speed of 54 Mbps from a access point roughly 250 yards away, now with ubuntu 9.10 signal strength in the 15-20% range with a speed of 1 Mbps. My question is, what is the best way to overcome this wifi signal strength and speed problem, it is a noticable performance disadvatange easily seen on a website like youtube where as before videos would play 95% of the time without having to stop and catch up, would a different wireless pci card be a better choice than what I have, or is the problem in the software as in a driver incompatability or lack of correct driver, not sure how to remedy the problem  ,,, any and all help would be greatly appreciated!   thanks;).

---

### Post by muddinyoreye on 2010-01-15
bump

---

### Post by muddinyoreye on 2010-01-15
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

---

### Post by jondodson on 2010-01-16
I've noticed the same thing.  I'm dual booting vista and 9.10 but the same hardware is reporting 70% in windows and 15% in Linux.  Even weirder, windows reports 3.8 Mbps and Linux reports 4.2mbps.  I've concluded that you can't really trust the signal strength meter (bit like on a mobile phone, where more bars doesn't necessarily equal higher 3G data speeds) but not to worry because it works fine anway.  Afterthought- I wonder if Linux calculates the number of bars displayed as (current data rate / maximum possible data rate) - that would explain the 15% I get based on a theoretical 802.11g maximum.  Jon.

---

### Post by JackRock on 2010-01-16
Can't answer on the signal *speed*, but I can answer on the signal *strength,* having had a lot to do with radio signals in the army.

The strength of the signal is unaffected by the software on a computer, as all the software and hardware that affects it is in the router/access point and its associated power source(s).  So unless you recently re-wired your house, I doubt the actual signal strength is waning.

What MAY be the case is Ubuntu/Linux has a different scale for how strong a signal can be, therefore giving a different percentage.  Connection to that signal may be affected by the client computer's OS, so connection speeds are affected there.  Maybe somebody with more knowledge on Ubuntu wireless hookups can comment.

But I stand by my statement that if the wireless signal truly is lower, then the problem is the router/AP hardware, not your OS.  I'm betting is a "perception" of Linux.

---

