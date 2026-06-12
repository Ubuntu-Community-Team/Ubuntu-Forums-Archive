---
title: "Help with JACK"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by johnapeterson on 2007-08-04
Hey,
Really new to ubuntu studio, I finally got my m-audio Delta 44 card going, but am having a couple of problems.

When I try to open JACK I get an error message that says "Could not open ASLA sequencer as a client"

The JACK message board says the following:
07:43:40.078 Patchbay deactivated.
07:43:40.162 Statistics reset.
07:43:40.162 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.

And when I click the start button on JACK, the message board has the following text:

07:46:12.984 Startup script...
07:46:12.984 artsshell -q terminate
can't create mcop directory
Link points to "/tmp/ksocket-john"
07:46:13.521 Startup script terminated with exit status=256.
07:46:13.527 JACK is starting...
07:46:13.529 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -m
07:46:13.558 JACK was started with PID=6320 (0x18b0).
could not open driver .so '/usr/lib/libjack0.100.0/jack_alsa.so': /usr/lib/libjack0.100.0/jack_alsa.so: symbol snd_ctl_elem_value_set_id, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
could not open driver .so '/usr/lib/libjack0.100.0/jack_freebob.so': /usr/lib/libjack0.100.0/jack_freebob.so: symbol snd_midi_event_decode, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
jackd: unknown driver 'alsa'
07:46:13.723 JACK was stopped with exit status=1.
07:46:13.726 Post-shutdown script...
07:46:13.728 killall jackd
jackd: no process killed
07:46:13.957 Post-shutdown script terminated with exit status=256.
07:46:15.590 Could not connect to JACK server as client. Please check the messages window for more info.

I must admit, I am very new to this and am assuming that I do not have it set up right, and might need a explanation in layman terms.

Also, my little volume control on the top of the screen has an "x" on it.  Left click on the icon gives me a message saying that volume control could not find any elements  and/or device to control.  And it also mentions about not finding any Gstreamer plugins.

Going to my sound preferences under system, I get a test tone for when I press the "test" button (everyting in on auto detect), but the "default mixer track" window has nothing listed in it.

Otherwise, I am gettin sounds startup, shut down, but when I try to get something going like Ardour, it will not start because it needs JACK.

Thanks for any help.
John

---

