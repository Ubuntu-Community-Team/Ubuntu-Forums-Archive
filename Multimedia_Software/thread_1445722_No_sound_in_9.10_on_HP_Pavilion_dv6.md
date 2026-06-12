---
title: "No sound in 9.10 on HP Pavilion dv6"
date: 2010-04-03
forum: Multimedia Software
---

### Post by adamcrume on 2010-04-03
I have an HP Pavilion laptop running Kubuntu 9.10.  The sound worked at one point, but somewhere along the line it broke.  When I test the sound in the system settings panel, I get nothing.  No errors, no sound.  I checked KMix and alsamixer.  All channels are unmuted and turned up. I've also tried the headphone jack, and there's no sound there, either.  It works fine if I boot into Windows.  Here's the output from alsa-info.sh: [http://www.alsa-project.org/db/?f=cfcc481511b6ecf990c0498fb4b4dd95b03f0ee3](http://www.alsa-project.org/db/?f=cfcc481511b6ecf990c0498fb4b4dd95b03f0ee3)

I would also like Amarok to work, too.  I had problems in the past getting it to output sound.

Any help would be appreciated.

---

### Post by lidex on 2010-04-03
Try updating your alsa to latest version. Click the alsa upgrade script link in my sig. I'm using gnome on my Dv7, but it required that update.

---

### Post by adamcrume on 2010-04-03
The upgrade script fails during the install phase with the error "configure: error: panelw library not found".  /usr/lib/libpanelw.so.5.7 exists.  I tried following this workaround, recompiling and reinstalling, but it still fails with the same error: [http://trac.64studio.com/64studio/ticket/511](http://trac.64studio.com/64studio/ticket/511)

---

### Post by lidex on 2010-04-03
Do you have a symlink in that same directory named "libpanelw.so.5" that points to "libpanelw.so.5.7"? If not, create one and try again.

---

### Post by adamcrume on 2010-04-03
I do, and libpanelw.so.5.7 exists and is readable.

---

### Post by lidex on 2010-04-03
I have not seen that before. Try enabling unsupported (backports) repo in "Software Sources" and installing the alsa modules:
```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

---

### Post by adamcrume on 2010-04-03
The sound works now (including Amarok) after updating ALSA from the backports!  Thanks!

---

### Post by lidex on 2010-04-03
You're welcome. ;)

---

