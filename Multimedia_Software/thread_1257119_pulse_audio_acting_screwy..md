---
title: "pulse audio acting screwy."
date: 2009-09-03
forum: Multimedia Software
---

### Post by suffer1989 on 2009-09-03
Just when i got pulseaudio working perfectly, it starts acting screwy. I cant access the volume controll, it starts, then immediatly crashes.

> sufy@sufy-laptop:~$ pavucontrol
/home/sufy/.themes/UbuntuStudio/gtk-2.0/gtkrc:77: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/home/sufy/.themes/UbuntuStudio/gtk-2.0/gtkrc:213: Unable to locate image file in pixmap_path: "panel.png"
/usr/share/themes/Human/gtk-2.0/gtkrc:263: Invalid symbolic color 'tooltip_fg_color'
/usr/share/themes/Human/gtk-2.0/gtkrc:263: error: invalid identifier `tooltip_fg_color', expected valid identifier
**
ERROR:pavucontrol.cc:473:void StreamWidget::setVolume(const pa_cvolume&, bool): assertion failed: (v.channels == channelMap.channels)
Aborted


The Colon P above got converted to :p

---

### Post by suffer1989 on 2009-09-04
Bamp ?

---

### Post by Quake on 2009-09-04
Sorry if I don't help you here but my take: pulseaudio is a virus. I removed it and I no longer have a problem with sound.

---

### Post by jacksenechal on 2009-09-24
I'm having the same problem. It all happened after I upgraded to the PulseAudio edition of Skype. I have no idea if that is related. 

I can get it working by killing pulseaudio with ```
killall pulseaudio
``` and then letting it respawn when there is another audio request. After that pavucontrol works great.

---

