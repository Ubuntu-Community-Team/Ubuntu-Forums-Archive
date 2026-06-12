---
title: "Stupid sound issues"
date: 2008-11-10
forum: Multimedia Software
---

### Post by Ionamay on 2008-11-10
This doesn't seem to be because I upgraded, because it worked for a while after I upgraded to Intrepid Ibex. My sound suddenly wouldn't work and keeps making a crackly noise. I've used guides from here to fix it, including these:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)
When I removed pulseaudio, the crackling stopped and there was just no sound at all. Then I removed and reinstalled the ALSA drivers, then tested it out under sound prefs, and it seemed to work, but when I started to try playing music, it started crackling again, no sound, and the sound prefs test didn't work either.

---

### Post by Ionamay on 2008-11-10
Okay this is odd, sound works provided I uninstall my preferred network manager, wicd, so I either have:
wicd- no sound
crappy default network manager that gives me problems- sound

---

### Post by psyke83 on 2008-11-10
> **Ionamay said:**
> Okay this is odd, sound works provided I uninstall my preferred network manager, wicd, so I either have:
wicd- no sound
crappy default network manager that gives me problems- sound

No, I think this change is incidental. The bug you're experiencing is a result of a PCM or Master mixer being set to 0% (which inexplicably causes faint crackling, when the speaker should be silent). Check your mixer levels via:

```
$ alsamixer -Dhw
```

---

### Post by Ionamay on 2008-11-10
Thanks a lot, but the reason I thought deleting wicd caused the problem was that when i was uninstalling the ALSA drivers, it told me that it was getting rid of the wicd package too. When it was finished, the sound worked, but then I reinstalled wicd and it didn't work anymore. Then I decided to uninstall wicd again, and it worked again.

Anyway, the PCM mixer was set to 0% and I changed it, and when I can be bothered I'll put wicd back on :p
Thank you

---

