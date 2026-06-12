---
title: "ALSA lag in Wine"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by juraj on 2007-06-03
Okay, I am fighting with this for a week. I'm using Ubuntu Feisty.

I want to use native teamspeak client while playing UT 99 in Wine. (yes I know there's a native version)

To achieve this, I must use ALSA because I have a AC97 onboard sound card which doesn't support hardware mixing.

With default configuration, teamspeak runs fine through aoss. UT can run, but sound lags 1 to 2 seconds when Wine is configured to use the native ALSA driver, silence with OSS + aoss. With OSS driver UT runs excellent, however, I can't use teamspeak.

Now, I've tried literally HUNDREDS of .asoundrc configs and haven't discovered a perfect config. With this .asoundrc I can't use microphone in teamspeak and sound lag in UT is tolerable (~0.2-3 seconds):
```

pcm.ossmix {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024 
        buffer_size 4096
    }
    bindings {
        0 0 # from 0 => to 0
        1 1 # from 1 => to 1
    }
}
pcm.dsp0 {
    type plug
    slave.pcm "ossmix" # use our new PCM here
}
# mixer0 like above
ctl.mixer0 {
    type hw
    card 0
}


pcm.default pcm.dsp0
```

What should I do? Please help!

---

### Post by juraj on 2007-06-04
Please, anyone? I would really like to be able to have normal ALSA output in Wine so I can use Teamspeak.

---

### Post by juraj on 2007-06-08
bump

---

