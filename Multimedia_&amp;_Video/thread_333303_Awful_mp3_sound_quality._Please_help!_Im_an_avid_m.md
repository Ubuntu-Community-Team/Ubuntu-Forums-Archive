---
title: "Awful mp3 sound quality. Please help! Im an avid music listener!"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by jamesoz91 on 2007-01-07
Hi.
I recently did a fresh install of Edgy on my external hard drive after getting very annoyed with the Windows that blights the internal hard drive of the computer I share with some other people.

Everything else seems to be working fine now - although not without a fair bit of work - except the sound quality when playing back mp3 (mpeg-1 layer 3) files. It is absolutely woeful.

It's not the speakers, I've tried with my iPod using the speakers and the quality is fantastic. And it's not the sound card, I've tried playing back music on Windows, and the quality was still very good.

I'm using AmaroK for my music collection. Most of the music I have is in MP3, although a little of it is in AAC/MP4 because in the old days I had iTunes. That music seems to be playing back perfectly. It's definitely just the MP3 files I have a problem with.

Any help with this? I have absolutely NO idea about the internal mixers of Linux or anything like that. I've heard about packages called "gstreamer" and "libxine" and I'm fairly certain they're for sound. But I have no idea what they do.

I'm an avid music listener, and this is really turning me off Ubuntu. ](*,)

---

### Post by pay on 2007-01-07
Try```
sudo aptitude install gstreamer-mad
```Which is in the universe repository.

---

### Post by meng on 2007-01-07
What about the sound quality with something other than mp3 playback (e.g. perhaps DVD sound or wav)? In other words, could it be the sound driver/configuration in Ubuntu, rather than something mp3-specific? What sort of sound card is this?

---

### Post by jamesoz91 on 2007-01-15
The sound card is an Intel integrated one, I'm not sure exactly which...
The only problem is with MP3 coding. Everything else appears to be fine.

@"pay"
I couldn't find any package called "gstreamer-mad"....

---

### Post by killernurd on 2007-01-17
You'll need to enable the 'universe' repository before you can install the codecs.

The packages you'll need:
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly

You might also think about installing:
gstreamer0.10-fluendo-mp3


I've been successfully using Amarok for high-quality music for six months now (used XMMS before that :). I've had no troubles with sound quality at all, and I've been broadcasting that music as well with absolutely not problems in quality.

Good luck!

---

### Post by jamesoz91 on 2007-01-18
Thanks for your reply.
I had the first three packages, but not the last one. Still, it made no difference.
Also, I've just noticed a weird thing. After many weeks of all the system clicks and stuff working fine, they've suddenly disappeared.
I'm beginning to give up on sound. ](*,)

---

### Post by killernurd on 2007-01-18
Hrm. That sounds like it's actually a problem with ESD, not with what codecs you've got. You may want to try reinstalling ALSA and ESD.

Also, which distro are you running? I had problems with sound when I upgraded from Dapper to Edgy, and it was because I still had stuff in an ALSA config file that got deprecated.

---

### Post by jamesoz91 on 2007-01-18
I'm using Edgy, but I didn't upgrade it from Dapper, I did a fresh install.
Reinstall ALSA and ESD? How would I do that?

---

### Post by killernurd on 2007-01-18
Ehh... it occurs to me that perhaps you're not running GNOME :)

Anyway, you'll likely want to reinstall ALSA, so fire up your package manager (Adept or Synaptic) and look for these packages:
alsa-base
alsa-utils
libasound2

Mark them for reinstallation. Also, while you're in there, look for the appropriate sound daemon libraries. For GNOME, these are:
esound
gstreamer0.10-esd
libesd-alsa0

For KDE, they are:
gstreamer0.8-artsd
libarts1c2a

For that matter, if you're using KDE, you might want to get libarts1-mpeglib and/or libarts1-xine

---

### Post by jamesoz91 on 2007-01-18
No, no, I'm running GNOME... where did you get that idea from? :) 
Anyway, thanks for your help. I'll go do what you said...
I'm not a heavy user of Synaptic.. didn't know you could just check "Reinstall" lol. Thanks.
I'll post about it afterwards.

---

### Post by jamesoz91 on 2007-01-18
It's certainly made the quality better.. but its not perfect.. if that makes any sense. This is really complex. I will post again once I've done better testing of it. That would be in about 12 hours.

---

### Post by the.ant on 2007-01-18
It might sound stupid, but have you checked your mixer settings?
At my machine, sound gets horrible as soon as PCM goes higher than abnout 70 (of 100). Some programs seem to mess with the settings (don't know about amarok), so take a look at your mixer while playing the MP3. 
(should be kmix if you use KDE (as amarok suggests) don't know about gnome. Else try alsamixer from the terminal.

---

### Post by jamesoz91 on 2007-01-18
After all that... :mad: 
THANK YOU!!!!!
How could I have overlooked that...?
The PCM was right up to 100 when playing music.
Edit: By the way, it was alsamixer.
Problem solved.
Thanks to everyone that helped!

---

### Post by marttali on 2007-01-25
:D 
it helped me too, the sound was awful before that mixer setting changing...

---

### Post by zirconx on 2007-01-25
What is the PCM setting?  I'm a new Ubuntu user and am having problems playing MP3 files.  The sound gets all choppy when I try to do anything else, like surf the web.

---

### Post by killernurd on 2007-01-25
The PCM control handles pretty much all sound you'll get out of your computer, with a very small number of exceptions.

The sound getting choppy is probably 'cause Firefox is attempting to output through ALSA, while whatever you're playing the MP3s through is outputting through either ESD or aRts. My advice would be to set your FIREFOX_DSP environment variable to ESD (for GNOME) or arts (for KDE).

```

tony@lugh:~$ export FIREFOX_DSP="esd"

```

You might also want to add that command to .bash_profile, to ensure it happens every time you log in.

---

