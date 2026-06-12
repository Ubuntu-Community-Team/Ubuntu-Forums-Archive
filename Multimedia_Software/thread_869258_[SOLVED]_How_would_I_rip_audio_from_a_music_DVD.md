---
title: "[SOLVED] How would I rip audio from a music DVD?"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Xzallion on 2008-07-24
I bought a Nine inch Nails tour dvd, and like the music but don't care to watch the performance.  How would I go about ripping the audio to flac so I can listen to it in Amarok?

---

### Post by mc4man on 2008-07-24
I don't know about directly to flac but it's very easy to use mplayer to extract to .wav and then convert as wanted. Are you familiar with using mplayer from the cli?
 Is each song is confined to a single chapter or do they span across chapters? That would be the ideal, though there's several ways to get around if they span chapters.

---

### Post by xc3RnbFO8P on 2008-07-25
You can use DVD:RIP and Avidemux.
First rip the dvd with DVD:RIP,
then open the first vob with Avidemux, 
append the rest of the vobs.
In audio on the left side choose format (or copy).
Up on the top choose audio> save.

---

### Post by cariboo on 2008-07-25
Sound Juicer found in Applications-->Sound & Video-->Audio CD Extractor
will rip to flac. Just open Edit-->Prefereences and set your output format.

---

### Post by Xzallion on 2008-07-25
> **mc4man said:**
> I don't know about directly to flac but it's very easy to use mplayer to extract to .wav and then convert as wanted. Are you familiar with using mplayer from the cli?
 Is each song is confined to a single chapter or do they span across chapters? That would be the ideal, though there's several ways to get around if they span chapters.
I'm not familiar with using MPlayer from the cli, but each song is contained in a single chapter.  I'll look into this.


> **Ringi said:**
> You can use DVD:RIP and Avidemux.
First rip the dvd with DVD:RIP,
then open the first vob with Avidemux, 
append the rest of the vobs.
In audio on the left side choose format (or copy).
Up on the top choose audio> save.

Is .vob lossless?

> **cariboo907 said:**
> Sound Juicer found in Applications-->Sound & Video-->Audio CD Extractor
will rip to flac. Just open Edit-->Prefereences and set your output format.

Thats for audio cd's... at least thats what I thought.  This isn't an audio cd, but if it works for dvd's also let me know.

---

### Post by mc4man on 2008-07-25
the basic comm. would be this, variables in red
```
 mplayer -vc null -vo null -aid [COLOR="Red"]128[/COLOR] -ao pcm:fast:waveheader:file=[COLOR="Red"]foo1[/COLOR].wav dvd://[COLOR="Red"]1[/COLOR] -chapter [COLOR="Red"]1-1[/COLOR]
```

Above is assuming the dvd device is found @ /dev/dvd, if your drive was say /dev/dvd1 then 
```
mplayer -vc null -vo null -aid 128 -ao pcm:fast:waveheader:file=foo1.wav -dvd-device /dev/dvd1 dvd://1 -chapter 1-1

```

Shouldn't take any more than 15-20 secs per 5 min. of audio. Each chapter will be saved individually to home dir., you could probably add a different dir. to comm.
If you use the up arrow to repeat the command you'll only need to change the chapter #'s and the outputted .wav name. I usually just start at foo1, work up with the chapters and rename later.
You only need to set dvd://1 once, the # is the title # of what your're extracting from,just open movie and check in navigation.
The -aid is the # given to the audio stream you want to use. Usually the first available stream is given 128, and they progress by 1, but not always. You can get the id #'s by opening the disk with mplayer from cli. (probably others ways too.

```
mplayer dvd://[COLOR="Red"]1[/COLOR]
```  0r 
```
mplayer -dvd-device /dev/dvd1 dvd://[COLOR="Red"]1[/COLOR]

```
EX. of non standard 

> Playing dvd://6.
There are 8 titles on this DVD.
There are 14 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: lpcm (stereo) language: unknown aid: 160.
audio stream: 1 format: ac3 (5.1) language: unknown aid: 129.
audio stream: 2 format: dts (5.1/6.1) language: unknown aid: 138.
number of audio channels on disk: 3.

In this case because I'd want to use the lpcm track I'd use -aid 160 in the command.

Pretty simple once you do it .

If they spanned chapters you could still do them as above but you'd have line them up in order in amarok, the switching of tracks would be pretty much seamless.
Or you could just remove the chapter option and extract to one big .wav. Seeking probably wouldn't work in amarok so it's either listen from start onward or use a sound editor to cut individual .wav's. Possibly there's a way to use an option other than chapters to extrsct across them ?

If you see this ignore -  **** Your system is too SLOW to play this!  ****
If you see a _crc_ error maybe ignore, sometimes it shows up at end of rip,  Do though make sure disk is clean and in good shape, I'm not sure how tolerant process is to read errors. (ie. probably not at all, unlike 'ripping' to file(video_ts) where the app will retry x # of times.

---

