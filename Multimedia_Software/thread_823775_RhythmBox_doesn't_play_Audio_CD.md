---
title: "RhythmBox doesn't play Audio CD"
date: 2008-06-09
forum: Multimedia Software
---

### Post by KingTermite on 2008-06-09
I got a new CD yesterday. It is created by a local radio station (only mention because I don't know of the production quality). I put it in to listen to last night and try to listen via Rhythmbox.

It comes up and shows the correct number of tracks, but it doesn't start playing. Clicking the "play" button does nothing. I don't get any errors it just won't start playing.

I'm not at home at the moment to try anything, but thought I'd see if anybody had any ideas. I haven't tried any other audio CDs either, but can try that when I get home.

BTW....brought the same CD to work today and it plays fine (in WMP on XP), so I don't "think" its the CD.

---

### Post by pytheas22 on 2008-06-09
In order to narrow down the problem, as you mention, you should try other CDs.  Also try playing the CD using a different program, like Totem (aka "Movie Player").  That way you'll know whether the problem is that particular CD, Rhythmbox or some problem with your computer reading CDs.  Post the results and we can figure out where to go next.

---

### Post by KingTermite on 2008-06-09
OK. I have tried another regular audio CD and still have the exact same issue.

I tried to open in Totem and it gives an error about "stream has no data", but I think its expecting "wav" files on the audio CD.

I just tried to click "open" and navigate to audio CD where it showed wav files (which really aren't there) and selected one of them.

---

### Post by KingTermite on 2008-06-09
I just went to mounted audio CD from the "places" menu and it brought it up in Sound Juicer. I selected "play" from its menu. It spun the disc up, but it still didn't play.

---

### Post by pytheas22 on 2008-06-09
I'm not sure if it's the problem (I doubt it is), but it couldn't hurt to make sure you have all of the decoders and things installed, just in case a missing multimedia codec is causing the CD not to be read (it doesn't make a huge amount of sense, but just in case...):

```
sudo apt-get install ubuntu-restricted-extras
```

You might also get useful information if you try running the applications from a terminal (just type 'totem' for Totem and 'rhythmbox' for Rhythmbox) and see if any information gets dumped to the terminal regarding a problem with the CD.

Also, are you able to play other audio files from the hard disk?

---

### Post by KingTermite on 2008-06-10
> **pytheas22 said:**
> I'm not sure if it's the problem (I doubt it is), but it couldn't hurt to make sure you have all of the decoders and things installed, just in case a missing multimedia codec is causing the CD not to be read (it doesn't make a huge amount of sense, but just in case...):

```
sudo apt-get install ubuntu-restricted-extras
```

You might also get useful information if you try running the applications from a terminal (just type 'totem' for Totem and 'rhythmbox' for Rhythmbox) and see if any information gets dumped to the terminal regarding a problem with the CD.

Also, are you able to play other audio files from the hard disk?

You rock, pytheas22!!! That's apparently exactly what the problem was.

I'd never have guessed that a codec to run a regular audio disc wouldn't be installed by default.

---

### Post by pytheas22 on 2008-06-10
Nice, glad it works.  I didn't think a codec made much sense...I don't know too much about CDs but I thought they just always contained .wav files, which I thought could be played by Ubuntu out of the box.  But I guess we both learned something...

---

