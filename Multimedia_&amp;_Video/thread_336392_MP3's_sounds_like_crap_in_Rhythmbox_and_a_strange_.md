---
title: "MP3's sounds like crap in Rhythmbox and a strange clicking"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by Grog140 on 2007-01-11
I have a few MP3 files in my rhythmbox library and they sound terrible compared with my ogg files. In addition, they sounds great in totem player.

So that is the most annoying problem.

The next problem is less noticeable. While playing music files with any media player there is a strange clicking that happens every 20 seconds or so. Not with any video files I have tried playing though! It is quiet but driving me insane. Could anyone help?  

Thanks

EDIT: Switching totem-xine to totem-gstreamer makes the mp3 files sound bad in totem player as well.
That narrows things down, I just don't know how to fix it.

Also, the clicking doesn't happen in any video format except MP4 I found out.

---

### Post by imon9 on 2007-01-17
i am not 100% positive this can help, but uninstall your mixer software and installing other one might help...in my case, i have a Realtek AC 97 soundcard build-in with my twinhead laptop (nevermind if u never heard of it)....as i was saying, i tried ALSAmixer, xfce-mixer, gnome mixer but all somund bad, but when i changed to QAMix, all went to nice normal sound, go try your luck...

my mic however is currently not functional after changing mixer, so be aware of the possible problem with mic recoding for now..

if this workes,  please post a reply..and if it is not too much of toruble, please private massage me too...

i cant keep track where i answer these treads in the forums, so i can't check back wether it is working, but if this solve the problem, i want to write an article for the rest fo the ubuntu commmunity to know it... (and port it in the forum, in hope it can help others)

---

### Post by imon9 on 2007-01-17
i update ALSA and the mic start working flawlessly. Previously, with other mixer, my mic will be hard over my speaker ALL THE TIME no matter how i set to mute it.

Now, it record my sound, but will not echo it over the speaker which is PERFECT.

so, i think changing Mixer software INDEED wll help to fix those bad quality sound...

For other who it didn;t solve it, try update your ALSA driver to the later ones (ALSA 14 RC2, at this moment) and use ALSA instead of OSS or other mechanism for playback... ESD is old sound driver, so it might be the cause of problem if ur machine use it as default

---

### Post by pertti on 2007-01-19
You could also check if you have the 'gstreamer0.10-fluendo-mp3' package installed. This decoder was also giving me bad sound quality with some (but not all) of my MP3s, due to some bug. Try uninstalling it, install the 'gstreamer0.10-plugins-ugly' package (i'm not sure if it is this one, or the multiverse one) if it's not already, and see if the problem is still there in Totem and Rhythmbox.

---

### Post by cinnix on 2007-01-20
Hey guys, I'm also getting the "clicking" when playing mp3 files (in any player). I'm new to ubuntu and installed it single-boot the other day (byebye Windows :), so if anyone can spell out to me what I should do, or post some guides and whatnot... it will be much appreciated.

Thanks in Advance.

edit: I have an nForce 4 chipset, intergrated audio which could possibly be 5.1, but I will be more than happy with just stereo.

Edit 2: Just uninstalled gstreamer0.10-fluendo-mp3 and the clipping/clicking has gone. Upon further research it is also apparently unresolved issue with variable bitrate mp3 files.

---

