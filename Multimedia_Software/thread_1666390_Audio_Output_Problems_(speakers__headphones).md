---
title: "Audio Output Problems (speakers / headphones)"
date: 2011-01-13
forum: Multimedia Software
---

### Post by peterx14 on 2011-01-13
Hi all,

Sorry this is a long post -- short summary: audio works, but when I plug headphones in, it is muted, and if I then adjust the volume, the headphones are *VERY* loud.

Full problem: I have my main speakers connected up to the "Line Out" (lime colour) connector on my motherboard, and this works fine. But, I often like to connect headphones up to the front-panel connector; this _should_ mute the main speakers and only output to the headphones, however it just mutes the sound everywhere. If I then adjust the volume level, sound comes out the main speakers at a normal level and also out of the headphones *REALLY REALLY* loud.

The sound-preferences dialog wasn't particularly useful; the "Connector" option on the output tab gives me two options: "Analog Output" and "Analog Headphones" and the Headphones option does work as expected, i.e. the main speakers are muted whilst the headphones output at a normal level. But this requires me to change the connector option manually! Also, when it's back on Analog Output, if the headphones are connected, they go back to *REALLY REALLY* loud mode... honestly, it's hazardously loud!! :D

To try to resolve this, I've done the following:
[LIST=1]
[*]I've installed gnome-alsamixer.
[*]I've added "options snd-hda-intel model=6stack-digout" to the end of my /etc/modprobe.d/alsa-base.conf file. This doesn't *seem* to change anything for me!
[/LIST]

With gnome-alsamixer running, I can see that when I plug in my headphones, the "Front" mute box is checked and the sys-tray volume indicator shows it muted. If I then un-check that mute box or if I change the volume, I get sound out of both main speakers and headphones. Using alsamixer I can adjust the "Headphone" volume, which by default are at maximum.

Other odd stuff, (1). if I adjust levels using alsamixer to get sound out the headphones, if I then unplug and re-plug the headphones *BOTH* the "Front" and "Headphone" channels have their Mute box checked, and (2). the volume control in the sys-tray seems to be bound to the "Front" channel even when I have headphones plugged in.

So I seem to have to use the "Connector" option on sound preferences to get the volume control bound to the Headphone level, but I don't know why it doesn't switch the connector automatically when I plug my headphone in?

[LIST]
[*]Motherboard: Asus P7P55D
[*]Main speakers connected to mobo via Line Out (lime-green) connector.
[*]Headphones connected to front panel, which in-turn is connected to mobo analog
[*]front panel connector using "HD Audio" connectors (NOT AC97!) and the BIOS is
[*]configured for HD Audio front panel also.
[*]I think I'm using a VIA VT1828S chipset?
[/LIST]

The Gnome-alsamixer sound card properties lists the following, all of which
are enabled:

```
Headphone           Headphon
PCM                 PCM
Front               Front
Front Mic           Front Mi
Front Mic Boost     Front Mi
Surround            Surround
Center              Center
LFE                 LFE
Side                Side
Line                Line
CD                  CD
Mic                 Mic
Mic Boost           Mic Boos
Capture             Capture
Capture             Capture
IEC958              IEC958
IEC958 Default PCM  IEC958 Default PCM
Input Source        Input Source
Input Source        Input Source
Smart 5.1           Smart 5.1
```

And finally... this is a fresh Ubuntu 10.10 64bit installation with a clean
user profile.

Any idea welcome!! :D

---

### Post by peterx14 on 2011-02-14
Bump of hope!

---

