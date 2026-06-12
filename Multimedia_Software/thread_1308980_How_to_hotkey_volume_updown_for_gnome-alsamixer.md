---
title: "How to hotkey volume up/down for gnome-alsamixer"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Darvenkry on 2009-11-01
I would like to hotkey gnome-alsamixer to control my systems volume. How can i create a hotkey for volume up (using MASTER channel). This is a workaround for pulseaudio. Had to uninstall it cos it was creating this loud static for all my songs. Now using ALSA, but gnome-volume-control does not work. Thus using gnome-alsamixer. Just need to recreate hotkeys for system. Cheers

---

### Post by OrangeVixen on 2009-11-01
No sure if this is overly obvious or I missed something, but when I wanted to control the volume using the volume keys on the keyboard, I went to System->Preferences->Sounds and on the Devices tab there is the Default Mixer Tracks and a popup list that says Device: in which I selected ALSA Mixer.

You can change that and don't forget to select at least one mixer channel in the list below it before clicking Close. Hope I didn't misunderstand the question.

---

### Post by Darvenkry on 2009-11-01
Well there doesnt seem to be Preferences->Sound anymore in Karmic Koala (which i updated to the other day). Any other ways to select which mixer I use? Because all the keyboard shortcuts are set for volume up and volume down in Preferences->KeyBoard Shortcuts. However nothing happens for volume up/down because gnome-volume-control is broken. I get the nice message of "Waiting for sound system to respond" when I try open Volume Control. Thus i would like to use gnome-alsamixer to control sound volume. How do i link the mixer to my shortcuts?

---

### Post by kerry_s on 2009-11-01
> **Darvenkry said:**
> I would like to hotkey gnome-alsamixer to control my systems volume. How can i create a hotkey for volume up (using MASTER channel). This is a workaround for pulseaudio. Had to uninstall it cos it was creating this loud static for all my songs. Now using ALSA, but gnome-volume-control does not work. Thus using gnome-alsamixer. Just need to recreate hotkeys for system. Cheers


you mean you just need the commands?
```

amixer set Master 3+ unmute
amixer set Master 3- unmute
amixer set Master toggle

```

---

### Post by Darvenkry on 2009-11-02
Thx Alot, I put all the commands into Keyboard Shortcuts, and I can now control my sound with hotkeys. Too bad no cool graphic of my volume slider comes up when i press the hotkeys like it usually does with gnome-volume-control, but no matter.

---

### Post by Snyder.4000 on 2010-07-02
I was looking for this too, thank you [kerry_s]("http://ubuntuforums.org/member.php?u=132335") it was very usefull

---

