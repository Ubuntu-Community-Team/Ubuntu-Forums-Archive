---
title: "crackling audio External USB DAC"
date: 2012-03-06
forum: Multimedia Software
---

### Post by matt99eo on 2012-03-06
Hi,

I am trying to get my audio to stop crackling in Ubuntu 11.10.   Currently it outputs to an external USB DAC and seams to be dropping bits or something.

I have been trying to fix it using Pulseaudio setting and alsa mixer settings to no avail.

The crackling occurs when no music is playing, during playback, and when I open a new terminal window.  Very odd.

Any help appreciated.

---

### Post by matt99eo on 2012-03-06
Here are some excerpts from my pulseverbose log.  PLEASE HELP ME.:p

(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
(   0.015|   0.015) D: [pulseaudio] core-util.c: RealtimeKit worked.
(   0.015|   0.000) I: [pulseaudio] core-util.c: Successfully gained nice level -11.
(   0.015|   0.000) I: [pulseaudio] main.c: This is PulseAudio 1.0
(   0.015|   0.000) D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
(   0.015|   0.000) D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -g -O2 -Wall -W -Wextra -pipe 
(  46.927|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Core1.Memstats removed from object /org/pulseaudio/core1/memstats
...
(  46.927|   0.000) I: [pulseaudio] sink.c: Freeing sink 0 "alsa_output.usb-Burr-Brown_from_TI_USB_Audio_DAC-00-DAC.iec958-stereo"
(  46.927|   0.000) I: [pulseaudio] source.c: Freeing source 0 "alsa_output.usb-Burr-Brown_from_TI_USB_Audio_DAC-00-DAC.iec958-stereo.monitor"
....
(  46.928|   0.000) I: [pulseaudio] module.c: Unloaded "module-dbus-protocol" (index: #21).
(  46.928|   0.000) I: [pulseaudio] module.c: Unloading "module-switch-on-port-available" (index: #22).
(  46.928|   0.000) I: [pulseaudio] module.c: Unloaded "module-switch-on-port-available" (index: #22).
(  46.928|   0.000) I: [pulseaudio] module.c: Unloading "module-null-sink" (index: #23).
(  46.928|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  46.928|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  46.928|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  46.928|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  46.928|   0.000) D: [null-sink] module-null-sink.c: Thread shutting down
(  46.928|   0.000) I: [pulseaudio] sink.c: Freeing sink 1 "auto_null"
(  46.928|   0.000) I: [pulseaudio] source.c: Freeing source 1 "auto_null.monitor"
(  46.928|   0.000) I: [pulseaudio] module.c: Unloaded "module-null-sink" (index: #23).
(  46.928|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
(  46.928|   0.000) I: [pulseaudio] main.c: Daemon terminated.
[/CODE]

---

### Post by matt99eo on 2012-03-07
Bump.  

Come on Ubuntu!  I really need help with this issue.  

So if I play music through the built in audio through headphones all is well but if I play through my external DAC  I start getting the glitches and crackling even when music is not playing.  Open a new terminal = crackling.

---

