---
title: "pulse-module-lirc"
date: 2011-10-15
forum: Multimedia Software
---

### Post by Krister Hallergard on 2011-10-15
I have just upgraded very successfully from 11.04 to 11.10.  My only problem is that pulse-module-lirc does not work any more (yes, as before I have added the line "load-module module-lirc" to /etc/pulse/default.pa).  Use this to mute or control volume on websites with flash video.  Help, please!

---

### Post by Krister Hallergard on 2011-11-04
Found that it worked sometimes, but usually not, at least not at boot.  Was not able to work out why it sometimes worked.

I could kill pulse with "pulseaudio --kill" but could not restart pulse with "pulseaudio --start".  But I noticed that if after the kill  I restarted Firefox and the flash video, there was sound and the lirc command "mute-toggle" worked!  So it seems that pulse was restarted.

So I put the script "pulseaudio -kill" in with the autostart scripts, and it now works all the time.

---

