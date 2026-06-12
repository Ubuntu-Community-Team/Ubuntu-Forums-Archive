---
title: "VLC and Flash audio not working"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by Tom B on 2007-11-03
I'm running 7.10- everything worked fine in Feisty. Now, vlc and flash don't play audio- video plays fine in both, and everything else has sound. When I try to play a sound file with vlc, it returns the error: ```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[00000354] oss audio output error: cannot open audio device (/dev/dsp)
[00000354] main audio output error: couldn't find a filter for the conversion
[00000354] main audio output error: couldn't create audio output pipeline
```
I checked the /dev/dsp file:the audio group has read/write permissions and I am in the audio group.

When I try to play a flash video in swiftweasel (and firefox, and swiftfox), the video plays fine but there is no sound. It gives me: ```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
```

I have looked at dozens of threads of people with similar problems and have still been unable to fix this. I tried this: 
> Quote:
dentaku65
FIXED!
Code:

mv ~/.asoundrc .asoundrc.old
mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

Restart FF and ....tak flash audio is working!!

and it did not work. I tried the "getting the alsa drivers" section in [this thread]("http://ubuntuforums.org/showthread.php?t=205449"), but it didn't work either. I don't really know what I am doing, and I'm honestly a little surprised that I haven't messed up anything else trying to fix it. Any suggestions?

---

### Post by internetarchitect on 2007-11-04
I am having the same problem running Gutsy.  Anyone know what is going on?

---

### Post by jslmg on 2008-01-17
Same problem here--but only on Flash. Thread after thread of people with this issue, and for months now, and still no one with a fix?

---

### Post by tapu on 2008-06-28
i ma newbie yo ubuntu.
my prob is dat my vlc is playin video and no audio..
also gstreamer is either not playin or playing wd dead like hang..!!
help..!

---

