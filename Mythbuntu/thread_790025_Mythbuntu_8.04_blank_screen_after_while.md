---
title: "Mythbuntu 8.04 blank screen after while"
date: 2008-05-11
forum: Mythbuntu
---

### Post by ziissi on 2008-05-11
I've disabled DMPS in xorg.conf and disabled the screensaver as "regular" user and as mythtv user. But still the screen blanks off after while when I'm not using Mythbuntu (watching tv or videos). This would not be issue at all, but my LCD-tv (DVI-HDMI) says no signal even if I press some button from my USB-keyboard. I always have to restart X by pressing ctrl+alt+backspace. Any solutions?

---

### Post by parc on 2008-05-14
> **ziissi said:**
> I've disabled DMPS in xorg.conf and disabled the screensaver as "regular" user and as mythtv user. But still the screen blanks off after while when I'm not using Mythbuntu (watching tv or videos). This would not be issue at all, but my LCD-tv (DVI-HDMI) says no signal even if I press some button from my USB-keyboard. I always have to restart X by pressing ctrl+alt+backspace. Any solutions?

That would be nice to know - because with my 8.04 installation the
music stops playing, when the screensaver becomes active. If I press a key on my keyboard or the ir controller, the screensaver stops and music
is there again ....

---

### Post by cyberfin on 2008-05-18
> **parc said:**
> That would be nice to know - because with my 8.04 installation the
music stops playing, when the screensaver becomes active. If I press a key on my keyboard or the ir controller, the screensaver stops and music
is there again ....

I second this exactly. And I have as well disabled DMPS in xorg.

---

### Post by cyberfin on 2008-05-18
I have found this:

[https://bugs.launchpad.net/mythbuntu/+bug/157158](https://bugs.launchpad.net/mythbuntu/+bug/157158)

In the thread i found this command:

```
chmod a-x /usr/bin/gnome-screensaver
```

It seems to completely disable the screensaver all together. It seems to have worked. Will confirm.

---

