---
title: "unable to get delta 44 working with alsamixer"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by johnapeterson on 2007-08-15
Hey My Mighty Ubuntu Guru Friends,

I need some help getting my maudio delta 44 up and running.  Actually it seems to be running fine for the most part, but if I try to open alsamixer (I am using alsa with the card, not oss) I get the following message:
 

********************   WARNING   *******************************
Warning! alsamixer uses ALSA emulation instead of the native OSS API
****************************************************************

snd_mixer_set_callback()
No mixer elems found

Also when I fire up JACK I get this message at startup:

16:21:31.327 Patchbay deactivated.
16:21:31.438 Statistics reset.
16:21:31.439 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
16:21:35.259 Startup script...
16:21:35.259 artsshell -q terminate
can't create mcop directory
Creating link /home/john/.kde/socket-john-desktop.
16:21:35.749 Startup script terminated with exit status=256.
16:21:35.749 JACK is starting...
16:21:35.749 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -D -P/dev/dsp0 -m
16:21:35.758 JACK was started with PID=7548 (0x1d7c).
could not open driver .so '/usr/lib/libjack0.100.0/jack_alsa.so': /usr/lib/libjack0.100.0/jack_alsa.so: symbol snd_ctl_elem_value_set_id, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
could not open driver .so '/usr/lib/libjack0.100.0/jack_freebob.so': /usr/lib/libjack0.100.0/jack_freebob.so: symbol snd_midi_event_decode, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
jackd: unknown driver 'alsa'
16:21:35.886 JACK was stopped with exit status=1.
16:21:35.886 Post-shutdown script...
16:21:35.886 killall jackd
jackd: no process killed
16:21:36.116 Post-shutdown script terminated with exit status=256.
16:21:37.969 Could not connect to JACK server as client. Please check the messages window for more info.

I am assuming that I do not have something set up right.  I am really new to this and would appreciate any help.](*,)

Thanks for any help.
John

---

