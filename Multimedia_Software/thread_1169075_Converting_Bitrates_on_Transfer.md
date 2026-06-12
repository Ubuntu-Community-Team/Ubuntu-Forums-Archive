---
title: "Converting Bitrates on Transfer"
date: 2009-05-24
forum: Multimedia Software
---

### Post by emeraldgirl08 on 2009-05-24
Hi. I sure hope I can explain this without confusing people.

I have a lot of digital files of music that are encoded at 320 kb/sec. I have an MP3 player that isn't capable of holding that much music- especially if they're at 320! On the M$ side I would use Nero to convert the bitrates to something like 192 kb/s or a variable bit rate around 192.

Problem is I have a small HD and have alot of music stored on DVD's. I was wondering if there is a program that will convert "on-the-fly" 320 kb/s DVD MP3's to 192 kb/s (or VBR) SD cards? 

It sounds a little complicated but I could do it with Nero. I'm using Ubuntu 99% of the time these days so I don't like rebooting to get back to XP and vice versa. Thanks.

---

### Post by TheNosh on 2009-05-24
Audacity can change bitrates, you just need the lame plugin to encode to mp3

---

### Post by emeraldgirl08 on 2009-05-24
Coolbeans :D

I'll give it a try!

---

### Post by emeraldgirl08 on 2009-05-24
I've installed Audacity. I just need to figure out how to import an album and set the conversion for whatever bitrate I want. Can anyone help me??? I already have the output folder set for CF card so I'm good there :)

---

### Post by TheNosh on 2009-05-25
i think audacity can only do one song at a time, i don't have a solution for doing whole albums all at once. sorry if i wasn't any help. maybe someone else can offer better advice

good luck

---

### Post by mc4man on 2009-05-25
If audacity doesn't work out, probably soundconverter or something similar may work.

If space is an issue you could  use ffmpeg to go directly from dvd to your removable media . (tested from dvd drive to usb flash
If your tracks are in a directory structure on the dvd  and if you wanted to do 1 directory (album) at a time, keeping the same files names and directory name,  a simple script could handle that.

The main issue there would be if you needed some tags for your player though if so they could be tagged after transfer. ( though it would be possible to add some simple tagging to end of script

I don't know scripts well but here's something simple, and tagging could be added.

In this case I made a directory on the flash drive named mp3, the dvd (my son's) was mounted at /media/cdrom0 and the flash drive at /media/disk

the script was run from a directory prompt of one of the albums "Placebo" at /media/cdrom0/1996 Placebo - Placebo

Terminal output (begining
> doug@doug-desktop:/media/cdrom0/1996 Placebo - Placebo$ convert3
path to destination?
/media/disk/mp3
Name of album?
Placebo
FFmpeg version SVN-r18769, Copyright (c) 2000-2009 Fabrice Bellard, et al.
Input #0, mp3, from '01 - Come Home.mp3':
  Duration: 00:05:09.19, start: 0.000000, bitrate: 320 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 320 kb/s
Output #0, mp3, to '/media/disk/mp3/Placebo/01 - Come Home.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    3077kB time=131.29 bitrate= 192.0kbits/s 

Basic script without tagging
[PHP]#!/bin/bash
echo "path to destination?"
P= read P
echo "Name of album?"
N= read N
mkdir -p "$P"/"$N"
for f in *.mp3; do ffmpeg -i "$f"  -acodec libmp3lame -ab 192k "$P"/"$N"/"${f%.wav}"; done
[/PHP]

---

### Post by TheNosh on 2009-05-25
Ah! i think i may have found something useful after all. if you could do it with nero in windows, i would asume you can do the same in ubuntu. 

Nero has a linux version, and even handy dandy .deb packages!
heres the trial [http://www.nero.com/eng/downloads-linux3-trial.php](http://www.nero.com/eng/downloads-linux3-trial.php)

and i may still be wrong, the features may be different, i don't know much about nero and i've never used it myself

---

### Post by emeraldgirl08 on 2009-05-26
Thanks Nosh.

I've downloaded Audacity and figured out how to do the conversions :)

I'm all good now!

**Edit:** Just read your thread mc4man. Those scripts are awesome!!! I couldn't find a way to do the whole folder in one shot on Audacity. I have to try that one of these days :)

---

