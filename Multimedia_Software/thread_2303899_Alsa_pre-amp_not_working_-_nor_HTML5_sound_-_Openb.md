---
title: "Alsa pre-amp not working - nor HTML5 sound - Openbox environment"
date: 2015-11-22
forum: Multimedia Software
---

### Post by steve234 on 2015-11-22
Evening,

I am having problems with volume and sound in Lubuntu Openbox environment 

(1) The sound is woefully low. I have done some googling and seen that ALSA project seem to like low sound, and the fix seems to be amending the /etc/asound.conf file to include a pre-amp.

I've tried this and the pre-amp slider doesn't show up? Have I done something wrong? my asound.conf is:

```

 pcm.!default {        type hw
        card 0
}
ctl.!default {
        type hw
        card 0
}
pcm.!default {
        type plug
        slave.pcm “softvol”
}
pcm.softvol {
        type softvol
        slave {
                pcm “dmix”
        }
        control {
                name “Pre-Amp”
                card 0
        }
        min_dB -5.0
        max_dB 20.0
        resolution 6
}



```

I see it mentions a plugin called dmix - is this something built in to 'buntu as it's not in the repo?

(2) I don't get any sound at all when playing HTML5 video - Chromium browser. 

Any suggestions?

---

