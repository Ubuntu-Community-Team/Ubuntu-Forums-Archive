---
title: "Anybody help? No Hauppauge capture through VLC (WAH)"
date: 2010-04-28
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-04-28
I'm just not getting anywhere here after 12 - 15 hours of googling last 3 days...

I'm linked out, and linked back, almost into a do-loop, just like a boomerang, and still no vids...

---

### Post by Mud.Knee.Havoc on 2010-04-28
I finally figured out how to use mine... I forget exactly which version I've got (does PVR-250 sound right?), but I found that everything was set up right except that I needed to change the channel via a command in order to get everything going.  I was trying to copy a VHS tape to the computer and then convert to DVD.

Can you let us know which Hauppauge card you've got, as well as anything else that might be useful?

EDIT: I just found the commands in my bash history which I used to get VHS capture running.  Here they are in order:

```
sudo aptitude install scantv
```
(I forget what this was for... does it supply ivtv-tune or something?)

```
v4l2-ctl -i 0
```
(0, 1 and 2 choose between coax, AV cables, and whatever else - if my memory is correct)

```
ivtv-tune -c3
```
(I wanted channel 3 because it's an old-school VCR)

```
vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts ,dst="/home/user/output.mpg"}}'
```
(This command opens a window so I can see what's being recorded while outputting it to "output.mpg" at the same time.)

---

### Post by Moozillaaa on 2010-04-28
Well, it loaded perfectly. You're the man. 

The card is a 500 - same as 150, just 2 tuner chips. Mine was installed right also, and was showing up by chipset ID, card ID, and tuner1, 2 in lots of places...

Now for extra credit:
How can I tell if the configuration settings for VLC (or any other settings - software OR hardware), can be tweaked, for optimal recording, IN VLC???

And volume control, for max record levels, without distortion?

CLI return shows this:


[00000427] main video output warning: late picture skipped (136707)
[00000427] main video output warning: late picture skipped (103345)
[00000427] main video output warning: late picture skipped (69982)
[00000427] main video output warning: late picture skipped (36619)
[00000427] x11 video output debug: x11 image size 720x540 (0,0,720x540)
[00000427] main video output warning: late picture skipped (24580)
[00000431] main private debug: decoded 104/105 pictures
[00000392] main audio output warning: resampling stopped after 12811217 usec (drift: -10100)
[00000427] main video output warning: late picture skipped (35264)
[00000427] main video output warning: late picture skipped (1926)
[00000427] main video output warning: late picture skipped (33371)
[00000427] main video output warning: late picture skipped (37)
[00000427] main video output warning: late picture skipped (144395)
[00000427] main video output warning: late picture skipped (111055)
[00000427] main video output warning: late picture skipped (77381)
[00000427] main video output warning: late picture skipped (44019)
[00000427] main video output warning: late picture skipped (10656)
[00000427] main video output warning: late picture skipped (23197)
[00000431] main private debug: decoded 104/105 pictures
[00000392] main audio output warning: output date isn't PTS date, requesting resampling (45332)
[00000392] main audio output warning: buffer is 56020 late, triggering upsampling
[00000392] main audio output warning: output date isn't PTS date, requesting resampling (45157)
[00000427] main video output warning: late picture skipped (1436)
[00000392] main audio output warning: resampling stopped after 13003577 usec (drift: -29056)
[00000392] main audio output warning: output date isn't PTS date, requesting resampling (89882)
[00000392] main audio output warning: buffer is 117771 late, triggering upsampling
[00000427] main video output warning: late picture skipped (959)
[00000392] main audio output warning: resampling stopped after 16820668 usec (drift: 5679)
[00000392] main audio output warning: output date isn't PTS date, requesting resampling (47704)
[00000392] main audio output warning: buffer is 51547 late, triggering upsampling
[00000392] main audio output debug: audio output is starving (24109), playing silence
[00000427] main video output warning: late picture skipped (4218)
[00000392] main audio output warning: resampling stopped after 10455020 usec (drift: -3034)
[00000392] main audio output warning: output date isn't PTS date, requesting resampling (66353)
[00000392] main audio output warning: buffer is 83630 late, triggering upsampling
[00000427] main video output warning: late picture skipped (2545)
[00000392] main audio output warning: output date isn't PTS date, requesting resampling (67683)
[00000392] main audio output warning: resampling stopped after 12514647 usec (drift: -80703)
[00000392] main audio output warning: buffer is 80870 late, triggering upsampling
[00000392] main audio output warning: resampling stopped after 12509279 usec (drift: -13672)
[00000392] main audio output warning: output date isn't PTS date, requesting resampling (45296)
[00000392] main audio output warning: buffer is 56134 late, triggering upsampling
[00000392] main audio output warning: output date isn't PTS date, requesting resampling (157436)
[00000392] main audio output warning: audio drift is too big (209607), dropping buffer
[00000392] main audio output warning: audio drift is too big (185607), dropping buffer
[00000392] main audio output warning: audio drift is too big (157729), dropping buffer
[00000392] main audio output warning: audio drift is too big (133729), dropping buffer
[00000392] main audio output warning: timing screwed, stopping resampling



Hardware should handle MUCH more - new stuff, Hardy x64, Athlon II 3-core 3.0Ghz doing only this now:

---

