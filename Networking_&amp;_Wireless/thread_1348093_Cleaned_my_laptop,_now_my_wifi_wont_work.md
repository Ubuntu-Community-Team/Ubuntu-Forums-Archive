---
title: "Cleaned my laptop, now my wifi wont work"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by kkdogiedog on 2009-12-06
Before cleaning my compaq presario v2000 notebook i put in countless hours trying to get my wifi driver to work. I finally found the install command ( sudo apt-get install b43-fwcutter ) for the driver that makes my wifi work. Then my wifi was working perfectly. Then i decided to take apart my laptop so i could clean out all of the dust. to do this i had to take out the battery, hard disk, and network chip(which is broadcom). I got it all cleaned out, put it back together exactly how it was, turned it on and it popped up with a message saying "mount of file system failed". Then i typed in "fsck" in the command prompt provided and it worked like a charm, my computer started up just like it should, but there was one problem, my wifi didnt work just like it did before i installed the driver. i already unisntalled the driver with ( sudo apt-get remove b43-fwcutter ) and reinstalled it and it still didnt work. What can i do to make my wifi work again? please help me.

---

