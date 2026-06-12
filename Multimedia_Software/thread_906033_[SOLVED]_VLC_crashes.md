---
title: "[SOLVED] VLC crashes"
date: 2008-08-31
forum: Multimedia Software
---

### Post by xjgnsdof on 2008-08-31
When I try to play a video in VLC, I get the following output in my terminal:

```
VLC media player 0.8.6e Janus
mdb:187, lastbuf:0 skiping granule 0
mdb:187, lastbuf:0 skiping granule 0
[00000384] pulse audio output error: Failed to connect to server: Connection refused
[00000384] pulse audio output error: Pulse initialization failed
vlc: pcm_plug.c:388: snd_pcm_plug_change_channels: Assertion `snd_pcm_format_linear(slv->format)' failed.
Aborted

```

VLC crashes, and the video never plays.

---

### Post by xjgnsdof on 2008-09-01
up

---

### Post by nicedude on 2008-09-01
Well it looks like a failure of pulse audio, try running "gnome-sound-properties" without quotes in a terminal and then when it pops up try selecting alsa for all the choices and see if that works for you.


Also what kind of video are you trying to play?

---

### Post by xjgnsdof on 2008-09-01
Everything is already set to ALSA. I can't play FLV videos; before I reinstalled Ubuntu, I could.

---

### Post by nicedude on 2008-09-01
Don't know what to tell you then as it is clearly related to pulse audio as you can see in your error message. I just yesterday uninstalled pulse audio altogether on my laptop since I use alsa and don't need it. Also you might want to look in the forums for how to install Adobe Flashplayer 10 as it helped me with some firefox flash playback freezes I was having but I think VLC uses its own codecs for everything so I don't know if that would change anything other than better flash playback in firefox.

Sorry I couldn't be more help


-=Edit =-
I didn't tell you to uninstall anything in my post, I only told you what I did since I didn't need pulse but instead I do need alsa. 

I just found your answer via googling your error codes in 3 minutes so why not google this and see if you can find the answer as it doesn't take sherlock holmes , larry holmes could figure this out (with the help of google of course).

---

### Post by xjgnsdof on 2008-09-01
I never had to uninstall Pulse before, so I think I'll leave it and try something else to get VLC working. Does anybody else have advice?

---

### Post by mc4man on 2008-09-01
> Everything is already set to ALSA
Does that include the audio output module in vlc? 
settings -> preferences -> click show advanced options -> expand audio -> highlight output modules and change in drop down on right.
**click save**
If you go there then also highlight interface and ck. 'show advanced options' (disabled by default

---

### Post by xjgnsdof on 2008-09-01
I changed the output to ALSA in VLC, but I get a different error message:

```

vlc: pcm_plug.c:388: snd_pcm_plug_change_channels: Assertion `snd_pcm_format_linear(slv->format)' failed.
```

Any video I want to play still crashes VLC.

---

### Post by mc4man on 2008-09-01
I don't have any flv video so not much help there. I'd try switching the output module to OSS or try another player for flv.

---

### Post by xjgnsdof on 2008-09-01
I did a fresh install of Ubuntu, though I kept my home folder and the settings therein. Perhaps one of my settings is tripping VLC up?

---

### Post by mc4man on 2008-09-01
Don't know, did you try oss?
 If so and no go it wouldn't hurt to delete the .vlc folder in home dir. (you'll have to reset settings -> preferences .... again

edit: dated but very similar
[http://mailman.videolan.org/pipermail/vlc-devel/2006-February/022655.html](http://mailman.videolan.org/pipermail/vlc-devel/2006-February/022655.html)

---

### Post by xjgnsdof on 2008-09-01
When I switched to OSS output in VLC, I get playback for all file formats, but no sound.

My Terminal output reads as follows:
```

VLC media player 0.8.6e Janus
mdb:187, lastbuf:0 skiping granule 0
mdb:187, lastbuf:0 skiping granule 0
[00000384] oss audio output error: cannot open audio device (/dev/dsp)
[00000384] pulse audio output error: Failed to connect to server: Connection refused
[00000384] pulse audio output error: Pulse initialization failed
[00000384] jack audio output error: failed to connect to JACK server
mdb:255, lastbuf:188 skiping granule 0
mdb:255, lastbuf:188 skiping granule 0

```

---

### Post by mc4man on 2008-09-01
i'm sure there are other threads, for starters

[http://ubuntuforums.org/showthread.php?t=767880](http://ubuntuforums.org/showthread.php?t=767880)

---

### Post by xjgnsdof on 2008-09-01
I did what the OP did, but to no avail. You'd think a fresh installation of VLC on a fresh installation of Ubuntu would work. I even tried deleting the .vlc folder in my Home partition. Still no video and/or sound.

---

### Post by xjgnsdof on 2008-09-03
up

---

### Post by xjgnsdof on 2008-09-04
up

---

### Post by xjgnsdof on 2008-09-05
I figured out the problem after checking out a Fedora forum.

"Settings" -> "Preferences" -> tick "Advanced Options" -> "Output Modules" -> select audio output module from the dropdown menu (I use ALSA) -> expand "Output Modules" and select the subcategory that matches your output module -> "Refresh List" -> select your sound device

Now, every video I throw at VLC plays perfectly. VLC was just telling me that I hadn't selected the sound card yet.

---

