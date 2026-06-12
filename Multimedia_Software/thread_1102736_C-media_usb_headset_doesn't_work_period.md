---
title: "C-media usb headset doesn't work period"
date: 2009-03-22
forum: Multimedia Software
---

### Post by SonnHalter on 2009-03-22
I've looked around but can't find any help with how to get my head set to work. it works great in windows.

it works when i test it in gnome sound settings but online the audio doesn't play. help?

---

### Post by markbuntu on 2009-03-22
I have a C-media USB headset which is partly why I wrote this post:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by SonnHalter on 2009-03-22
Firefox still wont' use the headset. I think because its playing through "firefox ALSA plugin"

and what should be my device in main volume control?

---

### Post by SonnHalter on 2009-03-23
bumpp

---

### Post by markbuntu on 2009-03-23
As in the link I gave earlier, you should set your System/Preferences/Sound so firefox uses pulseaudio instead of alsa or oss-alsa. Then you can use pavucontrol, the Pulseaudio Volume Control to direct the firefox stream to your usb headset once something is playing. You can control the master volumes of the devices and the volume of the streams in pavucontrol. It is not really important which one is in the gnome volume control. Just make sure they are turned up.

---

