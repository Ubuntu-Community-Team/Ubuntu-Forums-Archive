---
title: "Strange Audio Issues"
date: 2009-05-20
forum: Mythbuntu
---

### Post by blade944 on 2009-05-20
My Setup is as follows:
Gigabyte GA-73PVM-S2H motherboard
Intel Q6600 Core 2 Quad
2 Gig Kingston Ram
500 Gig Western Digital Drive
Motorola DCT-6200 Attached Through Firewire
Audio out through SP/DIF only
Running Version 9.04

Problem:
 2 weeks after installing I lose audio in Myth Movies.
Audio continues to work in TV and Music. If I try to view a Divx, Xvid or MKV file with VLC, Mplayer, or Xine there is also no audio.
This occurred with the last release as well. Without fail 2 weeks after the install I would no longer get Audio from my Divx, Xvid, or MKV backups.
 I have made no changes to the setup to cause this problem.
The last time this happened I watched a movie in the morning. Took the dog for a walk. And upon my return the next movie I tried to watch had no more audio.
  Alsa mixer still has the same settings as I had them at prior to the problem.
  Any help would be greatly appreciated.

---

### Post by blade944 on 2009-05-31
Did a fresh install at the time of the first post and all audio was working till I rebooted the system this morning. This was the first reboot of the system since the install. 
  Now the only audio I get is from mpeg sources , ie: tsmpeg stream from cable box, DVD, and mpeg video files.
  Divx, Xvid, MKV, mp3 etc. has no audio. 
  No settings have changed. I have checked alsa mixer and all is still as it was.
  I have tried to play these files through Mplayer, Xine, and VLC and the same problem exists.
  I am stumped as to what is causing this. It is almost as if the codec needed for the audio play back is not initializing.
  The only way I have found to fix the issue is to do a fresh install.
  Any help with this would be greatly appreciated.

  I am going to try adding a different audio card than the on-board sound but am not expecting any different results as the I am getting sound, just not for all file types.

---

### Post by Neon Dusk on 2009-05-31
I've got the same MB and sometimes get this - usually after watching BBC HD.

Doing a speaker test brings the sound back for me.
```
speaker-test -c2 --device cards.pcm.iec958 --rate 44100
```

---

### Post by blade944 on 2009-05-31
Fantastic.....That did the trick!!!
Thanks so much for your help.
I'm gonna give a Creative Labs card a try to see if this issue would be resolved that way as well. 
  Having to do the audio test all the time is not too wife friendly LOL

---

