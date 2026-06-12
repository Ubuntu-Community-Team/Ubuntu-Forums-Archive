---
title: "Sound / Volume Control for Compaq V3136TU laptop"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by in_flu_ence on 2008-01-18
I have a compaq v3136tu laptop with a  Conexant CX20551 codec. However, It seems that my volume control buttons on my lappie is not able to control the volume. In my volume control, my sound is controlled by PCM-2 while my buttons are changing the headphone volume.

I tried to use the preference to control both the headphone/PCM-2 at the same time but things doesn't improve 'cause the buttons still are controlling just the headphone.

I have tried to install alsa-driver 1.0.15 but I am not sure if I have done a proper job. Is there a way to check?

Of course any help in this issue will be appreciated.

Thanks

---

### Post by Metaljaz on 2008-01-19
Try going to System>Preferences>Sound>Default Mixer Tracks and make sure "Master" is selected.

---

### Post by in_flu_ence on 2008-01-20
Cool. It works. It seems that the volume applet is not linked to the Sound option in preference. So it might be something that someone has to look into it in future.

Not sure if this is considered a bug.

---

