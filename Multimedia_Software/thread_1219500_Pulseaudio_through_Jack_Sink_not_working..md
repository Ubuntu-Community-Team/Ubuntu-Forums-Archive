---
title: "Pulseaudio through Jack Sink not working."
date: 2009-07-21
forum: Multimedia Software
---

### Post by secondstage on 2009-07-21
I followed [this how-to]("http://ubuntuforums.org/showthread.php?t=843012") to get Jack Audio to play nice with Pulseaudio, and it seems functional. Using patchage the audio seems to be coming out fine digitally from the PulseAudio Jack Sink (I used a VU Bridge to register the audio.), but although the connections are present, no audio is coming out of my speakers. Pulseaudio Volume Control is even picking up the Jack Sink, and showing output.

Is there a missing connection in Jack, or PA that is keeping the audio from getting out of my computer?

---

### Post by secondstage on 2009-07-22
I tried it today, and it worked perfectly, well after I did a bit of configuration.

I had to move the stream to the Jack Sink, and then make sure that any new audio devices automatically attached themselves to Jack by making the Jack Output Device the default. And then I just made Jake start itself on boot, so I always have Jack open and ready for any Jack-aware program, and then because Pulse and Jack are playing nice now, I can have any sort of audio thing hook into my system perfectly.

---

