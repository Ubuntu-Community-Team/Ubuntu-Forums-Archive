---
title: "Lost audio when ripping DVD with dvd::rip"
date: 2008-11-05
forum: Multimedia Software
---

### Post by xfred on 2008-11-05
I'm having difficulty ripping some dvds I recently purchased.  Acidrip crashes when I try to rip them and vlc can't play them so I can't just redirect its output, but dvd::rip is able to rip playable VOBs (with audio).  However when I transcode them from VOB to AVI format the resulting AVIs have no audio (tested with movie player, gxine and vlc).  I've used dvd::rip to rip other dvds without running into this problem.  Anyhow, here's what VLC says about the VOBs:

- stream 0 codec mpgv type video
- stream 1 codec a52 type audio (selected)

Now I've double-checked to make sure that dvd::rip has the correct audio track selected - track 1, though in desperation I've also tried all of the other audio tracks, but to no avail - and it is.  Track 1: en ac3 48kHz 6Ch => 1, Bitrate 128, 48000 Hz, quality 2, volume rescale using 1.685 all seem ok.

Here are the commands that dvd::rip is using for the conversion:
```
mkdir -m 0775 -p '/home/me/dvdrip-data/losts4d1/tmp'
cd /home/me/dvdrip-data/losts4d1/tmp
mkdir -p /home/me/dvdrip-data/losts4d1/avi/001
execflow -n 19 transcode -H 10 -a 0 -x vob,null -i \/home\/me\/dvdrip\-data\/losts4d1\/vob\/001\/ -w 2791,50 -b 128,0,2 -s 1.685 --a52_drc_off -J smartyuv=threshold=10:Blend=1:diffmode=2:highq=1 -f 25.000 -R 1 -y xvid,null -o /dev/null --print_status 25
echo EXECFLOW_OK
mkdir -m 0775 -p '/home/me/dvdrip-data/losts4d1/tmp'
cd /home/me/dvdrip-data/losts4d1/tmp
mkdir -p /home/me/dvdrip-data/losts4d1/avi/001
execflow -n 19 transcode -H 10 -a 0 -x vob -i \/home\/me\/dvdrip\-data\/losts4d1\/vob\/001\/ -w 2791,50 -b 128,0,2 -s 1.685 --a52_drc_off -J smartyuv=threshold=10:Blend=1:diffmode=2:highq=1 -f 25.000 -R 2 -y xvid -o /home/me/dvdrip-data/losts4d1/avi/001/losts4d1-001.avi --print_status 25
echo EXECFLOW_OK
```

Now to me that looks fine (after briefly sifting through the manpage), but I'm guessing the problem must be in the above.  Any suggestions on what I might need to change to fix this problem?

---

### Post by xfred on 2008-11-09
UPDATE: I found that avidemux can extract the audio (but requires a mixer to convert to mp3 for some reason).  Now I just need to find a way to recombine my sound-free video and the audio tracks extracted using avidemux.

---

