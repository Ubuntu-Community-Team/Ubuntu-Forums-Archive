---
title: "Can't get GNOME volume control to work"
date: 2009-04-16
forum: Multimedia Software
---

### Post by melefire on 2009-04-16
I have changed alot of settings in the Preferences->Sound panal but i cannot get the gnome volume applet to control my volume. I can control it from the terminal via alsamixer but i cant get it to work in the applet. Any ideas?

thanks

---

### Post by Daisuke_Aramaki on 2009-04-16
> **melefire said:**
> I have changed alot of settings in the Preferences->Sound panal but i cannot get the gnome volume applet to control my volume. I can control it from the terminal via alsamixer but i cant get it to work in the applet. Any ideas?

thanks

What Device option are you using in gnome-volume-control applet? If it is hda-intel-alsamixer or something like that it should work

---

### Post by melefire on 2009-04-16
> **Daisuke_Aramaki said:**
> What Device option are you using in gnome-volume-control applet? If it is hda-intel-alsamixer or something like that it should work
hda-intel-alsamixer is not available i am just using the one labeled ALSA at the end

---

### Post by ajgreeny on 2009-04-16
Are you actually using alsa or have you got everything set to pulseaudio?  I use Hardy still and had terrible problems with pulse and applications refusing to work, so went back to alsa.  Everything works properly with that, but I'm sure it's related to hardware; some works well, some doesn't.

Try changing your default sound preferences temporarily to alsa to see if it makes any difference.

---

### Post by melefire on 2009-04-16
I have switched all the audio outputs to ALSA and i then can change the volumes with the advanced volume panel but i still can get that mini applet to work.

---

### Post by melefire on 2009-04-16
Ok i fixed the issue, apparently you change the contoler via right clicking and selecting preferances.

---

