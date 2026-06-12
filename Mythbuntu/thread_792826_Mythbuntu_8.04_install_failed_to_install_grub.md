---
title: "Mythbuntu 8.04 install failed to install grub"
date: 2008-05-13
forum: Mythbuntu
---

### Post by CornMaster on 2008-05-13
Over the weekend I upgraded my mythtv/ubuntu box to 8.04.  I did a fresh install (saving my recordings and DB of course), however, after the install completed, the machine wouldn't come to the grub menu.  Failed saying file not found.

After a few hours of messing around trying to figure out exactly what happened, and another clean install attempt, I got everything working.

I was using the AMD 64-bit Live CD version of the install, and I installed from the initial menu.

Basically what happened, is that the system installed, but failed to install grub.  I booted to the live CD, and installed grub from the command line onto the HDD in the boot folder.  Then I configured the mbr, then generated the menu.lst file.  Then when I rebooted, I had to edit the boot options because the paths were wrong because of where I mounted the HDD while using the live CD.  Then once I finally got in, I fixed the menu.lst for good.

Now, it's all working, and I was able to restore my DB, and everything is running smoothly now. :)  I learned a lot, but I still don't know what the problem was.  Posting hoping that someone can enlighten me.

I also noticed that during the install I changed some of the options, installed some services, and disabled some pluggins, but when the install completed, all the defaults were there, and I had to redo everything.  Not exactly sure why it didn't follow my install instructions either.

Anywho...if anyone has any insights, that would be cool. :)

---

### Post by superm1 on 2008-05-13
> **CornMaster said:**
> Over the weekend I upgraded my mythtv/ubuntu box to 8.04.  I did a fresh install (saving my recordings and DB of course), however, after the install completed, the machine wouldn't come to the grub menu.  Failed saying file not found.

After a few hours of messing around trying to figure out exactly what happened, and another clean install attempt, I got everything working.

I was using the AMD 64-bit Live CD version of the install, and I installed from the initial menu.

Basically what happened, is that the system installed, but failed to install grub.  I booted to the live CD, and installed grub from the command line onto the HDD in the boot folder.  Then I configured the mbr, then generated the menu.lst file.  Then when I rebooted, I had to edit the boot options because the paths were wrong because of where I mounted the HDD while using the live CD.  Then once I finally got in, I fixed the menu.lst for good.

Now, it's all working, and I was able to restore my DB, and everything is running smoothly now. :)  I learned a lot, but I still don't know what the problem was.  Posting hoping that someone can enlighten me.

I also noticed that during the install I changed some of the options, installed some services, and disabled some pluggins, but when the install completed, all the defaults were there, and I had to redo everything.  Not exactly sure why it didn't follow my install instructions either.

Anywho...if anyone has any insights, that would be cool. :)
If all of the defaults were there, that indicates that the install didn't complete.  Please post a copy of /var/log/syslog from the live session or /var/log/installer/syslog from the resultant system (if it exists).

No other way to really debug an issue like this.

---

