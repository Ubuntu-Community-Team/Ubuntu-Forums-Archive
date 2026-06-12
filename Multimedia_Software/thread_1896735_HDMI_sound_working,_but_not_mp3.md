---
title: "HDMI sound working, but not mp3"
date: 2011-12-17
forum: Multimedia Software
---

### Post by mc@2 on 2011-12-17
Yeah, another HDMI-sound question. But the good news is that sound via HDMi is working! Well, for movies and wav files it seem. So what works?
- movies played with xbmc with ac3 audio stream
- aplay -D plughw:0,3 /usr/share/sounds/alsa/Side_Right.wav

What doesn't work? Anything with mp3. So my mp3's and movies with mp3 audio stream stay silent. If i play such a movie or mp3 (in xbmc) i get no errors but simple no sound.

I've installed ubuntu-restricted-extras, got no /etc/asound.conf nor .asoundrc present and i'm running vanilla 11.10.

Any ideas how to go from here?

---

### Post by mc@2 on 2011-12-18
Hmm, the plot thickens. mpg321 -a hdmi test.mp3 works good and gives sounds via hdmi on my TV.

Any idea why the mp3's played in xbmc won't give sound?

---

### Post by MoreOrLess on 2011-12-18
You need libmp3lame0 package.

---

### Post by mc@2 on 2011-12-18
I don't think that's the solution:

[FONT="Courier New"]sudo apt-get install  libmp3lame0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmp3lame0 is already the newest version.
libmp3lame0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]

Odd thing is that played with mpg321 i get sound, but played from xbmc, no sound.

---

### Post by BicyclerBoy on 2011-12-18
Try both these (don't change anything):
In a terminal:
speaker-test -c 2 -r 44100 -D hw:0,3
speaker-test -c 2 -r 48000 -D hw:0,3

close/re-open terminal between each command..

ls -al /proc/asound/card0/eld#*

cat each eld# file for one that is valid/not-empty..post it here..

---

### Post by mc@2 on 2011-12-23
ls -al /proc/asound/card0/
total 0
dr-xr-xr-x 7 root root 0 2011-12-23 23:13 .
dr-xr-xr-x 4 root root 0 2011-12-23 23:13 ..
-r--r--r-- 1 root root 0 2011-12-23 23:13 codec#0
-r--r--r-- 1 root root 0 2011-12-23 23:13 codec#3
-r--r--r-- 1 root root 0 2011-12-23 23:13 id
dr-xr-xr-x 3 root root 0 2011-12-23 23:13 pcm0c
dr-xr-xr-x 3 root root 0 2011-12-23 23:13 pcm0p
dr-xr-xr-x 3 root root 0 2011-12-23 23:13 pcm1p
dr-xr-xr-x 3 root root 0 2011-12-23 23:13 pcm2c
dr-xr-xr-x 3 root root 0 2011-12-23 23:13 pcm3p

So no eld files found?

---

### Post by mc@2 on 2011-12-29
Anyone?

---

### Post by BicyclerBoy on 2011-12-29
What about the speaker-test commands ?

aplay -l
aplay -L

No eld data/files could mean that your hdmi audio (video card) does not support audio eld handshake.

---

