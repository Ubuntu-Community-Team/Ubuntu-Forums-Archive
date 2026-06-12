---
title: "no sound in amarok"
date: 2010-02-15
forum: Multimedia Software
---

### Post by steve.a on 2010-02-15
hi i just upgraded to karmic koala, i had amarok on jaunty it worked for a while but then suddenly it stopped playing music files - or at least it was playing them but no sound was coming out.
i still have the same problem, i checked my sound card driver - works, the mp3 codecs - installed. in fact sound works with rythmbox and audacious everywhere in the system except with amarok.
i get no error messages, nothing, it just shows the file as playing but no sound. i edited the playback perferences switching the output device between pulseaudio and my HDA intel sound card but still nothing. i have to mention that both seem to emit a sound when i test them.
i really don't know how to fix this please help.
thanks

---

### Post by ajgreeny on 2010-02-15
I don't use amarok, but I did have some sound problems with karmic which were solved by installing padevchooser.  I simply started it from the sound and video menu, and the problems were gone; I didn't actually do anything in padevchooser, just started it.

Give that a try, there's nothing lost if it is a failure, but potentially sound to gain if it does work.

Pulseaudio still seems to be not well configured in ubuntu at the moment; let's hope it is better in lucid.

---

### Post by steve.a on 2010-02-15
> **ajgreeny said:**
> I don't use amarok, but I did have some sound problems with karmic which were solved by installing padevchooser.  I simply started it from the sound and video menu, and the problems were gone; I didn't actually do anything in padevchooser, just started it.

Give that a try, there's nothing lost if it is a failure, but potentially sound to gain if it does work.

Pulseaudio still seems to be not well configured in ubuntu at the moment; let's hope it is better in lucid.

i had sound problems too when i upgraded to karmic but i solved them while the problem i am facing with amarok was already there before the upgrade. as i said sound works in rythmbox and audacious but i like the interface of amarok better and i just thought it's time to deal with it.

---

### Post by ajgreeny on 2010-02-16
It is worth having a look at **banshee** as well as the other sound apps you already know about.  I have used rhythmbox until a few weeks ago when someone on a thread suggested banshee.  It is great!  I was having big problems with rhythmbox not finding any cover art from the web, but banshee gets it all straight away, and for my personal tastes, has a better interface.

---

### Post by ubunyou on 2010-03-30
I had the same problem and fixed it by installing libxine1-ffmpeg

```

sudo apt-get install libxine1-ffmpeg

```

Details:

I just upgraded to Ubuntu 9.10 and am having the same issue.
Sound works using on an mp3 using the hover preview feature as well as the default movie player. The same mp3 does not play using amarok.

When I enqueue multiple mp3 in a playlist and hit play amarok will quickly cycle through the entire list and fail to play each one.

---

### Post by lidex on 2010-03-31
You may need this:
```
sudo apt-get install phonon-backend-xine
```

---

