---
title: "HOWTO: shift tempo in mplayer without changing pitch"
date: 2009-07-30
forum: Multimedia Software
---

### Post by Ndlovu on 2009-07-30
I took some time to figure this out for myself, so I thought I'd post a quick note for the benefit of others and so I can remember in the future.

This post explains how to use mplayer to play an audio file (though it could also be a video) at a slower or faster speed without changing the pitch of the sound. Note that if pitch is not important, speed can be controlled with the [ and ] keys during playback.

I am running Hardy (8.04), so your mileage may vary on other systems. Newer versions of mplayer achieve the same results with the "scaletempo" filter, so Google that first if you are running a current system.

First, you'll need to install tap-plugins:
```
$ sudo apt-get install tap-plugins
```

Then, you will use a command of the following form to play the file:
```
$ mplayer -speed x -af ladspa=/usr/lib/ladspa/tap_pitch.so:tap_pitch:0:y:-90:0 file.mp3

```

Here, x is the rate at which the file should play, with 1 being normal speed. So if you want to play at 80% of normal speed, x = 0.8, and if you want to play it at 150% of normal speed, x = 1.5.

On the other side, y is the modified pitch, as a percentage change, with 0 being normal. So if you want to increase the pitch by 50%, y = 50, and if you want to decrease the pitch by 50%, then y = -50.

The challenge we have is that we want to keep the pitch the same, so we need to work out the relationship between x and y so that if we decrease the speed (tempo), we increase the pitch to compensate. This relationship is given by the following equation:
> y = (100-100x)/x.

So if we want to play the file at 80% of normal speed, x = 0.8 and y = (100-100*0.8)/(0.8) = 25, and the command we would use to play the file becomes:
```
$ mplayer -speed 0.8 -af ladspa=/usr/lib/ladspa/tap_pitch.so:tap_pitch:0:25:-90:0 file.mp3

```

If we want to play the file at 200% of normal speed, x = 2 and y = (100-100*2)/2 = -50, and the command we would use to play the file becomes:
```
$ mplayer -speed 2 -af ladspa=/usr/lib/ladspa/tap_pitch.so:tap_pitch:0:-50:-90:0 file.mp3

```

tap-pitch only works with a pitch shift range of -50 to 100, which corresponds to speeds of 0.5x to 2.0x, although it is possible to chain the filters if you want to increase that range (so run tap-pitch on tap-pitch), but that's outside of my scope.

If you want to dig deeper, please check the following resources.

Relevant resources:
[LIST]
[*][http://markplusplus.wordpress.com/2006/10/01/pitch-correct-play-speed-with-mplayer/]("http://markplusplus.wordpress.com/2006/10/01/pitch-correct-play-speed-with-mplayer/")
[*][http://tap-plugins.sourceforge.net/ladspa/pitch.html]("http://tap-plugins.sourceforge.net/ladspa/pitch.html")
[/LIST]

---

### Post by Ninefold on 2009-08-17
Thank you very much for this!

I am using Jaunty and the scaletempo.deb from sourceforge had a dependency error. So, I did as you had instructed above and installed the tap-plugings and it worked.

I am thrilled. I really needed this feature.

---

### Post by johnnyb0y on 2009-11-07
A beautiful post.

I managed to resurrect an old import CD from the USA which was recorded at some weird too-fast setting.

Using your information in the post helped me enormously, so much so I can listen to it just like I remembered!

Many many thanks.

John G

---

### Post by 80aless on 2010-04-20
great! there are some distorsion at 0.8, but I guess it is unavoidable
Can I output the result to a sound file? 
If I half the speed, I should do 

PS: the composer Stockhausen, to compose electronic music had to record a sound, cut the tape and play it at double speed to double the pitch

---

### Post by Bumfun MC on 2010-04-24
0.5 <= SPEED <= 2
# apt-get install tap-plugins

```
SPEED=0.5 && mplayer -speed $SPEED -af ladspa=/usr/lib/ladspa/tap_pitch.so:tap_pitch:0:`echo "(100-100*$SPEED)/$SPEED" | bc`:-90:0 FILE.OGG
```

---

### Post by andrew.46 on 2010-04-24
Of course more recent copies of MPlayer now feature the scaletempo audio filter which is yet another way to achieve this goal...

Andrew

---

### Post by haomself on 2011-03-16
mplayer -af scaletempo -speed 0.5 test.ogg
using kubuntu 10.10 
mplayer  1.0rc4-4.4.5 (C)

---

