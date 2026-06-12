---
title: "so my sound quit working after I installed kubuntu-desktop"
date: 2009-08-23
forum: Multimedia Software
---

### Post by v1nsai on 2009-08-23
I'm running gnome ubuntu 9.04 and saw a screenshot of the latest KDE and decided to try it out (damn it got sleek since the last time I used it).  Anyway, I noticed I wasn't able to listen to any of my music in amarok (it never attempted to play anything, and even crashed after I tried playing several different things), so I shrugged it off and continued playing around, then logged and switched back to gnome.  My sound hasn't worked since.  However, instead of crashing like amarok did in KDE it sits and plays but no sound comes out.

It was definitely working before I added kde, I was even listening to music in rhythmbox as the packages downloaded.

I have tried using both headphones and the main speakers, and (tried) listening to rhythmbox and music through a flash player in firefox.  No dice.  Definitely a software problem.  Everything is turned on and up in the sound mixer, but beyond that I don't know anything else to check.  Confused, help appreciated :)

---

### Post by markbuntu on 2009-08-23
You can read this about what KDE4 does when you install it over gnome.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

This is for getting pulseaudio set up correctly in gnome

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Between those you should be able to get your sound straightened out.

---

### Post by v1nsai on 2009-08-23
cool, thanks a lot I'm gonna start playing with it now.  Kubuntu-desktop was a ~500MB install when I did put it on, yet when I tried removing it after my sound problems began, it was only a matter of kilobytes.  How can I find and remove the other packages it put on, my hard drive is pretty cramped from that install now, I keep /home on a separate partition.

---

### Post by markbuntu on 2009-08-24
There is a zillion kubuntu packages installed, They all start with ksomething. You can use synaptic and search k and remove all the obvious kubuntu stuff like

kubuntu-docs kubuntu-artwork kubuntu-default-settings etc etc and you can remove phonon while you are at it. Just keep an eye out for what other packages it want to remove or you could end up losing a lot of stuff you really need.

---

### Post by v1nsai on 2009-08-24
I said f*** it and reinstalled ubuntu.  I have /home mounted on another partition, so it took me about an hour to reinstall and get everything back like it was.  Didn't fix the problem with the sound though, but I was able to use your instructions for using pulseaudio to get that running, I even got my volume keys on my keyboard to work.  Thanks a bunch man!

---

