---
title: "Another Asus EEE PC drama!"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by FuneralQueen on 2010-08-13
Hi there :)

After trying for several hours (to no avail), I'm hoping someone can give me a definite solution!

I recently (yesterday) bought a Asus EEE PC 1001PX.

The wireless card is a Atheros AR8132.

I installed the latest Netbook remix - everything (including wired network) works perfectly, except the wireless!

So, first I tried the steps at the Ubuntu Help page for the Asus EEE PC. (EEEPC Fixes page). No good.

Then I searched the forums - it seems as though the EEE PC comes with different wireless cards, sadly, nothing I found for MY card seemed to work (and strangely enough, everyone linked the OP to other posts for other cards.. it all got a bit convoluted!)

So the only "good" thing to come out of it, is at least now I have a "wireless" menu option (there was none before) - however it is grayed out completely :(

So after everything that I tried (including google searches which led me to random blogs, which suggested downloading jaunty packages - which didn't work either!) - I am reaaaaaally hoping that someone could perhaps spell out a easyish-to-understand way of making my wireless work!

I really do love Ubuntu and I don't want to go back to XP :\

Thank you!!

---

### Post by mikewhatever on 2010-08-14
Have you installed the wireless backport modules?

---

### Post by NikoNZ on 2010-08-16
I had the same problem on my new 1001px and this solution worked for me:

.....

2) Installed ndiswrapper using "Ubuntu Software Center"

3) Downloaded "Wlan_NE785H_GE112H-V7_7_0_377_XP.zip" from the Asus website, and extracted the content.

4) Ran ndiswrapper and added netathw.inf driver. Got an error message, ignored it!

5) Rebooted, and it worked!


found it @ [http://ubuntuforums.org/showthread.php?t=1479058](http://ubuntuforums.org/showthread.php?t=1479058)

the post is by Mathieup75, who did a great job of putting it into plain language I could understand :) Good luck.

---

### Post by LightningCrash on 2010-08-16
I had Atheros problems on my netbook, I ended up swapping in an Intel 3945ABG, I found them online for $5 + ship.


You can find Intel 4965AG cards for around $15 + shipping.


It's sad but they really do work better than the Atheros by far.

---

