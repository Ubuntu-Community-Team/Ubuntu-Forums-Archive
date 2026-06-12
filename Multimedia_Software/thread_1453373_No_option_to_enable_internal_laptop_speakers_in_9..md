---
title: "No option to enable internal laptop speakers in 9.10"
date: 2010-04-13
forum: Multimedia Software
---

### Post by richwillal on 2010-04-13
In Hardy and Intrepid, I could use the sound preferences applet to select "Line in as output" which for the HDX9300 would enable the internal laptop speakers in addition to the external 5.1/7.1 speaker jacks.  Now that the PulseAudio changes and the sound controls are updated, that's no longer an option.  Has anyone solved this problem yet?

Currently the external speakers work perfectly, and the headphone jacks correctly mute the external speakers when used.  The only change required for that was to set the option in /etc/modprobe.d/alsa-base.conf forcing the model.

Thanks

---

