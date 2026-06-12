---
title: "Flash video no longer has sound"
date: 2011-06-08
forum: Multimedia Software
---

### Post by astraljava on 2011-06-08
Hey guys,

so it seems that the latest flash players for 64-bit system don't provide sound anymore. I had chrome open for several days, so I can't confirm exactly when the issue started. However I noticed that there are two flashplugin-installer updates during the past few days.

After I had to reboot, flash videos no longer produce audio output. At least spotify, rhythmbox and some others do, and when I check indicator-sound-service when a video is playing, it says in the Sound Preferences that no application is playing or recording audio.

So, anyone else having this problem? My system is Natty (11.04), vanilla Ubuntu with Ubuntu Studio packages on top.

---

### Post by lovinglinux on 2011-06-09
You are actually using the 32bit flash with a 64bit wrapper.

Use [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) to install the 64bit version from Adobe Labs. 

It should probably work better, but keep in mind it hasn't been updated for a while. See security recommendations on the [add-on documentation page]("http://www.webgapps.org/add-ons/flash-aid/documentation").

---

### Post by astraljava on 2011-06-09
Well, thanks for the suggestions. However, the solution was actually pretty simple. Just have no idea why it was needed, though. I can't recall having that config around previously.

And the resolution, you ask? Check it out here: 

<http://www.pulseaudio.org/wiki/PerfectSetup#ALSAApplications>

Just needed to tell that pulse driver is the default. Now everything works as previously. Weird, huh?

---

### Post by SpinUp on 2011-07-11
Thanks for the tip -- I had the same issue with flash audio in 32-bit Ubuntu 10.10 and this solved it.

---

