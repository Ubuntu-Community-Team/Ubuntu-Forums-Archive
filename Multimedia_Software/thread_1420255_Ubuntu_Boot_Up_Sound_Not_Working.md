---
title: "Ubuntu Boot Up Sound Not Working"
date: 2010-03-02
forum: Multimedia Software
---

### Post by emagine on 2010-03-02
Hello everyone,

I recently noticed that when I boot up ubuntu it no longer plays the cool startup music. I think it may have something to do with me removing these packages in synaptic package manager because they were interferring with my sound in total annihilation for spring. Most of the packages below were reinstalled because my sound icon disappeared and I had to reinstall them. But are any one of these packages responsible for the ubuntu boot up sound?

gstreamer0.10-pulseaudio
libcanberra-pulse
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-bluetooth
pulseaudio-module-gconf
pulseaudio-module-udev
pulseaudio-module-x11
pulseaudio-utils
ubuntu-desktop

Thank you.

---

### Post by emagine on 2010-03-03
I figured out the problem.  It did not have to do with the packages.  All I had to do was right click the sound icon in the top right and go to sound preferences.  From there, under sound effects I unmuted the alert volume and confirmed that ubuntu was the default sound theme.

---

