---
title: "Keeping Wireless Enabled"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by PeteyPete on 2009-11-08
First, I'd like to thank all of those who make this forum such a valuable resource to newbies like myself.  While I'm still a total novice, the advise on this forum got me up and running, and I even managed to get my Marvell Topdog EC85 working (though it took me 2-3 hours of copy/pasting into the terminal). 

My issue is keeping the wireless enabled.  When I restart my computer, I'm forced to copy/paste the following in order to enable my wireless card:

[php]sudo ndiswrapper -m

sudo depmod -a

sudo modprobe ndiswrapper
[/php]Any ideas on how to keep it enabled?  

PS...Please be easy on a non-coder newbie...almost any solution requires a baby-steps approach and explanation.

---

### Post by ZeroSpawn on 2009-11-08
I would make a "New File" insert the 3 lines of commands. Then goto "System" -> "Preferences" -> "Start Up". Add the file and see if it will run it next time u boot.

If that doesnt work I hope someone knows how to wright a small prog to exec these commands.

---

