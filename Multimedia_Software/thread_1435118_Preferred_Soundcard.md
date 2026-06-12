---
title: "Preferred Soundcard"
date: 2010-03-21
forum: Multimedia Software
---

### Post by oppigard on 2010-03-21
Hi

Im running Ubuntu 9.10 on my Fujitsu Siemens laptop (M3438g)
I recently bought a [Logitech N700]("http://www.logitech.com/index.cfm/notebook_products/cooling_pads/devices/6394&cl=gb,en?WT.mc_id=amr_tai_redirect_012010_news-N700") (Lapdesk speakers with cooling)
My problem in ubuntu is that when I start ubuntu, the mute-light on the n700 is on, and there is no sound.
I can click the mute button on the n700 and it reacts in ubuntu, but the mute light on n700 is still on, and I can adjust the volume on the n700, which changes the volume in ubuntu.
After I fiddle with the audio device settings, I get sound, but its kind of tricky, I have to change it to usb device, change it back to internal and back. and often change channel.

I have tried [this guide]("https://help.ubuntu.com/community/SoundTroubleshooting#Configuring%20default%20soundcards%20/%20stopping%20soundcards%20from%20switching"), but with no luck.
Although now I get:
```
$ cat /proc/asound/modules
 0 snd_usb_audio
 1 snd_hda_intel

```

Edit: When I get into gnome, and check the audio device settings, the selected device is the internal, so apparently the editing of alsa config did not work!

---

