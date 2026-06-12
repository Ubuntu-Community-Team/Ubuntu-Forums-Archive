---
title: "PulseAudio &quot;loopback&quot; setup?"
date: 2009-05-03
forum: Multimedia Software
---

### Post by djbon2112 on 2009-05-03
Hello everyone. I've got a quick question about PulseAudio. Is it possible to set up a "loopback" that will send an input device directly to an output stream? Here's my setup

Mixing Board (USB interface) -> Laptop (PulseAudio Input Device A)
Laptop -> USB Sound card (PulseAudio Output Device B)

Is there a way to send A directly to B as a monitor of some sort?

---

### Post by markbuntu on 2009-05-04
There is no way to connect sinks and sources directly with pulseaudio. People have been asking Lennart to do this for years but he seems to think there is no need even though it should be fairly easy to make some "monitors" of sources for the Output Devices like the monitors of sinks in Input Devices.

That said, you can turn on the rtp sender and set a loopback in the Pulse Audio Preferences.

Why don't you ask at the pulseaudio mailing list or file a bug ticket at 

[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

---

### Post by djbon2112 on 2009-05-04
> **markbuntu said:**
> There is no way to connect sinks and sources directly with pulseaudio. People have been asking Lennart to do this for years but he seems to think there is no need even though it should be fairly easy to make some "monitors" of sources for the Output Devices like the monitors of sinks in Input Devices.

That said, you can turn on the rtp sender and set a loopback in the Pulse Audio Preferences.

Why don't you ask at the pulseaudio mailing list or file a bug ticket at 

[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

That's unfortunate... I'd use Jack but it seems a lot of programs don't work well with it as the main audio system. Oh well, thanks though!

---

