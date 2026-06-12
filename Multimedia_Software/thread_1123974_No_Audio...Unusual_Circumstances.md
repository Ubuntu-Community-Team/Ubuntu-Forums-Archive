---
title: "No Audio...Unusual Circumstances"
date: 2009-04-12
forum: Multimedia Software
---

### Post by NemX162 on 2009-04-12
Hello.  I've been using Ubuntu 8.10 for a few months now and the audio always worked, I never had to change anything.  However, earlier today I was messing with Timidity, trying to get Guitar Pro 5 to work.

A few hours later I realized my sound was not working.  I removed timidity and put it back, trying to fix it and it didn't work.  I don't see why messing with Timidity would cause this problem.

In my sad attempts to fix it, I removed ALSA and reinstalled it, but it did not help.

I think what I need to do is just recover all the original audio files and settings that Ubuntu came with, but I don't know how. Any help?

My audio controller is: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

---

### Post by soltanis on 2009-04-13
Running alsaconf might alleviate your situation but recently Debian and Ubuntu have decided to deliberately omit the utility from the alsa-utils package.

Oh yeah, sorry, they removed it because "obviously if you need it there is a bug."

So clearly the free software geniuses have determined their software breaks and so the obvious solution was to remove the only tool that solved it #-o.

I'm trying to find where you can get the script online.

EDIT.
[http://dir.filewatcher.com/d/Debian/all/sound/alsaconf_0.4.3b-4_all.deb.13902.html](http://dir.filewatcher.com/d/Debian/all/sound/alsaconf_0.4.3b-4_all.deb.13902.html)

That looks like a debian package and probably an old one...I wouldn't install it just yet if I were you. Wait to see if anyone has a more specific solution for you.

---

### Post by NemX162 on 2009-04-13
If nobody has any better suggestions, I suppose I'll back up my important stuff and reinstall ubuntu?

---

