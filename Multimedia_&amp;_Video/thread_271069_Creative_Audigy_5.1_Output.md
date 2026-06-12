---
title: "Creative Audigy 5.1 Output"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by sc0tt on 2006-10-04
hey folks.

In my system, i can play sound at the moment (i think its going via alsa, not sure though). In alsamixer i see various front/rear/center settings for my soundcard, which alsamixer is showing as a "SigmaTel STAC9721,23"

lspci shows:

root@starlet:/etc# lspci | grep Creative
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:00:0c.1 Input device controller: Creative Labs SB Audigy LS MIDI/Game port

My question is this. In windows, i have an option with the EAX software included to set the card to upmix from 2.0 to 5.1. I'm well aware it doesn't actually upmix per se, it just feeds the audio via each additional speaker too, and also via the sub. The sound in my opinion, is much better than the front left & right speakers.

Is there any way i can do this with ubuntu, as its probably the only thing i miss from windows :P

Any help appreciated.

Scott.

---

### Post by sjieke on 2006-10-04
Yes you can using alsa and the asound.conf file

In this thread: [http://ubuntuforums.org/showthread.php?t=261317]("http://ubuntuforums.org/showthread.php?t=261317") you can find how I did it

---

### Post by sc0tt on 2006-10-05
I tried the speaker test, and i got:

ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'cards.SAA71 34.pcm.surround51.0:CARD=0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned err or: No such file or directory
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such file or directo ry
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory

So methinks its not recognised my card properly.

---

### Post by sjieke on 2006-10-06
He doesn't recognize the surround51 plug. This is normally default included in alsa, or maybe he doesn't recognize your card...

If you ommit the -D option of the speaker-test, so using the default settings, what do you get. Try also to change the channel numbers. -c6 is for 6 channels (5.1 surround), -c2 is 2 channels (stereo).
```
speaker-test -c6
```
or
```
speaker-test -c2
```

You can also check wether alsa found your card with following command:
```
cat /proc/asounds/cards
```

This should give a list of all cards recognized in alsa (including dummy's and virtual one). You can post it here again so I can have a look at it...

Also do you have an asound.conf or .asoundrc file, if so could you post that also, maybe there is a configuration issue...

---

### Post by dw5437 on 2006-10-06
Google 
Alsa Multi-channel Audio mini-HOWTO

Worked for me

---

