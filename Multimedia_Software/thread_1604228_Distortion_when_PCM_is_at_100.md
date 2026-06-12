---
title: "Distortion when PCM is at 100"
date: 2010-10-23
forum: Multimedia Software
---

### Post by chrisinspace on 2010-10-23
I am using Kubuntu 10.10 and having a sound issue.  I fully installed PulseAudio so that I could properly enable the 5.1 sound on my system.  At some volume levels it sounds great, while at others it has a terrible metallic-sounding distortion.  I have worked with the various audio tools I have installed and narrowed down the problem.

Here is what I have installed to configure sound settings: kmix (KDE equivalent of gnome-volume-manager), pavucontrol, alsamixer.

I have found that when I adjust the master volume level through kmix (either with the GUI slider or the volume control keys on my keyboard), the levels in alsamixer all change, too, not just the Master level.  When PCM maxes out at 100, I get the distortion, but if it is at 99 or lower, everything sounds perfect.  The weird thing is that as I adjust the master volume level, the PCM level bounces between 98 and 100.  Like this:

[CENTER]_Master_     _PCM_

23.....100
35.....98
42.....100
52.....98
58.....98
61.....100
68.....98
74.....98
78+....100[/CENTER]

Is there any way to lock the PCM level or cap it at 99?  If I can keep the PCM from hitting 100, I can get rid of the distortion.  I would greatly appreciate anyone's help.

---

### Post by chrisinspace on 2010-10-25
So, I got a suggestion to look at the /etc/alsa.state file.  Does anyone know anything about this?

Have any other members experienced a similar problem?  I had this same issue in 10.04, but I didn't have time to troubleshoot it, so I bypassed the surround-sound speakers and used my TV's speakers.  When 10.10 came out I rebuilt the machine and I really want to get everything set up correctly.  I just need to prevent alsa from maxing out the PCM.

---

### Post by chrisinspace on 2010-10-29
I've been stuck on this issue for almost a week now.  Can anyone help me out?  I would like to accomplish any 1 of 3 things:

1. Lock the PCM channel so it doesn't change when I adjust the main volume.

2. Cap the maximum PCM level at 99 or below.

3. Set it up so that kmix controls the PCM volume instead of the master.

Is anyone else having this issue? I read about a [similar problem at KDE.org]("http://forum.kde.org/viewtopic.php?f=19&t=82804&start=10"), but there wasn't a solution that worked for me.

---

### Post by chrisinspace on 2010-11-02
Well, in case anyone else is having this issue, I eventually found a work around on another forum (Thanks, Mandriva). If you kill kmix, then run the command

```
KMIX_PULSEAUDIO_DISABLE=1 kmix 
```

you will be able to select the master channel.  I selected PCM.  That allows me to control the system volume with the PCM slider, preventing it from jumping to 100.  I just never set the volume above 99.  The change reverts if I reboot the machine, so the next step will be to set it that way at bootup, but I haven't gotten there yet.  I'll update this when I figure that out, but it's not super-high on my priority list since I don't reboot this machine very often.

---

