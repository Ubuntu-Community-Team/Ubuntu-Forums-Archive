---
title: "multiple monitors"
date: 2010-09-11
forum: Multimedia Software
---

### Post by rayandrews on 2010-09-11
Hi,

I'm making about my fourth 'push' into Linux, trying to get away from the Empire.  Slackware wouldn't find my printer or my sound, but Ubuntu found both without trouble. However, I'm a multiple monitor fanatic -- can't compute without it!  XP gives me my three monitors effortlessly but I can't find anything that works with either Slackware or Ubuntu.  'Xorg -configure' gives me an xorg.conf that looks like it should do the job but it ends up with no monitors working at all.  However, all three monitors work if I cut down xorg.conf to just that one card/monitor -- so all the hardware works, but not together.  At one point I had all three lit up with the screensaver, but it crashed as soon as I moved the mouse cursor.

There's lots of  fragmentary, out of date, wrong distro, and just plain wrong information out there, so I'm getting rather discouraged.  

Oh, 'lspci' shows all hardware accurately, so Linux must at least 'see' it all. 'xrandr', however sees only one monitor, ditto with the multiple monitor setup thingie.

Save me from the Borg!

---

### Post by drpjkurian on 2010-09-11
hi
Hope this may help you
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by rayandrews on 2010-09-11
Thanks,

But it seems that those solutions require either the nVidea (sp?) driver, which I understand only works with their cards, or a dual head card.  Maybe I'm just not going to get this done with three different cards as I have it now.  Still, I hate the idea that Windows can do something that Linux cant.

---

### Post by drpjkurian on 2010-09-11
hi
Well Iam not expert in multiple monitors. But let me share you that there is an option in System->preferences->monitors with an option to detect multiple monitors. Did you try that

---

### Post by formaldehyde_spoon on 2010-09-12
You're using ATI?  Doesn't ATI have something similar to nvidia-settings?  If not you'll have to get your hands dirty in xorg.conf ;)  

I'm no expert by the way, far from it.  My experience here is limited to having two monitors from one nvidia card, and trying to get a third working on a second card.

---

### Post by beefone on 2010-09-12
The Ati control center will allow you to make the necessary changes to get multi monitors setup and configured correctly.

---

