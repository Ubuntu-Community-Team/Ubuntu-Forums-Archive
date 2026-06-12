---
title: "screensaver won't start in myth"
date: 2010-02-06
forum: Mythbuntu
---

### Post by linuxhippy on 2010-02-06
I am running mythbuntu 9.10.  I am able to start the screensaver on the xfce desktop, but it doesn't start when I'm not watching TV in myth.  Why?

---

### Post by tgm4883 on 2010-02-06
It's disabled when playback starts. Why would you want a screensaver to show up during playback.

:EDIT:

I reread your question. I think screensaver is disabled when mythfrontend is started, but DPMS should still work.

---

### Post by linuxhippy on 2010-02-06
my monitor isn't going into a powersave either...I did set it up to go into powersave after 15 minutes of no use.

---

### Post by superm1 on 2010-02-07
Actually it's a bug with gnome-screensaver changing API's during 9.10 that doesn't work in xfce.  For 10.04 we're switching to xscreensaver.  You can switch during 9.10 if you'd like too.

---

### Post by linuxhippy on 2010-02-07
> **superm1 said:**
> Actually it's a bug with gnome-screensaver changing API's during 9.10 that doesn't work in xfce.  For 10.04 we're switching to xscreensaver.  You can switch during 9.10 if you'd like too.

That worked well.  I did this:

sudo aptitude install xscreensaver

After installation there will be 2 screensaver entries in the menu.  Pick the first one, it will then want to stop gnome-screensaver and start xscreensaver.  I set it up to blank in 10 minutes.  It does not blank the screen when I watch TV but does blank when just sitting there waiting to record.

---

