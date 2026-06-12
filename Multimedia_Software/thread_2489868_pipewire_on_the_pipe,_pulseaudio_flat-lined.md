---
title: "pipewire on the pipe, pulseaudio flat-lined"
date: 2023-08-12
forum: Multimedia Software
---

### Post by sienile on 2023-08-12
After removing fluidsynth, all my sound settings are screwed. I never even heard of pipewire before this, but apparently it was installed from the beginning as was the familiar pulseaudio. Originally when my problems started I had nothing showing up in my sound settings, no devices, nothing. After a few days of poking at it I got it to display a Dummy Output by making a fresh user (which works entirely as expected) and copying that user's pulseaudio and pipewire config files over. Seeing this dummy output required either pipewire or pulseaudio to be restarted first.

At one point I had sound playing without restarting the services, but it would show the dummy output and a muted volume indicator. Sounds would default to their highest setting like this, with no way of controlling them.

I've tried everything I can find on this (aside from fresh install) and still the problem is the same. When I remove pulseaudio, I lose my volume indicator and still need to restart pipewire with this command:
```
systemctl --user restart pipewire{,-pulse}{,.socket} wireplumber

```Restarting the various pipewire services individually would sometimes work, but usually not.

When pulseaudio was removed, pipewire runs at login according to systemctl and journalctl, but doesn't work until I enter the above command.

So what am I doing wrong and why is it that new users have it right but I can't just copy over their settings? Are there user settings that I'm missing?

---

