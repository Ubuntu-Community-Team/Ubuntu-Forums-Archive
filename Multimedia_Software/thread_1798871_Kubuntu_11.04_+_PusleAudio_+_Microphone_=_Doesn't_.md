---
title: "Kubuntu 11.04 + PusleAudio + Microphone = Doesn't work"
date: 2011-07-06
forum: Multimedia Software
---

### Post by brandito on 2011-07-06
I upgraded to Kubuntu 11.04 and my mic is no longer working.
Everything looks good.

[http://www.alsa-project.org/db/?f=6cc838f9edf091301e360f6d1ed80b9b352dc7ac](http://www.alsa-project.org/db/?f=6cc838f9edf091301e360f6d1ed80b9b352dc7ac)

I unmute everything from alsamixer.
I test every input device from pavucontrol.  I've moved my mic from the front to the back, no luck.
I've created an /etc/asound.conf file with the following:
```
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

```
... and no luck.

I can't get the mic working with an app I have.
My phonon settings look fine.  I am totally lost.

---

