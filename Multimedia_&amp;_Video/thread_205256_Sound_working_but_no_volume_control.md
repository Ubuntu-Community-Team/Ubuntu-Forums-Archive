---
title: "Sound working but no volume control"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by Flavian on 2006-06-28
Hi guys! Maybe someone can help me with this.
I got the sound wo work on my Soundcard, BUT the only way to control the volume is by turning down the volume via the software panel.

The hardware control wheel on the side of my laptop, does not change ANYTHING!
I have no idea why, maybe someone can help me with this...

Flo

---

### Post by LordRaiden on 2006-06-28
I don't know if this will work, so I'll just make you do the initial step.

Go to a shell and type ```
xev
```

Now move your volume wheel in  the volume up direction then write down the keycode.

Then, move your volume wheel in  the volume down direction then write down the keycode.

Do not mix the keycodes. The initial step wold be to check if you get keycodes at all. If not it, post the manufacturer and model # of your laptop, and maybe someone with a similar laptop can help.

---

### Post by Flavian on 2006-06-28
Thanks Lord Raiden.
But, nope I don't get any keyvalues :(
It just doesn't happen...
My Laptop is a "Fujitsu Siemens Amilo M1437G" which afaik from my North American Friends, is not quiet widespread in North America... :/

Could it be that the sound does not run over the soundcard, but directly through the output? (That's what my friend suggested) I can not believe it, because the sound is not different than the sound in Windows...

Thanks in advance!
Flo

---

### Post by LordRaiden on 2006-06-28
It could be GNOME setting or a soundcard setting, hard to tell from my end.

Do this in the shell: ```
aplay -l 
``` That should give you the name and driver of your soundcard. Maybe something can done with that.

---

### Post by Flavian on 2006-06-29
Here's the output:
(Hope someone can help)

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by LordRaiden on 2006-06-29
Have a look at this.

[http://forums.suselinuxsupport.de/lofiversion/index.php/t10746.html]("http://forums.suselinuxsupport.de/lofiversion/index.php/t10746.html")

 If it works, please state exactly how you (not the post) fixed the problem.

---

