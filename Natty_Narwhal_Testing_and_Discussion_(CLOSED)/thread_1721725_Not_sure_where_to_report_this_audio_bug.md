---
title: "Not sure where to report this audio bug"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ninjaaron on 2011-04-04
A few days ago, my headphone jack stopped working with natty. When I plug something in, the sound continues to come out of the speaker. I can't see the line-out in my "sound" dialog or in alsamixer.

I realize this isn't the place to report it, but I'm not sure exactly where it ought to be reported, cause I don't know which software is causing the problem.

---

### Post by ninjaaron on 2011-04-05
still not sure.

---

### Post by cariboo on 2011-04-05
Have you tried Sound Preferences->Output->Connector, and set it to headphones? There is a long standing plug sensing bug, that causes it to not sense that something has been plugged into the headphone jack.

---

### Post by ninjaaron on 2011-04-06
In the "sound" dialog, under the "output" tab, and inside the box with the title "Choose a device..." I only have one entry: "Internal Audio Analog Stereo."

I don't see any other device to choose. This wasn't how it was before. One of the updates apparently killed it.

---

### Post by ninjaaron on 2011-04-08
So... yeah... about that...

I'm not looking for the solution to this bug, I just want to know where I ought to report it *so that it will eventually get fixed.*

---

### Post by cariboo on 2011-04-08
As always, you report bugs on [https://bugs.launchpad.net](https://bugs.launchpad.net). the easiest way is to press Alt-F2 and type:

```
 ubuntu-bug <package_name>
```

where <package_name> = the package you are reporting a bug about. You need a launchpad account to report bugs.

---

### Post by ninjaaron on 2011-04-09
> **cariboo907 said:**
> As always, you report bugs on [https://bugs.launchpad.net](https://bugs.launchpad.net). the easiest way is to press Alt-F2 and type:

```
 ubuntu-bug <package_name>
```

where <package_name> = the package you are reporting a bug about. You need a launchpad account to report bugs.

This is the the issue. I don't know which package is causing the problem. My headphone jack is just invisible to the OS, and I haven't a clue why.

I think, for the time being, I'm going to wipe the drive and install a daily to see if it was a setting that got messed up, not a driver or software issue perse.

---

### Post by jrothwell97 on 2011-04-10
I can confirm that I'm also getting this issue on a ThinkPad X100e (Intel HDA sound) on a fully up-to-date install of Natty.

The obvious place to look for bugs would be in pulseaudio or alsa, but this is an area I'm unfamiliar with.

---

### Post by cariboo on 2011-04-10
I'd suggest filing the bug against alsa-base.

---

### Post by ninjaaron on 2011-04-21
Today's update fixed it.:)

---

### Post by lidex on 2011-04-21
FFR: For lucid and later:
```
ubuntu-bug audio
```
For karmic:
```
ubuntu-bug -p alsa-base
```
More info reference the link in my sig.

---

