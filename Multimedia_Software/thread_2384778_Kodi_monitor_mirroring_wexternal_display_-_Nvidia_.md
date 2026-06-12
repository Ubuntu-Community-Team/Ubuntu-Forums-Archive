---
title: "Kodi monitor mirroring w/external display - Nvidia Driver"
date: 2018-02-12
forum: Multimedia Software
---

### Post by tallone55 on 2018-02-12
I built a media box with an Nvidia card to replace an aging machine and I'm trying to make the transition as seamless as possible for the primary user.


I have two displays that I need to use with the machine: an always-on 4:3 monitor connected via DVI and an "off-when-not-actively watching a movie" 16:9 projector connected via HDMI.


Currently I run this as a Startup Application whenever the media account logs into its desktop:
```
xrandr --output DVI-I-1 --same-as HDMI-0
xrandr --output DVI-I-1 --auto --scale-from 1280x720 --output HDMI-0

```It mirrors the projector display to the monitor with scaling such that the monitor displays a slightly stretched but perfectly usable copy of the projector image.


My problem is that turning off the projector causes the current solution I have to break. The projector ceases to be the primary display and stops being detected, which causes the mirroring to end and the monitor to stop being scaled. Simply running the above commands when I've turned the projector back on does *not* fix the displays.


How can I get this working?

---

