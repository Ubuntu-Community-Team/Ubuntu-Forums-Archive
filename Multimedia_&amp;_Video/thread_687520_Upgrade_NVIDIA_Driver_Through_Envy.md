---
title: "Upgrade NVIDIA Driver Through Envy"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by rykel on 2008-02-04
Hi pals,

Not too sure if this has been mentioned before... but I used ENVY to install the official NVIDIA driver on my Ubuntu Gutsy (and it works well!).

However, now there is a version 169.09 and so my question is, "How do I use ENVY to upgrade my driver to the latest one?"

Thanks for advising.

---

### Post by Foxray on 2008-02-04
The latest stable version of the Nvidia driver is 100.14.19 for ubuntu. Envy automatically updates your Nvidia driver if there is a new one out. to my knowledge version 169.09 is not yet stable for gutsy gibbon use just yet.

---

### Post by rykel on 2008-02-04
OK, thanks for that note... nevertheless I am happily running NVIDIA 169.07, installed by Envy. Which means 169.09 should not be too far off soon...

---

### Post by manimal347 on 2008-02-04
> **rykel said:**
> OK, thanks for that note... nevertheless I am happily running NVIDIA 169.07, installed by Envy. Which means 169.09 should not be too far off soon...

If you're "happily running" a driver, why upgrade? Unless the new driver promises a new feature or bug fix that offers you greatly enhanced utility, it's not wise to update. Fiddling with the video drivers can kill your Xserver, and create a situation that will take lots of mucking around on a terminal with Pico to fix. In fact, this rule is well-applied to most software in general. Leave "rolling update" state of the art systems to people who have advanced Unix skills, can trace errors and file bug reports, wage flamewars on the superiority of Emacs versus Vi, and know where just about every configuration file sits. Seriously, often very new packages are "broken," or have bugs that are only found in the field after the update has been out a while. Okay, I'm being slightly melodramatic, but cooking your xserver is really not fun, especially if you're using the computer as a production machine. If this was my computer, I wouldn't risk it.

---

