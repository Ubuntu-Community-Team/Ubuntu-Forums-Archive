---
title: "No sound after starting alsa-utils."
date: 2009-06-01
forum: Multimedia Software
---

### Post by phreaknite on 2009-06-01
I recently wanted to change my default "mute-on-startup".  I found that others solved this problem by turning on Audio Setting Management in System->Administration->Services.  When I did this it killed my sound....permanently.  Even when I turn off Audio Settings Management the sound no longer works.

I currently use ALSA 1.0.19 with PulseAudio.  It worked just fine before I ran alsa-utils through Audio Settings Management.

Is there anything I can do?  Is there more information that is needed?

---

### Post by dano1 on 2009-06-02
curious also...

---

### Post by phreaknite on 2009-06-04
This turned out to be a nightmarish 7 hour fight with my sound.

It turns out that alsa-utils script was broken...or something to that effect.  I updated to the latest ALSA drivers (1.0.20 from 1.0.19) only because it was better than just reinstalling the old driver.  When I did that I still had no sound.  I then killed pulseaudio and realized the PulseAudio app was blocking all my sound.

After a long struggle of uninstalling and reinstalling pulseaudio i finally realized that my device chooser somehow got set to HDA INTEL **HDMI** as the default output for my sound card where it should have been HDA INTEL.  As soon as I fixed that my sound worked fine.

I have not tried to run alsa-utils again for fear of going through the same process.  Now I just deal with my computer starting up muted and unmuting it!

---

