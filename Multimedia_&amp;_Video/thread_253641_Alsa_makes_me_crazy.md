---
title: "Alsa makes me crazy"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by dixxxxer on 2006-09-08
Ok, here's the deal.
The only software that's working with my tv-card is XdTv.
And it have worked fine until now.

I've made some new configuration 'cause the firefox isn't working correctly and so I tried to change my Dapper settings like it's been told here:
[http://http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME]("http://http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME")
And now I'm screwed ](*,) 

My XdTv works only with command : xdtv -noalsa
And when I try to use it with alsa it complains:
> *** AUDIO DEVICE TYPE = alsa
xdtv: simple.c:698: snd_mixer_selem_get_capture_switch: Assert-makro "elem" failed.
Interrupted

I'm lost! What to do, please help me :(

---

### Post by dixxxxer on 2006-09-10
Now it's working!
The reason was unconfigured .asoundrc file
This is what I did:

```
pcm.dmixer {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"
        period_time 0
        period_size 1024
        buffer_size 8192
   rate 44100
    }

    bindings {
        0 0
        1 1
    }
}

pcm.dsp0 {
    type plug
    slave.pcm "dmixer"
}

pcm.!default {
        type plug
        slave.pcm "dmixer"
}

pcm.default {
   type plug
   slave.pcm "dmixer"
}

ctl.mixer0 {
    type hw
    card 0
}


```

Now XdTv is working with alsa!

---

