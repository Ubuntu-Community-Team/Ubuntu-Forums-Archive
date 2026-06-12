---
title: "Rhythmbox plays two songs at once"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by TWO on 2007-12-27
On a few occasions now, whilst I have clicked on a song in Rhythmbox after listening for a little while, I hear another song playing in the background. When I then go to pause the song that is currently playing, on those occasions another song is still playing in the background until I close the program down entirely.

Has anyone else experienced this problem and if so, could this be a bug?

Thanks in advance

TWO

---

### Post by supernovus on 2008-05-15
It's a bug. I have the same issue. I can resolve it by double clicking on a song, which makes that the only song which plays.

It seems to do this when in shuffle mode, and it's a new bug that has only occurred since I upgraded to a processor which Hyperthreading.

And it doesn't happen every time, which makes it even more frustrating to try to track it down.

Just my info to add to the mix.

---

### Post by 5of0 on 2008-06-06
I've experienced this too...this seems like kind of a big issue, since Rhythmbox's whole purpose is playing music?

---

### Post by sean22190 on 2008-06-25
Yup, I have this too. Very annoying!

---

### Post by TWO on 2008-06-27
Wow, this problem is still occurring? 

I only use Rhythmbox occasionally now under Hardy. I haven't experienced anything yet. Is everyone else also using Hardy Heron?

---

### Post by sean22190 on 2008-06-27
Yup, I'm getting it under Hardy too. Time to change music players I guess.

---

### Post by forger on 2008-06-27
Maybe it's a glitch in the settings?
You could try clearing up rhythmbox settings, it might work...

[B]Use at your own risk!! This can damage your rhythmbox settings, keep backups!!
[/B]
**Close rhythmbox** then backup:
```

mv $HOME/.gnome2/rhythmbox $HOME/rhythmbox-backup
gconftool --dump /apps/rhythmbox > $HOME/rhythmbox-gconf.backup

```
then clear the values and reinstall rhythmbox
```
gconf --recursive-unset /apps/rhythmbox
sudo apt-get install --reinstall rhythmbox
```

(A restart of gnome would be recommended)

Now try and run rhythmbox again, and test it out.
In case something goes wrong, you can always revert back (always close rhythmbox before doing any changes):
```
mv $HOME/rhythmbox-backup $HOME/.gnome2/rhythmbox
gconf --load $HOME/rhythmbox-gconf.backup
```

---

### Post by forger on 2008-06-28
The other thing that it could be, might be a long crossfade?
Try disable the crossfade effect in menu edit > preferences > playback

---

### Post by TWO on 2008-06-28
> **forger said:**
> The other thing that it could be, might be a long crossfade?
Try disable the crossfade effect in menu edit > preferences > playback

I've been using Rhythmbox a little bit more at the moment. I have a 4 second crossfade set but I still haven't experienced the problem under Hardy.

If it is still causing problems, I too would suggest trying another music player; maybe Banshee, Exaile, or my favourites Amarok or Songbird.

(Songbird is under development and is at version 0.61 at the moment but it's looking good. Shaping up to be a winamp/iTunes mix.)

---

