---
title: "(hardy) no sound... various errors"
date: 2008-05-19
forum: Multimedia Software
---

### Post by oskar2000 on 2008-05-19
I have a m-audio 2496 - it's using the envy24 chipset which is officially supported by OSS and ALSA, and has always worked fine for me since I first bought it 6 years ago. It has worked with every Ubuntu version since Warty.. or Hedgehog... it was a hog, that much I know.

If I go to preferences-sound and try the testsounds, I get following errors:
Autodetect:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error.
```

USB Audio (headset)
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

ICE1712 multi:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

ALSA:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

OSS:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error.
```

Pulseaudio:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused
```

Pulseaudio has already worked with my on-board soundcard, but I disabled it because I'm not going to use it if I have a 100$ sound card in there that has been supported by linux since the cretaceous.
I have used my headset with skype, but now that doesn't work either.

Sound has worked with the m-audio, but only with VLC, Totem and m-player. Not with banshee, exail, listen or flash plugins. They only worked with my on-board when set to "Autodetect" - and not with any other option. But lately that stopped working too.

Help would be very much appreciated, as I'm not looking to change distribution over crap like that.

---

### Post by v0idnull on 2008-07-02
Hi I was wondering if you had any solutions? I'm having the same troubles with the same errors on the same card. I've reinstalled ALSA from scratch following the steps lined out at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

My card is installed, but not a single media player works, and testing the sound produces the same error.

---

### Post by evil6 on 2008-08-03
bumb.

Same issues here with my 2496.

---

### Post by ZootHornRollo on 2008-08-05
i got this card working by going back to 7.10 where it worked straight away.. no teaking.

If anyone has a solution to get it to work in 8.04 i'd be glad to hear it.

---

### Post by matt_garman on 2009-03-22
Bump... having the exact same problems as the original poster.

Edit: my problem is with 8.10 (Intrepid Ibex), but still the same as the original poster.

---

### Post by Unixus on 2009-03-24
bump.
Same issue with Jaunty Alpha 5

---

### Post by markbuntu on 2009-03-25
Try this

[http://ubuntuforums.org/showpost.php?p=6449370&postcount=989](http://ubuntuforums.org/showpost.php?p=6449370&postcount=989)

---

