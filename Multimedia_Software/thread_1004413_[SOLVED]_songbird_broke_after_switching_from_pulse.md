---
title: "[SOLVED] songbird broke after switching from pulseaudio to alsa"
date: 2008-12-07
forum: Multimedia Software
---

### Post by loganp82 on 2008-12-07
i disabled pulseaudio using this link [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965) and now i open up songbird and when i hit play it freezes. this is rather unfortunate because it quickly became my favorite music player and now is broke :( exaile,totem,etc... all work fine though. weird huh? any advice?

---

### Post by sleepyjon on 2008-12-07
What version of songbird are you using?

---

### Post by Catalyst2Death on 2008-12-07
Have you tried "reinstalling" songbird?  I usually have to do this after they release a new version because it will crash randomly/not work when the update...

Download the songbird tarball here:

[http://download.songbirdnest.com/installer/linux/i686/Songbird_1.0.0-860_linux-i686.tar.gz](http://download.songbirdnest.com/installer/linux/i686/Songbird_1.0.0-860_linux-i686.tar.gz)

then move it to where ever you have the old one.  Then remove the old one (or rename the old folder) extract the above with:

```
$ tar -xvf Songbird_1.0.0-860_linux-i686.tar.gz
```

and then start songbird:

```
$ Songbird/songbird
```

If that doesn't work, you can regenerate your profile (back it up first!):

```
$ rm -rf ~/.songbird2
```

Restart Songbird again.  Hopefully Songbird will wake up fresh and realize which audio server to use, rather than having the one it found earlier suddenly missing.

I disabled pulse-audio on my laptop, and I don't remember if Songbird broke, but I've reinstalled it a couple times (for upgrades) since then. Using the above method and Songbird works there.

---

### Post by loganp82 on 2008-12-07
its the newest version (1.0) i did reinstall it with add/remove programs i believe but that didnt help anything :(   it still becomes unresponsive as soon as i hit play. no luck on trying idea catalyst2death. but i appreciate your help anyways. i'm just going to revert what i did from that link and i will post my results when im done. ok guys i did this guide [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and it fixed everything. songbird works again :)

---

