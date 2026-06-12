---
title: "Audiostream PulseAudio"
date: 2011-12-08
forum: Multimedia Software
---

### Post by Carharttguy on 2011-12-08
Hello everybody,

I'm trying to stream my PulseAudio output to the web, and it works. Using Icecast.
I have this commandline to start the upstream:

> gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! audioconvert ! lame bitrate=96 mode=stereo ! shout2send ip=localhost port=8000 password=****** mount=stream.mp3No problem with this.. I stream this to my phone, and works perfectly.. Almost perfectly, there's a delay of about 10-15 seconds. I think it has something to do with realtime encoding.

But, what ouput does "gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" give? Maybe conversion isn't necessary. It would be so much quicker if I could upstream it without "audioconvert" and "lame".

Anybody has an idea how to do faster/no conversion? Maybe a config withing PulseAudio?

Thanks for helping me

---

### Post by Carharttguy on 2011-12-09
Nobody? Only a little hint could help me a lot.

I searched documentation of PulseAudio, but couldn't find info about the ouput stream.

---

