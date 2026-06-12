---
title: "Can't start jackd with Zoom h4n"
date: 2011-11-22
forum: Multimedia Software
---

### Post by tim_godfrey on 2011-11-22
I am trying to use the Zoom h4n as an audio interface with Jack. The device seems to be supported by Alsa, as I can play and capture audio using the default sound config tool in ubuntu, and with aplay. However, if I try to use the device with JACK, I can only start it in 'capture only' mode, or it will fail with

Alsa: cannot open device for playback (broken pipe)

I have found a few threads on forums and mailing lists in which people have described a similar problem, but I haven't found any solutions, or descriptions of what people did to make it work. 

What can I do to get more detailed output from alsa, when it is used launching the jack sound server? Any other suggestions to troubleshoot the problem?

Thanks!

---

