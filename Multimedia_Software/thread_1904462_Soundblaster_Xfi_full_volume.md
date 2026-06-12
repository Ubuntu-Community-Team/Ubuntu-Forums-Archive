---
title: "Soundblaster Xfi full volume"
date: 2012-01-04
forum: Multimedia Software
---

### Post by pingvin on 2012-01-04
Situation:
Ubuntu 10.04 (Lucid Lynx)
ALSA 1.0.21
Soundblaster Xfi 5.1 USB sound card

Problem 1:
USB sound card is always set to full volume by default (at start-up, after sleep etc.)

Problem 2:
gnome-volume-control reverts control to the internal (in my case, HDA Intel) sound card after sleep.

Solution:
Install pavucontrol (Pulse Audio Volume Control) and in the configuration tab, change the internal card to "Analog stereo **input**". Then make a backup of /etc/pulse/daemon.conf Find the line that says "flat-volumes" and change it - either from 'yes' to 'no' or vice versa. Mine was 'no', so I changed it to 'yes'. Save changes and restart. There is probably a way to restart PulseAudio without restarting the computer, but I was too lazy to find it out.

Hope that helps.

Mike.

---

