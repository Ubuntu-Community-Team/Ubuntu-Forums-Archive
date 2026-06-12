---
title: "No audio in mpeg1 and flv files."
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by Buntuuser01 on 2008-03-28
Hi there Ubuntu fans!

Maybe this has been addressed before, but I can not find the answer w/ the search function. I use Ubuntu 7.10 the Gutsy Gibbon for my Freevo mediacenter. However, when I try to watch an mpeg1- or (offline) flv video file I do not have audio. Some players and Avidemux even crash... I do not have this problem w/ Suse. I think I have all the right codecs installed. I've enabled the Medibuntu repository.

Anyone else have this problem, or a solution?

Best regards, Buntuuser01

---

### Post by xc3RnbFO8P on 2008-03-28
If you have VLC player use Terminal:
vlc> return
Show the output

---

### Post by Buntuuser01 on 2008-03-28
The output of VLC is:
```

VLC media player 0.8.6c Janus
*** PULSEAUDIO: Unable to connect: Connection refused
Segmentation fault

```

---

### Post by xc3RnbFO8P on 2008-03-28
See if this helps:
[http://ubuntuforums.org/showthread.php?t=658044&page=2&highlight=pulseaudio]("http://ubuntuforums.org/showthread.php?t=658044&page=2&highlight=pulseaudio")

Found another solution: 
> go to applications>sound and video>pulseaudio manager and click the "connect" button. For me the connection is being refused.

---

### Post by Buntuuser01 on 2008-03-28
Thanks for your help ! :)
I think the problem must bu Pulseaudio too. A few weeks ago I tried Pulse, but removed it again. Now I removed some more Pulse packages, and mpeg1 audio did work in VLC once. However, after a reboot audio in mpeg1 files didn't work anymore. Again, I get a Pulse relates error:

```
VLC media player 0.8.6c Janus
ALSA lib pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so

```

I would very much like to completely remove Pulseaudio and I want my media players (vlc, xine, mplayer etc.) NOT to look for Pulse anymore. Anybody got a solution?

In the mean time I'll try to reinstall Pule and see is that helps.

P.S. I cannot remove "libpulse0": dependency problems....

---

### Post by xc3RnbFO8P on 2008-03-28
> I would very much like to completely remove Pulseaudio
That was one of the solution.

---

### Post by Buntuuser01 on 2008-03-28
Installed as many Pulse packages as I could. But I just don't get it. I've absolutely no idea what do do or configure. It all seems to work, but no sound!

Error in VLC:
```
VLC media player 0.8.6c Janus
ALSA lib pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
[00000361] oss audio output error: cannot open audio device (/dev/dsp)
[00000361] main audio output error: couldn't find a filter for the conversion
[00000361] main audio output error: couldn't create audio output pipeline
[00000281] main playlist: nothing to play

```
I don't get it: I don't use OSS. I would very much like to get rid of anything Pulseaudio related. But how? And why is VLC "Pulse aware", even if I uninstalled it. I want it to simply use Alsa because that works. :(

Anybody got any success in **completely** removing Pulse?

---

### Post by Buntuuser01 on 2008-03-28
> **Ringi said:**
> That was one of the solution.
Ooops. My problem is that, no matter how many PA packages I throw away via Synaptic, I just cannot get rid of PA related error messages. Strange isn't it?

---

### Post by xc3RnbFO8P on 2008-03-28
try:
> sudo apt-get install esound
> sudo apt-get remove pulseaudio

---

### Post by Buntuuser01 on 2008-03-29
> **Ringi said:**
> try:
Thank you very much! :)
I had no idea that I had to re-install ESD manually. I thought Esound and Pulseaudio co-existed, and removing PA was enough. 

Problem solved, audio in mpeg1 and flv videos is perfect now, and no errors.

---

### Post by xc3RnbFO8P on 2008-03-29
mark this solved in thread tools :)

---

