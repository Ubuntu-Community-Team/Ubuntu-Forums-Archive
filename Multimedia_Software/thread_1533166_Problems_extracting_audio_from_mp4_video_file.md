---
title: "Problems extracting audio from mp4 video file"
date: 2010-07-17
forum: Multimedia Software
---

### Post by ChildOfMana on 2010-07-17
Hi,

I'm trying to extract the audio from an mp4 video file and convert it to mp3 using ffmpeg. The problem is that the resulting audio file is only 3m2s long, whereas the video file is 8m15s long.

Anyone know why the audio file is being truncated? Am I doing something wrong? Apart from being truncated the mp3 file plays perfectly.

Here's what ffmpeg has to say about the video file:

```
Seems stream 1 codec frame rate differs from container frame rate: 59.83 (59834/1000) -> 29.92 (359/12)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Part1.mp4':
  Duration: 00:08:15.60, start: 0.000000, bitrate: 541 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 1152x720, 29.92 tbr, 29.92 tbn, 59.83 tbc
```

And here's the command I'm using to extract and convert the audio:

```
ffmpeg -i Part1.mp4 -ab 128k Part1.mp3
```

Any help/advice will be greatly appreciated.

Thanks guys.

---

### Post by ChildOfMana on 2010-07-19
Bump?

If you can't help with the above then does anyone know of an alternative method of extracting the audio that may achieve the desired results? Maybe using Mencoder or similar? Preferably using the command line but I'll settle for a GUI option.

Cheers guys.

---

### Post by ron999 on 2010-07-19
Hi
WinFF is a GUI for ffmpeg.
The mp3 pre-set that it uses does pretty much the same as your command.
```
ffmpeg -i foo.mp4 -acodec libmp3lame -ab 160kb -ac 2 -ar 44100 foo.mp3

```
Another alternative is SoundConverter. It will do the job.

---

### Post by Jose Catre-Vandis on 2010-07-19
What happens if you output to wav (e.g. no re-encoding)?

---

### Post by ChildOfMana on 2010-07-19
**@ron999** Thanks but the code you provided achieves the same result unfortunately - a 3m2s audio file. I'll give the GUI a go when I get the chance. I'll let you know how I get on.

**@Jose Catre-Vandis** The same happens when I output to .wav - 3m2s :(

I'm seriously stumped :-k

Thanks so far anyway guys.

---

### Post by Jose Catre-Vandis on 2010-07-19
How about if you re-encode both video and audio, something like this:
```
#!/bin/bash

#convert mp4 to avi

FILES="*.mp4"

for F in $FILES

do
newname=`basename "$F" .mp4`
echo $newname

mencoder "$F" -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1500:mbd=2:trell:v4mv:autoaspect:turbo -vf pp=lb -oac mp3lame -lameopts vbr=3 -o "$newname.avi"

done
```
If this works then, you can rip the audio from the avi generated

or, I spotted you are not using the -vn switch
```
ffmpeg -i foo.mp4 -vn -acodec libmp3lame -ab 160kb -ac 2 -ar 44100 foo.mp3
```

---

### Post by ChildOfMana on 2010-07-21
Hi Jose.

The same problem occurs using the -vn switch unfortunately.

I haven't got time right now to try the other method you've suggested but I will do as soon as I get chance. I'll post back here and let you know how I get on.

Thanks for the help so far.

---

### Post by ron999 on 2010-07-21
OK Mana
Try extracting the aac soundtrack first.
Then check the duration.
If it's OK then convert it to mp3 afterwards.

This command ought to do it:-
```
ffmpeg -i foo.mp4 -vn -acodec copy foo.m4a
```

---

### Post by ChildOfMana on 2010-07-25
[quote="ron999"]OK Mana
Try extracting the aac soundtrack first.
Then check the duration.
If it's OK then convert it to mp3 afterwards.[/quote]


Thanks ron999 but I'm afraid the length is still only 3m2s.

---

### Post by ron999 on 2010-07-25
Hi
I'm out of ideas now.
Maybe you've got a corrupt file.

---

### Post by mc4man on 2010-07-25
IF the video plays with a player with full length audio then you could try using arecord to record/convert the audio to wave.

You may or may not get a good sound file - best if keeping the sample format and sample rate the same as source, there are 2 shortcuts that work ok for many sources - 
-f cd  and -f dat
See arecord --help

Ex. for a 6 min (-d <secs>) video with aac 48k using a shortcut

arecord -d 360  -c 2 -f dat /home/doug/test1.wav

---

### Post by ChildOfMana on 2010-07-29
Thanks mc4man I'll give it a try and see what happens.

@ron999 I thought that might be the case too but I've re-downloaded the file and am having the same problem. Perhaps the source is corrupt?

I'll try mc4man's way and see what happens. If not I think I'll have to admit defeat on this one!!

Thanks again guys.

---

### Post by kassoulet on 2010-08-03
Maybe the video is in fact two (or more!) files concatenated. 

To extract sound from such a file, we'll abuse gstreamer a little bit:

```
gst-launch-0.10 playbin2 uri=movie.mp4 audio-sink='identity single-segment=true! wavenc ! filesink location=foo.wav'
```

---

