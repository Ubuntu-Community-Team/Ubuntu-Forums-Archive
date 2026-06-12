---
title: "Combine Pulseaudio with JACK"
date: 2012-07-06
forum: Multimedia Software
---

### Post by luyade on 2012-07-06
Pulseaudio is the default sound server in Ubuntu 10.04. And it works not so good with applications which need low latency. So I want to combine pulseaudio with Jack to also get the low latency. Here is what I have done:
1. Install pulseaudio-module-jack, jackd
 
2. sudo usermod -a -G audio username
 
3. add lines to /etc/security/limits.conf :
  @audio          -       rtprio          100
  @audio          -       nice            -10
 
4. tweak the /etc/pulse/default.pa:
load-module module-jack-sink
load-module module-jack-source
 
5. make jackd started at boot time(before pulseaudio)
 
But I found that I can't record anything, the audio output is well. If I set default sink/source to jack_in/jack_out, I found that the playback also doesn't work. Anyone can help me on this? Tnanks.

---

