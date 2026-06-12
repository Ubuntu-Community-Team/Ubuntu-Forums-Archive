---
title: "Amarok 2.1 collection issues"
date: 2009-06-07
forum: Multimedia Software
---

### Post by meho_r on 2009-06-07
Hi. I installed KDE 4.2.4 and Amarok 2.1 and I notice (what a news!) that Amarok is practically unusable. The thing is that managing collection is completely messed up.

1. I put 3 folders in my Music folder, every of them containing 3 or 4 full albums.

2. I set Amarok to monitor Music folder and detect any change that happens

3. Amarok failed to display all Artists (and, of course, their albums) -- in fact, once it displays all of them, after restart some of them are missing, sometimes only couple of songs are missing

4. Amarok changes id3tag and replace artist field with that of other artist. It even moved songs from one folder into another!

Those are only couple of issues I have with Amarok. At this time, it is de facto the worst audio player I've ever seen :( And I'm sad because of that. Does anyone knows is there a way to remedy those problems?

---

### Post by Jamesss on 2009-06-08
I'm not using KDE, but I uninstalled Amarok 2.0 (because it was useless) and reinstalled 1.4 after upgrading to Jaunty. See here:

[https://edge.launchpad.net/~bogdanb/+archive/ppa](https://edge.launchpad.net/~bogdanb/+archive/ppa)

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1084971&highlight=bogdan+jaunty+amarok&page=8](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1084971&highlight=bogdan+jaunty+amarok&page=8)

---

### Post by meho_r on 2009-06-08
Thanks, but I actually like v2.1 and try to get it work as expected. Eventually, I purged it completely, deleted all settings and installed again. For now, it's working alright. I hope it will last.

On #amarok channel I learned of other cases of messing things up regarding collection and its manipulation with files. I noticed that Amarok changed/erased id3 tags only internally, while in other players all tags are intact. I suspected that it has something to do with mysql from (k)ubuntu repo (backport), but I'm not sure, especially now when it works.

EDIT: And here we go again. Simply put: Amarok (or is it mysql?) sucks. It messed my collection again, changed artists and again doesn't display all songs. Sigh. I give up. Will check it out when it reach v2.2. Maybe.

---

