---
title: "Get sound in center speaker when using Pulseaudio."
date: 2012-07-29
forum: Multimedia Software
---

### Post by ickefes on 2012-07-29
I set up my fathers computer (Ubuntu 11.10) and receiver using [Setup_audio_over_HDMI_on_nVidia_GeForce/nForce_controller]("http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_audio_over_HDMI_on_nVidia_GeForce/nForce_controller") and the mapping using Pulseaudio worked great when using speaker-test but when we play stereo audio there is sound in front l, front r AND front center but no lfe. It works fine when using ALSA where we get front left, front right and lfe.

Can't Pulseaudio understand or be configured to send stereo/two channel audio to only front l, front r and lfe?

Regards.

---

### Post by ickefes on 2012-07-30
bump

---

### Post by kingtiger01 on 2012-07-31
Add disable-remixing = yes to /etc/pulse/daemon.conf

-----

Whats happening in, By default its remixing Stereo Sources to Center and Surround.... this is called Remixing


You can also add "disable-lfe-remixing = yes" as well to disable Low-frequency sound being added to the subwoofer from Stereo Sources.

Press "Alt" and type
```
gksudo gedit /etc/pulse/daemon.conf
```

then add ```
disable-remixing = yes
``` to the bottom of it

---

### Post by ickefes on 2012-08-03
Thank you kingtiger01. I will try this and get back to you how it goes. Regards.

---

### Post by ickefes on 2012-08-03
I tried adding
```
disable-remixing = yes
``` which helped by getting rid of sound coming from the center speaker but the sound from the LFE also disappeared which is a problem. I am half way there at least! Regards.

---

### Post by kingtiger01 on 2012-10-21
Sorry ive been busy...

PulseAudio has Alot of Benifits but many Limitations...

Make sure you add *IN THIS ORDER* to youre Global configuration^^^

-------------------------------------------
enable-lfe-remixing = yes
enable-remixing = yes
default-sample-channels=2
-------------------------------------------

What this does is, enable Subwoofer, and limits speaker remixing to JUST the front 2 speakers...
Its kinda borked though... Some times it will refuse to work, but give it a shot!

---

