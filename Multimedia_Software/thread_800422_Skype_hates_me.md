---
title: "Skype hates me"
date: 2008-05-19
forum: Multimedia Software
---

### Post by rhichi on 2008-05-19
So I've been trying to correctly install Skype 2.0 for Hardy Heron. I've spent all evening installing it correctly, messing with pulseaudio, and trying to workaround it, following suggestions that came from previous Ubuntu Forums threads. However, nothing seems to work. I can make the test call, but it does not pick up my voice message. When I try to call someone else, it never even attempts to connect (I see nothing under the ID picture that says connecting or ringing).I don't know what else I could possibly do.

---

### Post by rhichi on 2008-05-19
I also get this message in the work around terminal that I am running skype through as suggested by [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

```
ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
```

---

### Post by rhichi on 2008-05-19
This may also be affecting my chat but I'm not sure.

---

### Post by rhichi on 2008-05-19
Ok so I can make calls if I don't open it via pasuspender but I can only hear things, can't say anything.

---

### Post by Timbothecat on 2008-06-02
Hi Rhichi.

I was having the exact same problem. What I did to fix it was this:

Open Volume control (either by going to System > Preferences > Volume Control or by right-clicking the speaker icon up next to the date.)

[LIST=1]
[*]Open Volume control (either by going to System > Preferences > Volume Control or by right-clicking the speaker icon up next to the date).
[*]Go to File > Change Device and make sure it's on ALSA Mixer (Probably the top one, should have a card number etc in front of alsa mixer).
[*]Click Edit > Preferences to open a dialogue box.
[*]Make sure Microphone & Microphone Booster are ticked.
[*]Click close and test your settings again.
[*]If people still can't hear you, go to System > Preferences > Sound.
[*]Make sure that "Sound Events - sound playback", "Music and Movies - sound playback" & "Audio Conferencing - sound capture" are all set to alsa and the device should be your sound card number followed by (alsa mixer).
[/LIST]

This was what I had to do to fix my problem, I hope it helps you out too. Now if I could only fix my issues of skype crashing everytime I switch on my web cam! ](*,):evil::-({|=:roll:

All the best,

Tim.

P.S. I also followed the instructions on here [http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/) but it didn't work until I made the changes listed above. If you follow this "How to", please bear in mind the the section that talks about "sudo apt-get install libsdl1.2" is libs dl 1.2, but in the instructions it looks like 11.2 or ll.2, that caused me some grief I can tell you. Keep that in mind and you should be right.

---

