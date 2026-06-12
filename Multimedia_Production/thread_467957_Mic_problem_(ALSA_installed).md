---
title: "Mic problem (ALSA installed)"
date: 2007-06-08
forum: Multimedia Production
---

### Post by malfist on 2007-06-08
I couldn't do anything with my mic until I installed ALSA and now when I talk into the mic it comes back out my speakers, but none of the applications can capture it, not Sound Recorder, not Audacity. Any ideas how to fix this?

I just set up this computer with the new Ubuntu 7.04

Edit: it works in Skype

---

### Post by nerubian on 2007-06-09
did you turn "capture" on in input of mixer settings (system tray)?
or you can turn capture on by typing
```

alsamixer -V capture

``` 

then u can increase capture level.try this it helped me.

---

### Post by malfist on 2007-06-09
Yes, capture is on on all of them.

---

### Post by nalmeth on 2007-06-10
Go into the preferences in Audacity, and make sure the right device is selected.

Also, go into the gnome-mixer and make sure the right input device is being used. You may have a webcam mic that has taken priority, or something similar

If the problem still isn't solved, report back to that effect

---

### Post by malfist on 2007-06-10
That fixed the Audacity one, it was trying to use OSS instead of the C-Media PCI card with ALSA (I plan on replacing the card though, it's crap).

Thanks.

---

### Post by nalmeth on 2007-06-10
Glad I could help

---

### Post by mpneerkaje on 2007-06-30
> **nalmeth said:**
> Go into the preferences in Audacity, and make sure the right device is selected.

Also, go into the gnome-mixer and make sure the right input device is being used. You may have a webcam mic that has taken priority, or something similar

If the problem still isn't solved, report back to that effect

By the way, where do I find gnome-mixer? I couldn't find it anywhere.
I too have the same problem, i'm using Nvidia HDA sound device. In Audacity, I'm not able to see the second device(AD198X Digital (hw:0,1)) in recording device drop down button, where as its available for playback. In windows i use this second device for recordnig.

---

### Post by malfist on 2007-07-02
The GNOME-Mixer is the sound icon in the system tray.

---

