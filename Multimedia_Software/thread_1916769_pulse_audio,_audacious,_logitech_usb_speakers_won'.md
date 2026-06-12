---
title: "pulse audio, audacious, logitech usb speakers won't work"
date: 2012-01-28
forum: Multimedia Software
---

### Post by pandalolwut on 2012-01-28
I'm using audacious on lubuntu, and my logitech usb s-00041 won't work. Before I installed pulse audio, I just used the ALSA output plugin, and went into output plugin preferences to change it to my speakers, which worked. 
Any help would be appreciated. Sorry for asking what may be an obvious question, I'm relatively new to linux.

---

### Post by ajgreeny on 2012-01-28
Make sure you have all the necessary pulseaudio packages installed, including **pavucontrol** and **padevchooser**, the first of which can be very helpful in setting volume levels of various devices, and the second occasionally can make things magically start working without actually doing anything with it, if I remember correctly from the first version of ubuntu that used pa.

Open pulseaudio volume control first and play with the settings in that.  If still no joy, come back again and tell us what you tried.

You can still run alsamixer, or install gnome-alsamixer and use it for added control of levels and devices.

---

### Post by pandalolwut on 2012-01-29
:D, so all I did was turn off the internal audio in the volume control and it worked. Thank you so much.

---

### Post by ajgreeny on 2012-01-29
My pleasure.

Please mark as SOLVED from the thread menu at the top of the thread

---

