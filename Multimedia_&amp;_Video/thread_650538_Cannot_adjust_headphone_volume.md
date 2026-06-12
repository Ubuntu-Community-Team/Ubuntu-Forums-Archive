---
title: "Cannot adjust headphone volume"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by bitter_mike on 2007-12-26
Hey all. I'm having a bit of a problem adjusting the volume output to my headphones. Basically, alsamixer shows a "headphone" output, but only allows you to mute/unmute it, not to adjust the volume to it. When I check the amixer output for the headphones, I get this:

Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]

Other mixer controls have the "pvolume" attribute which seems to correlate with alsamixer's ability to adjust the volume for it, Also, using the graphical volume thing that comes with Gutsy, I'm able to mute and unmute (there's a checkbox) but I can't adjust the volume. I should also mention that adjusting the other volume controls has some effect on the volume to the headphones, but even with all the available controls maxed out, the volume comes out a lot lower than my headphones are capable of outputting. Any ideas? Thanks.

---

