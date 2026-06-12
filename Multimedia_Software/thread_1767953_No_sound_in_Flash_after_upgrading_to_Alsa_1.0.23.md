---
title: "No sound in Flash after upgrading to Alsa 1.0.23"
date: 2011-05-26
forum: Multimedia Software
---

### Post by sag0th on 2011-05-26
Hi!

I had an issue with my mic so I decided to upgrade alsa to 1.0.23 to see if this will fix the problem. I used alsa driver/utils/lib 1.0.23 from alsa-project.org
So it fixed it...but now I don't have sound in Flash (youtybe videos, etc.). System sound works perfectly (even Skype is working :) )

Any idea why this is happening and how to fix it??? :confused:

I'm using Ubuntu 9.10 64bit and Google Chrome browser.
flash ->  flashplugin-nonfree

---

### Post by sag0th on 2011-05-26
nobody?... :???:

Tried reinstalling flashplugin-nonfree -> same result

Maybe remove the damned pulseaudio?

---

### Post by beew on 2011-05-26
Ubuntu 9.10 has passed its end of life for almost 2 months so I am not surprised if things don't work any more.

Should install a newer Ubuntu release.

---

### Post by sag0th on 2011-05-27
I'm really surprised by this answer.

"no longer being supported" != "not working any more"

Besides... Alsa release dates:```

2011-01-31	alsa 1.0.24 release | Changes v1.0.23 v1.0.24
[color=red]2010-04-16[/color]	alsa 1.0.23 release | Changes v1.0.22 v1.0.23
```

My experience is that 9.10 is _much_ more reliable than 10 and 11 (have them both on different PCs) but that's another story.

---

### Post by sag0th on 2011-05-27
Fixed by [[color=red]Temüjin[/color]](http://ubuntuforums.org/member.php?u=327594)! Respect!

The solution for me was in: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

