---
title: "MPlayer and Amarok take a long time to start up"
date: 2008-12-05
forum: Multimedia Software
---

### Post by KaiZ51 on 2008-12-05
I think this started happening after doing the instalation of the codecs on this page ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)), some of which I already had, such as the Flash Player, and maybe some others. What should I do? This seems to be codec related since Amarok and MPlayer both use codecs, and this doesn't happen with other programs.

---

### Post by jdoublep on 2008-12-05
Hello. How long is a long time? And the programs eventually do start, correct? You could try an uninstall and reinstall of the software to see if that resolves the issue. 
As an FYI, it takes a while for Amarok to start on my system (a while being 15-20 seconds) simply due to the massive amount of music files I have (and which it needs to parse through for any updates, etc.).

---

### Post by mc4man on 2008-12-05
Amarok will take some time to start up the first time you use it per session, after that it should restart very quickly if you had quit it during a session.

Mplayer (gmplayer) can be delayed if you have the 'Stop XScreensaver' enabled in it's preferences.
To disable, open mplayer from the Applications menu, right click on the video window -> preferences -> misc. You'll see the option there.

---

### Post by Archmage on 2008-12-05
If you have a large cache in Mplayer, than it needs a lot time to load the data.

---

