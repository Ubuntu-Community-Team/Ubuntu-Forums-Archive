---
title: "Any Idea How to Stop Banshee Using 300% CPU... and Finally Load??"
date: 2011-11-21
forum: Multimedia Software
---

### Post by OzzyFrank on 2011-11-21
Now, I'm sure many of you have your criticisms about Banshee, specifically its horrid misuse of system resources. When Banshee was installed, I decided to keep it, though I use Rhythmbox (because you don't need a supercomputer for the latter).

But after upgrading to 11.10, Banshee just won't load at all. At first I just thought it was crashing, as the outline and title bar is there, but the rest is white.

However, I now realise each time it has been trying to load, hence the heightened disk activity, so this time decided to let it try to do its thing, in case it was redrawing playlists or something else it needed to do after the upgrade. But after watching it churn away for half an hour, with CPU use going over a whopping 300%, all I am getting for my patience is furious disk activity, with CPU use still around the 300% mark. The only thing I can see happening is it wearing a hole in my hard drive, hehe, or melting my CPU. I simply cannot see what it could be doing, since it obviously isn't getting any nearer to successfully loading.

Any suggestions, besides remove Banshee?

---

### Post by OzzyFrank on 2011-11-21
Update: the hard drive activity did eventually die down to nothing (and perhaps could have been other processes) but the CPU usage continued to go over 300% with no sign of ceasing.

I decided to kill the process, which I could see was **banshee --redirect-log --play-enqueued %U**, so then decided to edit the launcher so the command was simply **banshee**.

Banshee now loads, and even while updating the library was only using about 12% CPU (actually, still updating it now, and is still a low 20%). Not sure if I should mark this as solved, though.

---

### Post by beew on 2011-11-21
I installed banshee in 11.04 with the ppa . It seems to start much faster than the version bundled with Ubuntu and it never crashed on me (like the default version)

[https://launchpad.net/~banshee-team/+archive/banshee-daily?field.series_filter=](https://launchpad.net/~banshee-team/+archive/banshee-daily?field.series_filter=)

---

