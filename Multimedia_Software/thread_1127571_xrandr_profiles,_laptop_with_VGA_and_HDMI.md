---
title: "xrandr profiles, laptop with VGA and HDMI"
date: 2009-04-16
forum: Multimedia Software
---

### Post by jblanca_val on 2009-04-16
Hi:
I've got a laptop with an external monitor (HDMI) and a video projector (VGA) attached to it. Some times (lid closed and HDMI connected) I want only the external monitor to start, some other times (just feeling to watch a movie and VGA connected) I want the video projector and the laptop on. Besides, my viewsonic monitor gives a faulty EDID info.
The result is quite a mess difficult to manage even with the xrandr tool. So I've written a couple of scripts that set up all that mess for me.  One of them (xrandr_profiles.py) declares some profiles, chooses one and enforces it using xrandr. Each profile has a list of prerequisites that should be met in order to be choosen, like:

external_monitor_only_prerequisites = {'connected_outputs':['TMDS-1'], 'requested_outputs':{'VGA':False}, lid_open':False}

So this profile will be chosen when TMDS-1 (HDMI) is connected, I'm not feeling to watch a movie (VGA not requested) and the laptop lid is closed. If that's the case this profile dictates that a newmode should be added to my faulty viewsonic monitor and that I just want my HDMI monitor to work.
vx2025_mode = {'output':'TMDS-1', 'name':'1680x1050@60', 'modeline':'1680x1050@60 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync'}
external_monitor_only_xrandr = ['--output', 'VGA',  '--off', '--output', 'LVDS', '--off', '--output', 'TMDS-1', '--mode', vx2025_mode['name']]

Maybe the description seems a little complex, but I don't think so. Just define when a profile should be used and how xrandr should set up the given profile. I'm using xrandr_profile.py in my gnome session to set everything up when gnome starts. When I want to watch a movie I click in a launcher that executes toogle_vga.py. Now I want to execute also xrandr_profile.py when I close or open my laptop lid.

I'm quite happy with this setup and I want it to share it. There's no documentation because is just a hack so if you want to use it maybe you'd need some python.
I'd be happy to read some comments about it, if you think that it's an interesting idea or even if you feel it's a crappy solution for a problem that could be solved with a proper tool that I'm not aware of :).
Best regards,

JB

---

### Post by jblanca_val on 2009-04-17
I've updated the script to fix a bug in the xrandr parsing.

Any hints about how to run a program when the laptop lid is open or closed?

---

