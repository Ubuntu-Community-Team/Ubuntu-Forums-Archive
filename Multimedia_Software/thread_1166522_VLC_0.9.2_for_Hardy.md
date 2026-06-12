---
title: "VLC 0.9.2 for Hardy?"
date: 2009-05-21
forum: Multimedia Software
---

### Post by noblerabbit on 2009-05-21
Is there any way of getting the new version of VLC for Hardy?

I have it in windows, and i had it on jaunty, but for hardy i cant get it, stuck with the really old and basic one, which wont let me seek smoothly or anything.

ive looked around but the c-korn distribution seems to be dangerous, and also not supported by amd64.

Anyone got it working on 64bit Hardy?

---

### Post by mc4man on 2009-05-21
I don't think you'll find too many vlc 0.9.x versions built for hardy, at least in the launchpad ppa's

I use hardy (32 bit) and just build my own

> ive looked around but the c-korn distribution seems to be dangerous, and also not supported by amd64.


I can't see what's " dangerous"  with his builds, which are using the best 0.9.x source (0.9.9a) and there certainly is  amd_64 [available]("https://edge.launchpad.net/~c-korn/+archive/vlc").

There is an old (sept) build of 0.9.3 [here]("https://edge.launchpad.net/~intuitivenipple/+archive/ppa/+index?start=50&batch=50")

---

### Post by noblerabbit on 2009-05-22
i only read it was "dangerous" because no public key was available (?)


i added these lines to my sources.list
```
[FONT=monospace]
[/FONT]deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) hardy main[FONT=Verdana]

```

removed vlc and then reinstalled with apt-get, but still its the same version. what am i doing wrong?
[/FONT]

---

### Post by noblerabbit on 2009-05-23
i left those repo entries in sources.list and today the new vlc was installed with my updates.

i wonder wth it didnt work when i just did it from command line.. ?

anywho, i have the new one now, so problem solved.

---

### Post by mc4man on 2009-05-23
> i wonder wth it didnt work when i just did it from command line.. ?

If you had entred the repo directly into sources.list (vs the gui in software sources, third pary) then you would have needed to run 
sudo apt-get update first to update the package list.

As far as the key, on all ppa pages there is a link that shows how to enter the key or there is a thread around here that has a script that'll do it for you

(for the couple of ppa's I have I've never set the key

---

