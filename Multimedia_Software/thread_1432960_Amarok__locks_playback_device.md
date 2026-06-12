---
title: "Amarok  locks playback device"
date: 2010-03-18
forum: Multimedia Software
---

### Post by DanielVartanov on 2010-03-18
When Amarok is started, Skype/Audacity/Adobe_Flash stop to see the playback device (it disappears from preferences) and don't play sound.

When I close Amarok, playback device appears again.

What am I doing wrong?

---

### Post by Yellow Pasque on 2010-03-19
You're not doing anything wrong, but I'm guessing that KDE/Phonon apps are using the hardware device by default.

You can try to force Phonon to use the ALSA software mixer by creating an asound.conf file.

```
kdesu kate /etc/asound.conf
```
Copy and paste this:
```
pcm.!default {
  type asym
  playback.pcm {
    type plug
    slave.pcm "dmix:0"
  }
	 
  capture.pcm {
    type plug
    slave.pcm "dsnoop:0"
  }
	 
  hint {
    show on
    description "DMIX"
  }
}
```
Save, quit. Reboot. See how it works. If it's worse, delete the asound.conf file we created and go back to the drawing board.

---

### Post by DanielVartanov on 2010-03-20
Thanks, Temüjin, it helped with Audacity and Flash, but Skype still have "Problem with audio playback". Is it specifically a Skype's issue?

---

