---
title: "Getting A SoundBlaster Live to work ?"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Borg on 2007-11-01
Anyone know how I can get output from more than just the 'stereo' jack on this card please ?

Running Gutsy

---

### Post by srg84 on 2007-11-01
Put this in /home/USER/.asoundrc

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

---

### Post by KrIaXPaTaLa on 2007-11-02
How do you control the volume on the applications after creating this file?

Regards.

EDIT: ok, xmms's done. Also vlc. And also gnome mixer. Xine is the only one still remanin, it refuses to set more then just one alsa mixer (and right now Im using 3: surround, center and LFE). Also, how can u mute the sound?

EDIT2: all done. the setting for software controled sound in xine is NOT in the audio section, but gui :|

---

