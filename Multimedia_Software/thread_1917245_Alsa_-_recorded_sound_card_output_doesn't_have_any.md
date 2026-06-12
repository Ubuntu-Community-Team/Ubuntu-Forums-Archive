---
title: "Alsa - recorded sound card output doesn't have any low tones"
date: 2012-01-29
forum: Multimedia Software
---

### Post by micechal on 2012-01-29
Hi! This is my first post on this forum and I come from Poland. I'm writing here, because I have a problem with recording my sound card output.
After recording, there aren't any low tones, I can hear only the high ones, and in the background there is very loud white noise. My sound server is Alsa, Pulseaudio doesn't work, and I'm on KDE 4.8, the distro I'm using is Ubuntu 11.10. Screens of my configuration:
Kmix - [http://i.lulzimg.com/9de11dd85c.png](http://i.lulzimg.com/9de11dd85c.png)
Alsamixergui - [http://i.lulzimg.com/d23ddcd0df.png](http://i.lulzimg.com/d23ddcd0df.png)
My microphone works well, the problem is only with recording what I hear in my speakers. To record sound I'm using Audacity

Sorry for mistakes, my english isn't at the highest level. Thanks for all your help.

---

### Post by micechal on 2012-01-31
Bump. Now when recording from microphone, there is a white noise too, and the audio quality isn't good. Anyone can help?

---

### Post by micechal on 2012-02-01
Really no one know how the hell can I fix it? Microphone is needed for me, because I want to talk on Skype. Please, help me.

---

### Post by micechal on 2012-02-03
Re-installed alsa-base. There is still a noise when recording form microphone, and from line. Still no low tones. Pulseaudio doesn't work, it says "Daemon startup without any loaded modules. Refusing to work". Can anyone help me, or the only way out is to reinstall Ubuntu?

---

### Post by jean noel on 2012-02-03
I don't know if this might work, but open the terminal (found in application=>accessories=>terminal), type alsamixer. Find the mic "spectrum" and try increasing the level.
I once nearly tore my hairs off trying to record an old cassette from audacity, just to find that the "line in" level was set to min.
Regards
Jean Noel

---

