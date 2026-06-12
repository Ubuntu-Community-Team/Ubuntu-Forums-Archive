---
title: "audiophile 2496"
date: 2008-11-01
forum: Multimedia Software
---

### Post by verby on 2008-11-01
I have upgreaded to ii 8.10 and my sound card audiopile 2496 plays no sound. It it recognized but ... nothing comes out. Any additional driver to install?

---

### Post by verby on 2008-11-02
anyone?

---

### Post by Ruhani04 on 2008-11-02
Hello,
I have the same problem or let's say had.
I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
I issued a bug report but never got anywhere. So far as I can see there have been several bug reports for the same problems but no real solution.
Not sure why this is given such a low priority.
Good luck :)

---

### Post by Ruhani04 on 2008-11-03
This is a warning to my previous posting.
I followed the instructions before from the link replacing pulse audio with esound in the beta but now in the final intrepid it won't boot anymore.
It looks like no pulse audio no boot up possible.
However I did find a workaround with the live cd which worked for me.
[-X

---

### Post by verby on 2008-11-03
so you are suggesting that I shouldn't do it? Everything works ok, except the sound:-k
it has to be some resolution to this...

---

### Post by Ruhani04 on 2008-11-04
There is definitely a resolution since I got it to work and I am pretty new to Ubuntu. Basically what happened was that during boot up Ubuntu looked for some pulse audio session files which were missing so I booted up via live cd and copied two pulse audio session files to the installed Ubuntu directory where Ubuntu was looking for those files. So far I have sound in all applications.
I know I am improvising here and if you want to go that route it is at your own risk. Sorry for the amateur like answer but I haven't found one of the pros to solve it. For me sound is a must.

---

### Post by Ruhani04 on 2008-11-07
Update 
I just found the following link
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
I followed the instructions for intrepid and I got the best sound ever with my audiophile 24/96. I am amazed at the quality and detail oss is delivering.
I am sorry but alsa and pulse audio are no match here.\\:D/\\:D/

---

### Post by verby on 2008-11-10
Thank you... IT WORKS !:guitar:

---

### Post by unknown03 on 2008-11-11
I might be a little late, but I just fixed my problem. I too have an audiophile 2496 and wasnt getting any sound with Intrepid 8.10.

Turns out, for me anyways, the problem is PulseAudio -- how I fixed it was opening a terminal and entering:

```

sudo apt-get purge pulseaudio
sudo rm /etc/X11/Xsession.d/70pulseaudio

```

---

### Post by Riverside on 2008-11-20
Sorry to hijack this thread but - how good is the Audiophile 2496 soundcard?  I have recently purchased a pair of M-Audio Studiophile AV 40 desktop speakers and am considering an Audiophile 2496 soundcard to go with them, currently I am using my DP35DP motherboard's onboard Intel HD Audio.

---

### Post by verby on 2008-11-21
I used audiophile 2496 on my home studio. To record some demos.
AFAIK and from my own experience this card is awesome.
Highly recommend it.

---

### Post by ironflippy on 2008-11-21
The card sounds fantastic if all you need are some stereo ins/outs. It doesn't match up to an RME or Apogee but those are also a magnitude of price extra. Nice card for some good quality audio. I use it at home with my Tannoy monitors.

---

### Post by unknown03 on 2008-12-20
> **Riverside said:**
> Sorry to hijack this thread but - how good is the Audiophile 2496 soundcard?  I have recently purchased a pair of M-Audio Studiophile AV 40 desktop speakers and am considering an Audiophile 2496 soundcard to go with them, currently I am using my DP35DP motherboard's onboard Intel HD Audio.

again I'm a little late,

I bought the audiophile 2496 because I needed a cheap production audio card. Keyword is CHEAP. M-audio does not officially support Vista 64bit or Linux and refuse to do so.. Just something to keep in mind. I would go with a more reputable company, but I am not sure which one is the best.

But from my research I would be wary of M-Audio and MOTU ...there may be a few others, but I cannot remember them right now

---

