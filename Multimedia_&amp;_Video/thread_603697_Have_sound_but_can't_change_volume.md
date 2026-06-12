---
title: "Have sound but can't change volume"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by theknowledgeist on 2007-11-05
Hello,

I have sound on my computer, but when I move the volume slider in the upper right hand corner, the volume doesn't change. Similarly, when I move the volume wheel on my keyboard, the speaker icon pops up in the center of the screen and the volume meter changes, but the actual sound does not change. I think I am stuck in the highest volume mode.

However, the volume sliders within applications like Songbird and VLC Media Player do work. 

I have gone into the Sound control panel and tried every possible option in the drop-down menus for how to control sound playback to no avail.

I have Ubuntu 7.10 and a Soundblaster Audigy SE soundcard. 

Any advice? Thanks.

---

### Post by logos34 on 2007-11-05
I had to reset mine just the other day.  Here's what I did:

System>Prefs>Sound>click 'Default mixer tracks'>device: 'Intel ICH (Alsa mixer)'> highlight 'Master' in box below.

---

### Post by theknowledgeist on 2007-11-05
Outstanding, that fixed the problem. Thanks!

---

### Post by Linuxratty on 2007-11-05
What do you do if there is no "master" selection in the box below? I have the same problem of sound being too low,even though my speakers are at full blast.

---

### Post by Not on 2007-11-07
I just registered as a user just so I could respond ... 

I'm a Kubuntu user, but had a problem where even though I could change volume levels with my various media applications the base level was very low (I had to have it maxed out, and then my speakers nearly maxed out too).

I struggled to find any GUI methods for changing the settings so i decided to change the settings more directly. So I was running through all the alsa related packages in aptitude when I saw a really interesting one included in alsa-utils (installed by default), called alsamixer.

This app is launched in your konsole/shell by simply typing alsamixer, and it gives you a mixer right there in the commandline. Left and right arrows change the slider you're changinging, while up and down change the level.

Try increasing the master slider. Since I am only using two channel speakers I also pushed the front channel up.

Hope it works

---

### Post by Not on 2007-11-07
Ok,

So it seems like I'm a bit of an idiot - I found the KDE GUI to change the alsa settings, its called KMix, nevertheless, the alsamixer app should work in any X environment, including the standard Gnome.

---

