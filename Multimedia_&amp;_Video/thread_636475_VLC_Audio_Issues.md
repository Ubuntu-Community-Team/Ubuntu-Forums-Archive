---
title: "VLC Audio Issues"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by noremac on 2007-12-09
While watching a movie in VLC, usually within a minute of starting it, the audio of the movie will just stop. I sometimes hear a crackling sounds and sometimes I don't. Then, it seems that usually the video will also slip up a little and start skipping just a bit. I brought up an old thread on the VLC forums about someone else having what appeared to be the same problem. I did the steps that fixed it for this poster but they did not work for me. I tried to get more help in that thread, but doesn't appear to have been heard.

Those steps were resetting all preferences and then running the command:
rm -rf ~/.vlc

It was that command that helped the other poster. But not so much for me. I have now ran VLC from a command line to see if any error would pop up and sure enough there was one:

[00000338] alsa audio output error: write failed (Broken pipe)

That is what I get as the error whenever the audio quits. Anyone aware what this error is caused by? This is specifically happening in just VLC. All video programs work fine, but I really prefer VLC. It's been like this since I installed Ubuntu a few weeks ago. Have tried reinstalling, but that didn't help either. 

Thanks to anyone with information, 
-Cameron

---

### Post by noremac on 2008-01-14
Anyone?

---

### Post by noremac on 2008-01-20
I have tried reinstalling it multiple times, still no luck. Anyone know at all what this is from??

---

### Post by disturbed1 on 2008-01-21
>  [00000338] alsa audio output error: write failed (Broken pipe)VLC is having issues getting sound out. This could be caused by anything from improper alsa setup, to another application running alsa at the same time, to esd/arts being run in the background.

Try a logout, logback in, then running VLC. If the issue persists, change the audio out driver in VLC. Settings -> Preferences, check advanced options in the bottom right, Audio -> Output Modules. See screen shot below.

In the audio menu, you can choose the output driver (ALSA, OSS, SDL....) and which device ALSA and the like will use (default. hw:0,0, /dev/dsp and so on). I *_believe_* VLC has to be closed then restarted after you save settings for them to take effect.

---

### Post by noremac on 2008-02-08
Neat! I didn't know anyone responded to this thread till today. Thanks. I did have to change the output driver and now it appears to be working great. I appreciate your help!

---

