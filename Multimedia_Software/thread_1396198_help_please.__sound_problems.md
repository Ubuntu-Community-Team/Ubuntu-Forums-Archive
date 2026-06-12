---
title: "help please.  sound problems"
date: 2010-02-01
forum: Multimedia Software
---

### Post by skn332 on 2010-02-01
I have recently installed Karmic and i have sound problems.  I did a clean installation.  Sound works in everything but flash programs(online streaming) and vlc. Amarok works fine and so does the dragon video player. .  I am running the sound through my video card which is an ati radeon 4890 hd.  it is being run through the hdmi cable from the video card to the tv.  i have uninstalled and installed flash player.  i have tried running just alsa with no pulse audio and and i have tried with pulse audio.  i have searched the forums for days but nothing seems to work.  any help would be nice.

---

### Post by VertexPusher on 2010-02-02
Make sure that libflashsupport is not installed. The Flash plugin uses ALSA, but libflashsupport will route its audio into Esound or OSS instead. OSS does not support sound card sharing, i.e. Flash will not be able to play back audio while any other application uses the sound card. Esound is basically dead.

In Ubuntu 9.10, libflashsupport comes with the package "flashplugin-nonfree-extrasound". If that package shows up as installed in Synaptic, remove it.

---

### Post by skn332 on 2010-02-02
neither one of those packages is installed.  still no sound.

---

