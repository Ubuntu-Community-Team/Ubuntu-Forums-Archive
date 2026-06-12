---
title: "Cannot record from microphone"
date: 2006-02-13
forum: Multimedia &amp; Video
---

### Post by Halmonster on 2006-02-13
I have an eMachines laptop (m5305).  I have booted this machine in Windows XP and used the line-in port w/ a Plantronics headset microphone, so I know the hardware works.

Sound device = ALI 5451

Nothing I do in Ubuntu allows me to record audio using this device.  I have looked at the Volume Control applet, and tried all permutations of my Capture settings, under both ALSA and OSS.  I have tried Audacity and the Gnome Sound Recorder application.

I can play audio just fine, both through the speakers and through the headset.

`lsmod | grep snd` shows this:
[INDENT]snd_ali5451            22596  2
snd_ac97_codec         72188  1 snd_ali5451
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm
[/INDENT]

Any and all help is welcome.

Thanks,
Hal

P.S. I have the same problem on an IBM ThinkPad T42 running Hoary, but I'll tackle that later.

---

### Post by wncben on 2006-02-13
I am pretty new to linux and ubuntu, but it seems like alot of times alsa oss and esd do not play nice together, and hog the soundcard.  It seems like setting up a duplex system makes them work togethet, and allows you to capture and playback sound at the same time.  Check out this thread:
[http://ubuntuforums.org/showthread.php?t=126975&page=6](http://ubuntuforums.org/showthread.php?t=126975&page=6)
and see if it helps..    I have my current setup on post 56, but the posts above it show the howto's I used,  (check them out! :-D ) and the troubleshooting process I went through to tweak my system.
Hope this helps.

~Ben

ps..  the howto's are from the Hoary forum, and they should help your other system too.

---

