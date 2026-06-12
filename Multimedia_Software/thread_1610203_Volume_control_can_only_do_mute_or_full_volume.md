---
title: "Volume control can only do mute or full volume"
date: 2010-10-31
forum: Multimedia Software
---

### Post by viki__ on 2010-10-31
Hi All,

I am struggling with a problem with the volume control... when i try to adjust the volume with the sliding bar i can not do it. If i put the scrollbar to the 0 position, it is muted. when i move it to anywhere else, i get the full volume. From other programs like vlc, i can adjust the volume with no problem.
Can anybody help me how to get it working?

Thanks

---

### Post by jaygo on 2010-11-08
I just ran into this myself a few days ago. Not sure what caused it as volume control was working normally for years. Now, when I adjust the system volume (with keyboard, system tray icon, or Sound Preferences window) I can see the slider going up and down but it does not change the volume. Alsamixer has the same result.

The only change I know of was adding a logitech webcam (with mic). I removed that and restarted pulseaudio with no change.

onboard Intel (Realtek ALC888) with optical out
Ubuntu 10.10

---

### Post by jaygo on 2010-11-08
Alright, just fixed it.

After removing my webcam & restarting pulseaudio, there were new options in Sound Preferences > Hardware.

For me, because I use optical out, I needed to have the system volume adjust the digital (PCM) level, rather than the analog levels which don't have anything connected.

[LIST=1]
[*]Sound Preferences > Hardware tab (click on volume icon or go to system > preferences > )
[*]change profile to "Digital Stereo ..."
[*]if you don't see "Digital Stereo ..." options, try removing any other sound devices that are listed on the hardware tab.
[/LIST]

---

