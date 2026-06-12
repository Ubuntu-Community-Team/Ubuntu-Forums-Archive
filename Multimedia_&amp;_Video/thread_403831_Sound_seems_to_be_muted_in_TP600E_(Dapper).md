---
title: "Sound seems to be muted in TP600E (Dapper)"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by tcturner2002 on 2007-04-07
Hi all,
A while back I decided to try to get the sound working on my Thinkpad 600E running Dapper.  Apparently everybody with a Thinkpad has this problem.  Basically, the sound icon on the panel has a little red icon next to it and when you click it, it tells you that you don't have any soundcards.  Programs like Movie Player won't run.  Commands like alsamixer, modprobe, and aplay just give error messages.  I had quite a bit fun trying to fix it, as you can see in [this thread]("http://ubuntuforums.org/showthread.php?t=26754").  There were lots of (very similar) suggestions, but none of them worked until clembone referred me to [this post]("http://ubuntuforums.org/showthread.php?t=282624").

I followed the steps there exactly, and finally I had sound.  But now, suddenly, the sound is not working.  Everything *says* it's working- I can control the volume, play a CD, whatever, and there are no error messages like before, but nothing's coming out of the speakers.  I don't think I did anything to it.  One day it was working fine and the next day ... no sound.  Haven't had any since.

It's like it's muted or something, but it says it's on 100%.  I know the hardware still works because I have plenty of sound in Windows.  And on the computer it's turned up all the way.  This is very weird.  Any ideas what's going on?  Thanks for helping!

---

### Post by tcturner2002 on 2007-04-14
Any ideas?  Thanks!

---

### Post by grumpymole on 2007-04-22
tcturner2002,

A few things to check:

1. Make sure that the hardware sound volume is all the way up.  Use the FN and PgUp.
2. Make sure that the PCM level is at maximum volume.  You will need to right-click on the volume control icon, select properties, choose PCM, set volume to max, then change volume back to Master or whatever the original volume level control was.

HTH

---

### Post by tcturner2002 on 2007-04-25
Yay it works!!  Never would have thought of checking the PCM level.  Thanks so much!

---

