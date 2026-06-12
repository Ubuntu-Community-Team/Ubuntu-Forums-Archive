---
title: "Troublshooting high cpu with not smooth playback in mythbuntu"
date: 2009-04-19
forum: Multimedia Software
---

### Post by arobinson on 2009-04-19
My MythTV (Mythbuntu 8.10) is working, but I am noticing that the mythfrontend.real process is running at 30-50% CPU usage all the time when watching live TV (mostly HD content). I have tried several things from posts on the net with no improvements. I have also noted that the playback is not always smooth, if there is a lot of movement on screen, there is a slight jerkiness to the picture. 

My specs:
[LIST]
[*]AMD Athlon 64 X2 5200 Brisbane 2.7GHz (running the amd64 distro)
[*]eVGA 113-M2-113 motherboard (nvidia 8200 graphics card with HDMI built in)
[*]Mythbuntu 8.10 with some Jaunty packages installed
[*]ALSA built from source
[*]Using the 180.44 Jaunty NVidia proprietary driver (was using the 180.11 with same problem)
[*]Output to a 4:3 HDTV with 1920x1080i resolution (Sony KV-32HS420)
[/LIST]

What I have tried:
[LIST]
[*]Disabling audio to rule out audio problem
[*]Turned off "sync to blank" in nvidia settings
[*]Tried and failed to build a custom modeline for my TV (ended up with 640x480)
[*]And a few other MythTV settings that I cannot recall at the moment
[/LIST]

The turning off the sync to blank with the 180.44 really improved vlc's CPU usage (from ~80% CPU to ~10%), but did not affect mythfrontend. 

I tried this modeline:
```
Modeline "1920x1080@60i" 77.60 1920 1952 2240 2272 1080 1104 1110 1135 interlace
```
But as I mentioned, NVidia dropped all the resolutions at or below 640x480 saying the resolutions did not have a valid mode.

Disabling the audio had no effect, so I don't think ALSA is to blame.

Playing one of the recordings back in other players:
[LIST]
[*]Totem: 20% CPU
[*]GMPlayer: 5.5% CPU, but was only playing a frame about every second
[*]12% CPU, but had some playback issues at times (would pixelate, stop, skip frames, etc.)
[*]Xine - 27% CPU, but Xorg pegged near 99% while playing
[/LIST]
These numbers didn't seem to help, just made the problem more confusing, not sure if the different players are having codec issues ore what.

I can live with the current performance, but obviously would like to improve it. Any suggestions?

---

