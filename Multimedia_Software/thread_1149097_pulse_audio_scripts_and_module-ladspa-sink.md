---
title: "pulse audio scripts and module-ladspa-sink"
date: 2009-05-04
forum: Multimedia Software
---

### Post by Absurd on 2009-05-04
so, I have been having these problems with pulseaudio and the module-ladspa-sink module

I was able to set up a working eq with the following option

```
load-module module-ladspa-sink sink_name=ladspa_out master=alsa_output.pci_1412_1724_sound_card_0_alsa_playback_0 plugin=mbeq_1197 label=mbeq control=4.0,-3.0,-5.0,-5.0,-5.0,-6.0,-6.0,-6.0,-6.0,-6.0,-5.0,-5.0,-5.0,-2.0,2.0
```

it works perfectly...*when I start pulseaudio from a terminal*

it seems that everytime I log back into ubuntu, which initiates /etc/Xsession.d/70pulseaudio and the other scripts identified, pulseaudio itself dies every time I change a track (in audacious) and I get the following error message

```
sink.c: Assertion '!s->thread_info.rewind_requested' failed at pulsecore/sink.c:640, function pa_sink_render(). Aborting.
```

however, after it dies and I restart pulseaudio in a terminal, pulseaudio works fine; no errors when changing tracks

will loading /usr/bin/pulseaudio instead of /usr/bin/pulse-session from /etc/X11/Xsession.d/70pulseaudio break anything?

yes, I've loaded pulseaudio from /usr/bin/pulseaudio, /usr/bin/pulse-session, and /usr/bin/start-pulseaudio-x11 and found /usr/bin/pulse-session to be the root of the problem

---

