---
title: "easy video switching between output=HDMI and output=VGA?"
date: 2011-03-15
forum: Multimedia Software
---

### Post by tlroche on 2011-03-15
My girlfriend connects a nettop with nVidia graphics running 10.10/Maverick to

[LIST=1]
[*]an older Sony monitor on her desk for doing real work, using a VGA cable. The Sony has only VGA input, and is nearly square (not widescreen). She likes it @ 1280x1024.
[*]a large, widescreen Samsung monitor for watching videos, using an HDMI cable. The Samsung supports several connectors (including RF, optical, RGB/component, HDMI, and VGA) with max resolution=1360x768.
[/LIST]

I'd like to know how to setup an easy way to either (in declining order of preference)

[LIST=1]
[*]switch between the monitors. When she wants to watch a movie, she sets output to go to the Samsung; when she's gotta work, she sends output to the Sony.
[*]enable both outputs (with different resolutions), "switching" by just turning off the monitor that's not in use.
[/LIST]

I have an old ThinkPad laptop with "ThinkVantage Presentation Director" that handles this usecase by allowing the user to define, and easily (notably, without restarting) switch between separate "profiles," which are collections of parameters, including

[LIST]
[*]output direction: i.e. output to laptop monitor or external monitor (via VGA only) or both
[*]resolution (same to all outputs)
[/LIST]

Is there a way to setup something similar to handle the Samsung/Sony usecase? On Gnome I'm guessing I would use System>Administration>NVidia X Server Settings, but would appreciate guidance from someone who's already done this. Pointers to documentation especially appreciated.

---

### Post by BicyclerBoy on 2011-03-16
Maybe 
xrandr with twinview metamode..

[http://morgancollett.wordpress.com/2008/11/25/nvidia-twinview-and-xrandr/](http://morgancollett.wordpress.com/2008/11/25/nvidia-twinview-and-xrandr/)

don't know if this still works ..good luck.

---

### Post by tlroche on 2011-03-16
> **tlroche said:**
> I'd like to know how to setup an easy way to either (in declining order of preference)

[LIST=1]
[*]switch [the same display] between [two] monitors. When she wants to watch a movie, she sets output to go to the Samsung; when she's gotta work, she sends output to the Sony.
[*]enable both outputs (with different resolutions), "switching" by just turning off the monitor that's not in use.
[/LIST]


> **BicyclerBoy said:**
> Maybe xrandr with twinview metamode..
[http://morgancollett.wordpress.com/2008/11/25/nvidia-twinview-and-xrandr/](http://morgancollett.wordpress.com/2008/11/25/nvidia-twinview-and-xrandr/)


Thanks for the link, it's quite informative. However, for this usecase, I don't need [span mode](http://en.wikipedia.org/wiki/Multi-monitor#Span_or_extended_desktop_mode) (i.e., to have one desktop spanning 2 monitors), and I need more than [clone mode](http://en.wikipedia.org/wiki/Multi-monitor#Clone_mode), which are (IIUC) what [TwinView](http://www.nvidia.com/object/feature_twinview.html) is about. I need [multi-mode](http://en.wikipedia.org/wiki/Multi-monitor#Multi-mode): I want the same desktop on 2 monitors, and at two different resolutions. But I'll definitely take a closer look @ TwinView.

---

### Post by BicyclerBoy on 2011-03-17
Using nvidia  x server driver..
Independent resolutions & refresh rate is only possible with separate X screens mode..AFAIK.
The flexibility is far lower than windose but AFAIK this is partly to do with Xorg.
The twinview metamode is a virtual rectangle box about both screen sizes..

I have heard that the nouveau driver is much more capable with hot swapping etc
You would have to give up vdpau & use CPU only.

The only downside of having 2 separate X screens always active (forced in xorg.conf) is that the nvidia driver will not use adaptive powersaving clocking modes & your mouse can get lost.

You can force apps to open on either screen which is good for video.

---

