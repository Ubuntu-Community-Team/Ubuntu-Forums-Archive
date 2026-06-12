---
title: "[SOLVED] Skype not working anymore"
date: 2008-10-08
forum: Multimedia Software
---

### Post by feydrutha on 2008-10-08
I am using ubuntu hardy, and had skype successfully installed from the medibuntu repository, using the skype-static package.

Yesterday (or the day before?) skype stopped working (I assume because of some update) and gave a "problem with audio playback" error in the GUI when trying to make a call. Flash plugins in firefox also stopped working but I fixed that by installing libflashsupport.

I have now followed [this]("http://ubuntuforums.org/showthread.php?t=843012&highlight=skype") guide, and I don't get that error anymore, but there is no sound in skype.

Specifically, I installed all the packages required by the guide above, checked all possible volume controls (alsamixer-gtk, pulseaudio volume control, and the normal volume control applet), and edited ~/.asoundrc as suggested.

I get sound from all other applications, it gets mixed properly, but no sound in skype. Also in the pulse audio volume control I see a skype stream appearing when I start skype, labeled "ALSA plug-in [skype]: ALSA Playback" (which is Mono).

If I use skype-static-oss (and then launch skype with "padsp skype") I get sound, but it crackles a lot and is bad enough to be unusable.

Just wasted most of my workday on this. Anyone have any suggestions?

---

### Post by markbuntu on 2008-10-08
Did you do this part of the guide for Skype, it may have been missing when you tried it before and should fix the crackling:

If you find the sound stuttering etc, you can edit the /etc/pulse/daemon.conf file. At the end of the file are two lines like this:
```

;default-fragments = 5
;default-fragment-size-msec = 25

```
Change them to look like this :
```

default-fragments = 8
default-fragment-size-msec = 5

```
Save the file and restart Pulse Audio which you do in a terminal:

killall pulseaudio

pulseaudio -D

Also, use the skype-static package, not the skype-static-oss one.

---

### Post by feydrutha on 2008-10-09
Worked! thanks a lot! I wasn't really expecting this to work, since with skype-static I had no sound at all, not the crackle problem.

I had not tried those values, but a similar edit to /etc/pulse/daemon.conf which was suggested in [this]("http://ubuntuforums.org/showthread.php?p=4928900") thread:

high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
default-fragments = 8
default-fragment-size-msec = 5
resample-method = speex-float-0

But this had made my sound crackle even with rythmbox, and not caused any output to come out of skype. I had also already edited .asoundrc as in [your thread]("http://ubuntuforums.org/showthread.php?t=937323").

So in conclusion, for anyone who has the same problem try to:

Follow [this guide]("http://ubuntuforums.org/showthread.php?t=843012&highlight=skype") to get overall sound to work good. This also gets you the pulseaudio volume control, which allows you to control volume of individual applications, and even send output from each stream to a different output device if you have more than one.

And do [this skype fix]("http://ubuntuforums.org/showthread.php?t=937323").

---

