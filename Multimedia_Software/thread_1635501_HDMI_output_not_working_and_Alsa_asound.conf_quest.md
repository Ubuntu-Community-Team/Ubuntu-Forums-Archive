---
title: "HDMI output not working and Alsa asound.conf question"
date: 2010-12-01
forum: Multimedia Software
---

### Post by excetara2 on 2010-12-01
I've tried to get HDMI output working but with all my might I can't seem to figure out what to do so resorting for help here. I have a Dell Studio XPS 16 with a ati mobility radeon 565v (same as HD 4670 card). I've attached my alsa-info script here.

[http://www.alsa-project.org/db/?f=cef173e3411e4411d20855d94913f8e2ed9fb665](http://www.alsa-project.org/db/?f=cef173e3411e4411d20855d94913f8e2ed9fb665)


Also I had to add this in to get sound to come out of browsers while flash is playing but I'm not sure why. This used to work fine but all the fiddling with the sound messed something up. This I assume just says set pulse the default for all sound types. Any known issues with this or just this got axed from somewhere else on my tries at getting HDMI going:

> !!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)

pcm.pulse {
type pulse
}
ctl.pulse {
type pulse
}
pcm.!default {
type pulse
}
ctl.!default {
type pulse
}




Cheers for any help,

Jeff

---

### Post by lidex on 2010-12-02
First check that spdif channels are not muted. You can use alsamixer in terminal or gnome-alsamixer gui.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

