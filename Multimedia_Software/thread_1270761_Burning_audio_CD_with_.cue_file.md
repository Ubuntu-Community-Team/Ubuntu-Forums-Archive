---
title: "Burning audio CD with .cue file"
date: 2009-09-20
forum: Multimedia Software
---

### Post by revengeofthecow on 2009-09-20
I don't understand why this isn't working. I have the .flac files for the 2009 Beatles remasters, and a .cue file. The .cue file appears to be for the .wav files, so I used SoundConverter to change them. Now I have the .wav files, and I try to open the .cue file in Brasero, and it says it can't find the .cue file I just opened! Aarrrgh! I looked around threads everywhere, tried to get the .cue file to work with the .flac audio files, tried a lot, but it's still not working, and I don't understand why. K3B says it's not a valid .cue file. Below is the text in one of the files:

```
REM GENRE Pop

REM DATE 2009

REM DISCID D50E890F

REM COMMENT "ExactAudioCopy v0.99pb3"

FILE "01 - Taxman.wav" WAVE

  TRACK 01 AUDIO

    INDEX 01 00:00:00

  TRACK 02 AUDIO

    INDEX 00 02:37:13

FILE "02 - Eleanor Rigby.wav" WAVE

    INDEX 01 00:00:00

  TRACK 03 AUDIO

    INDEX 00 02:04:60

FILE "03 - I'm Only Sleeping.wav" WAVE

    INDEX 01 00:00:00

  TRACK 04 AUDIO

    INDEX 00 02:59:03

FILE "04 - Love You To.wav" WAVE

    INDEX 01 00:00:00

  TRACK 05 AUDIO

    INDEX 00 02:58:54

FILE "05 - Here, There and Everywhere.wav" WAVE

    INDEX 01 00:00:00

  TRACK 06 AUDIO

    INDEX 00 02:23:34

FILE "06 - Yellow Submarine.wav" WAVE

    INDEX 01 00:00:00

  TRACK 07 AUDIO

    INDEX 00 02:37:32

FILE "07 - She Said She Said.wav" WAVE

    INDEX 01 00:00:00

  TRACK 08 AUDIO

    INDEX 00 02:34:65

FILE "08 - Good Day Sunshine.wav" WAVE

    INDEX 01 00:00:00

  TRACK 09 AUDIO

    INDEX 00 02:08:19

FILE "09 - And Your Bird Can Sing.wav" WAVE

    INDEX 01 00:00:00

  TRACK 10 AUDIO

    INDEX 00 01:59:05

FILE "10 - For No One.wav" WAVE

    INDEX 01 00:00:00

  TRACK 11 AUDIO

    INDEX 00 01:58:26

FILE "11 - Doctor Robert.wav" WAVE

    INDEX 01 00:00:00

  TRACK 12 AUDIO

    INDEX 00 02:13:33

FILE "12 - I Want to Tell You.wav" WAVE

    INDEX 01 00:00:00

  TRACK 13 AUDIO

    INDEX 00 02:26:73

FILE "13 - Got To Get You Into My Life.wav" WAVE

    INDEX 01 00:00:00

  TRACK 14 AUDIO

    INDEX 00 02:27:70

FILE "14 - Tomorrow Never Knows.wav" WAVE

    INDEX 01 00:00:00

  TRACK 15 MODEx/2xxx

    INDEX 00 02:59:41

```

One thread I read suggested to remove everything before the first FILE line. I tried that, and nothing. Still says it can't find the .cue file. Any suggestions would be very much appreciated! Thanks in advance!

---

### Post by revengeofthecow on 2009-09-20
Are there any suggestions? Sorry, this is frustrating me to no end...

---

### Post by falconindy on 2009-09-20
Not sure why you need the .cue file at all... drop the files into k3b, make sure they're in order, and hit burn.

---

### Post by revengeofthecow on 2009-09-20
For things like gapless playback (albums like Sgt. Pepper's Lonely Hearts Club Band and Abbey Road make this necessary) I would rather the .cue file work.

---

### Post by bliffle on 2009-09-29
I share your frustration. I have a couple classical CDs in FLAC/Cue form (with the entire CD in one FLAC file) and am having difficulty burning to CD. Here's what I've tried:

-brasero
-K3B
-two cue-splitting scripts from the ubuntuforums
-burrrn (a windows program which I tried in XP)
-EAC (XP)

But 2 years ago when I first tried burning a FLAC/cue set to CD I had no problem, and now I can't remember how I did it! At that time I successfully burned a Mozart CD twice. Now I can't burn that same Mozart set any way that I try.

Recently I successfully burned a Bach CD using burrrn on XP, but now I can't repeat that success.

Are cue files just that fragile? It's hard to find a good spec on cue files. Also, some programs (like Exact Audio Copy, EAC) produce cue files that they themselves will not read! Incomprehensible!

Next thing I'm going to try is "Nero" on an old Win2000 computer I used to use for rendering years ago. Maybe my Mozart success occured on that machine.

---

### Post by bliffle on 2009-10-06
I used "Nero" on an old Windows 2000 laptop that I had put away and not used for a year and it worked!

In fact I burned several CDs with Nero before running into one cue/flac pair that, apparently, are inconsistent.

So, now I have a way to burn cue/flac pairs that have the entire CD in one flac: fire up the old W2000 system. But that's a big let-down because I was trying to get everything running on ubuntu.

---

### Post by ycherem on 2009-12-24
So far the best attempt I've made is installing Burrrn with Wine. It finally could recognize my cd driver, but in the end there was some weird error with the .cue file itself...

---

### Post by ycherem on 2009-12-24
Just an update... I finally managed to burn .cue + .flac file with Burrrn in Wine. I really think there is no better way of burning .cue files in gnome (kde has k3b, which I haven't tried for this purpose yet).

---

