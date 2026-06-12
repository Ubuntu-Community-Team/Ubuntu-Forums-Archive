---
title: "Output Line-In to Speakers in 10.04"
date: 2010-07-16
forum: Multimedia Software
---

### Post by Hichhiker on 2010-07-16
Ok, I see this question asked many times, and yet to see an answer.

Before 10.04 "simplified" sound options, you could go into sound settings and set a checkbox to send line-in to speakers. This option is gone in 10.04 - how does one do such a feat?

I go into "PulseAudio Volume Control" (or "Sound Preferences") and I can choose line-in over "microphone" as my input. I can see Input Level so I know the system sees the Input. But I can find no way to send it directly to output.

In case it matters:

Audio Device:

00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)

Also: no, nothing is muted and yes, I checked "alsamixer".

-HH

Update: Looks like you can add a loopback module to PulseAudio to emulate this behaviour in software, but the 1-2 second delay this introduces makes it unsuitable for video applications.

---

