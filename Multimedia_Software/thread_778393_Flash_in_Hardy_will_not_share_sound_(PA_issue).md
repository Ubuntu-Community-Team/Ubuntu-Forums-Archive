---
title: "Flash in Hardy will not share sound (PA issue)"
date: 2008-05-02
forum: Multimedia Software
---

### Post by coolen on 2008-05-02
I discovered yesterday, much to my dismay, that the nonfree Flash in Hardy does not use PA, and blocks my soundcard.

I've looked, and the Wiki doesn't seem to mention this, and none of the forum threads have been solved.

Has anyone gotten [this]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox") to work in the final release? I tried it, but it didn't work. It may have broken in the final release.

Does anyone know of an alternative solution?

---

### Post by Zorael on 2008-05-02
Pulse should have an alsa-plugin to wrap it into working.

Essentially, Pulse works by creating a fake ALSA output device called pulse, which makes ALSA send its output there, which in turn makes Pulse mix stuff and do its thing. If you've set it up to send sound to your soundcard sink, it'll then send the output back to ALSA but with an explicitly provided device; namingly, your soundcard.

So you want to make sure you've set ALSA to use the pulse device by default. Does your /etc/asound.conf reflect this? I think that's where you set it up.
```
zorael@sunspire:/etc$ cat asound.conf
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

---

### Post by coolen on 2008-05-02
According to the website, this doesn't work with flash. You need a wrapper of some kind (or, whatever else it may be). I had PA setup in Gutsy, and it took a few extra steps.

Confirmed. This does not allow Flash to use PA.

---

### Post by Zorael on 2008-05-02
I have it working but I'm having a hard time remembering what I did.

Try the packages some way down over at [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio).

---

