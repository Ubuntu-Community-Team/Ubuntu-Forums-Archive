---
title: "Line-in port in PulseAudio"
date: 2009-10-28
forum: Multimedia Software
---

### Post by celtic426 on 2009-10-28
I'm trying to allow my Line-In port to be recognized and played thru my speakers.  In previous Ubuntu and most other linux distros, I could do this easily with ALSA.  All I had to do was open the sound mixer and the line-in port was right there, I just had to unmute it or turn the volume up.  I can't find anything like that in pulse and I have found little documentation online for configuring pulse.  Could anyone help me, thanks.

---

### Post by markbuntu on 2009-10-28
You should install gnome alsa mixer. It will give you finer control of your sound hardware than the volume control.

---

### Post by celtic426 on 2009-10-28
> **markbuntu said:**
> You should install gnome alsa mixer. It will give you finer control of your sound hardware than the volume control.


Do I have to remove the pulse one?  And if I set the settings in Alsa and then quit the mixer, will the settings stay?  Also, should I have Alsa start up automatically?  Should I just completely remove pulse and replace it with Alsa?

---

### Post by markbuntu on 2009-10-29
No, you do not need to remove pulseaudio. The gnome alsa mixer will appear in your menus. Changes made in the gnome alsa mixer will change the same settings in the other volume controls. The different volume controls all control the same stuff it is just that the gnome alsa mixer exposes more of the controls.

---

