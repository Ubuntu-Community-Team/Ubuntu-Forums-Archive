---
title: "Lucid freezes with compat wireless patch"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by ssc351 on 2010-11-23
Hey Guys,

I've got an atheros ar9287 based card with the ath9k driver from the base install of lucid and I installed a compat wireless patch via this thread: [http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)

to fix the issue of the card being stuck on a given channel when using aircrack.  Now, my system freezes up after about a minute or two.  If I leave the wireless card off, everything runs fine no problem.  I uninstalled the compat wireless driver via the readme just make uninstall in the compat-wireless folder, but I still get the freezes.  So I assume it has something to do with the patches.

I have no idea how to remove the patches.  Can anyone help me with this or is there a way to get everything up and running so the original problem of being stuck on a channel is fixed?

Thanks!

---

### Post by ssc351 on 2010-11-24
bump...please help would love to get my wireless working properly again.

---

### Post by ssc351 on 2010-11-24
I think I got it solved by uninstalling the backports and reinstalling them...not exactly sure what that did, but it seems to be working now for anyone that comes up with a similar problem

---

### Post by thatllmovethechains on 2010-12-16
ssc351,
I haven't seen this mentioned on other forums but I'm getting the same freezes you described since I installed the patch last night. can you explain how you removed the backports and reinstalled them? This would mean undoing the patch such that aircrack-ng no longer works, right?

Thanks

---

### Post by jaylc005 on 2011-12-02
Im also having trouble with this, posted on the forum but thought I would bump this up if its ok to do so, to see if the original poster is still around to offer advice on uninstalling and reinstalling backports, ide like to know which modules were uninstalled..

---

