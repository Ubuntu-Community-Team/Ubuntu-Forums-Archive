---
title: "In Jaunty how do i make VLC integrate into one window while watching a dvd??"
date: 2009-07-19
forum: Multimedia Software
---

### Post by JohneG on 2009-07-19
Since installing Jaunty i have loved it but what annoys me is VLC players interface remaining in two windows whilst watching a DVD. I have tried -

Preferences > Interface type > Integrate video in interface

Thought that would have done it but it doesn't. Anyone know how to do this??

---

### Post by mc4man on 2009-07-19
There are several options ranging from rebuilding 0.9.9a or building 1.0.0 to adding a ppa and installing 1.0 (there may still be a ppa  or 2 offering 0.9.9a for jaunty, for the most part 1.0 is superior

ppa's offering 1.0 for jaunty

Kow's
[https://edge.launchpad.net/~kow/+archive/ppa](https://edge.launchpad.net/~kow/+archive/ppa)

C.Korns
[https://edge.launchpad.net/~c-korn/+archive/vlc](https://edge.launchpad.net/~c-korn/+archive/vlc)

Both have pretty much the same build, Kow's will update ocassionally as 1.0.has minor bug fixes heading towards a 1.0.1 release.
Korn's will probably stay the same till 1.0.1

(1.0.1 is not to be confused with 1.1 which is only avaiable to build (considered 'unstable'


If you don't now how to use a ppa, ask first.

when upgrading vlc thru a ppa to a new version I'd suggest removing vlc first, at least the core packages, vlc, vlc-nox, libvlc2, vlc-data, and libvlccore0 (libvlccore0 is the main culprit for issues if not removed first. (search vlc in synaptic

After installing the new vlc I'd also suggest to start vlc for the first time as such (not 100% necessary, just what I'd do 
```
vlc --reset-config --reset-plugins-cache
```


Edit:
to answer your orig ?, the 'embedded' video in 0.9.x was/is considered broken by videolan and was disabled in the source.
On most debian/ubuntu installs it wasn't much of an issue, the source was edited to re-institute it in Intrepid. (only 1 line needs to be changed

Jaunty packagers decided not to patch the source, that's why it's separate  in jaunty.
1.0.0 fixed the problem, so it was re-enabled in the source, ect

---

### Post by bboston7 on 2009-07-19
Upgrading to 1.0 will fix that.

I would recommend adding the c-korn ppa to ensure that you get further updates as well

---

### Post by DeanoCYM on 2009-07-21
Thanks mc4man, very helpful. I always wondered why this happened. One minor annoyance gone :)

iechyd dda! Cheers, Rhys

---

### Post by michaeloleary on 2009-08-20
Sorry to Hijack this thread, but can anyone point me to a good tutorial for updating from a ppa? I keep running into errors and I'm not finding anything useful from googling. :confused:

Thanks
Mike

Update:

It looks like I eventually found out how to do it, if anyone else comes across the problem, please find a solution at the link below, I'm by no means a linux expert and found this very easy to deploy (turns out I was just over complicating things =/ ) please find the solution at the following url:

[http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

---

