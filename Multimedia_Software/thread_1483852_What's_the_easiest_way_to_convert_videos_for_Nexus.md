---
title: "What's the easiest way to convert videos for Nexus One?"
date: 2010-05-15
forum: Multimedia Software
---

### Post by wersdaluv on 2010-05-15
Been having problems with converting videos for Nexus One.

What quick and easy tool can you suggest?

Handbrake is acting weird here. The options I need are grayed out. Look [[img]http://www.ubuntu-pics.de/thumb/63355/handbrake_003_NGL5BT.png[/img]](http://www.ubuntu-pics.de/bild/63355/handbrake_003_NGL5BT.png)

If you would recommend Handbrake, what could be the fix? Also, does anyone happen to have a preset for Nexus One? It only comes with presets for iPhone and iPod.

Thanks in advance!

---

### Post by JohnAStebbins on 2010-05-15
The latest version of gtk made a non-backwards compatible api change that broke the 0.9.4 release of HandBrake on lucid.  You have to use the snapshot releases.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by wersdaluv on 2010-05-15
> **JohnAStebbins said:**
> The latest version of gtk made a non-backwards compatible api change that broke the 0.9.4 release of HandBrake on lucid.  You have to use the snapshot releases.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)
For some reason, options are still grayed out on the version from the PPA :( Any idea?

---

### Post by JohnAStebbins on 2010-05-16
First, make sure you are actually running the new version.  Look at the about dialog to see what version it is.  Then, tell us what your doing.  The best way to do this is to scan a video source then post HandBrake's activity log.  All logs are archived.  The current log is in ~/.config/ghb/Activity.log.<pid> and all archived encode logs get stored in ~/.config/ghb/EncodeLogs directory.

---

### Post by wersdaluv on 2010-05-17
> **JohnAStebbins said:**
> First, make sure you are actually running the new version.  Look at the about dialog to see what version it is.  Then, tell us what your doing.  The best way to do this is to scan a video source then post HandBrake's activity log.  All logs are archived.  The current log is in ~/.config/ghb/Activity.log.<pid> and all archived encode logs get stored in ~/.config/ghb/EncodeLogs directory.
I got HandBrake svn3295 (i686). svn3295ppa1~lucid1 to be exact

---

