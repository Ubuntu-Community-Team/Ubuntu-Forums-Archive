---
title: "Installing Ubuntu-Desktop breaks sound on Karmic Beta"
date: 2009-10-07
forum: Mythbuntu
---

### Post by Deborah Armstrong on 2009-10-07
yStarting with Mythbuntu Karmic Beta, we used the Mythbuntu control center to add Ubuntu-desktop. This appears to break sound, and I suspect it's another PulseAudio issue. Has anyone found a work-around; a way to have both Mythbuntu and the standard gnome-based Ubuntu desktop running on the same machine?

---

### Post by superm1 on 2009-10-07
This will be properly fixed in the next mythtv upload (there's an upstream bug about it).

For now, launch mythfrontend like this:

PULSE_INTERNAL=1 mythfrontend

---

### Post by sunfire on 2009-10-08
I had same problem with Kubuntu 9.10 BETA (Karmic Koala). No sound with pulseaudio at all. After I removed pulseaudio and rebooted sounds worked with normal alsa. Looks like there is bug in pulseaudio.

---

### Post by superm1 on 2009-10-08
This should be fixed in today's updates of mythtv (r22304 or later)

---

