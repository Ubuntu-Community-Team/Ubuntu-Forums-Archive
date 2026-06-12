---
title: "Asus - nVidia Geforce 210 - HDMI audio complete"
date: 2012-08-10
forum: Multimedia Software
---

### Post by Axess_Denied on 2012-08-10
I have referred to the thread here: [Asus nVidia discussion]("http://ubuntuforums.org/showthread.php?t=1317408")

I now have the following audio through HDMI working on boot:

Banshee
System Notifications

I can test sounds in terminal

```
aplay *test.wav*
```

However, using Google Chrome, I can not get audio?

Ubuntu 11.10 64-bit
Asus M4A875TD-evo
Asus Geforce 210

Any help?

---

### Post by Axess_Denied on 2012-08-11
Found the solution [here]("http://ubuntuforums.org/showthread.php?t=1317408&page=4"): page 4, post 31.

The idea is to first create/modify **/etc/modprobe.d/alsa-base.conf** by adding:

```
options snd-hda-intel probe_mask=0xfff2
```

I did this because I had already disabled onboard HDMI audio through BIOS and was only able to see the NVidia card in Terminal using:

```
aplayer -l
```

These steps allow me to see only the NVidia card listed under "output" tab in Sound Preferences.

To get audio working for Banshee, System Sounds and in FLV (Chrome and Firefox) I created/modified the file **/etc/asound.conf** with the following:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

Reboot the system and done.

---

