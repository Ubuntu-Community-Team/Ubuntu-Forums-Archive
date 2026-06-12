---
title: "constant pulseaudio connection failure (dual soundcard)"
date: 2008-11-25
forum: Multimedia Software
---

### Post by kakyoism on 2008-11-25
I was happy with pulseaudio.
But recently something weird happened constantly.

I have a USB soundcard and I use it as major sink for all applications.
But recently whenever I disconnected it and plug it back, my previous applications would fail to play; and if I try to launch the pulseaudio volume control widget, I got error dialog saying "connection failed".

I'd have to use "pulseaudio -D" to get the daemon back on manually.
Any idea?

---

### Post by markbuntu on 2008-11-25
Are you moving your applications from the usb sink before you disconnect it?

Pulseaudio should move the sinks automatically but seems to be crashing instead. There is a pulse log somewhere... or you could do a backtrace.

---

### Post by kakyoism on 2008-11-25
no...i just unplugged it...
before i unplug it, should i redirect all app audio streams that rely on my USB sink to the other soundcard through pavucontrol? that sounds quite tedious...

---

### Post by soxs on 2008-11-25
> **kakyoism said:**
> no...i just unplugged it...
before i unplug it, should i redirect all app audio streams that rely on my USB sink to the other soundcard through pavucontrol? that sounds quite tedious...

No this should be done automatically bei PA. But it doesn't do it in your case... -> file a bug report with any output being connect to it @ [www.launchpad.net](www.launchpad.net)

---

### Post by kostkon on 2008-12-03
Yes, it seems that *PulseAudio* crashes when trying to move the streams to your other soundcard when you unplug your USB soundcard.

Is your other soundcard working OK, especially with *PulseAudio*?

Yes, you could fill a bug report on *Launchpad*. 

When *PulseAudio* crashes/has problems it outputs any error messages to the *syslog* log file. Thus, use this output when filling your bug report.

---

