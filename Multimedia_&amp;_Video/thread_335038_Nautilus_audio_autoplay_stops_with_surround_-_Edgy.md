---
title: "Nautilus audio autoplay stops with surround - Edgy"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by onon_onon on 2007-01-09
I can't figure out what is going on here, but the nautilus sound autoplay feature (when you left mouse pointer over a mp3, wav or ogg file) works great, unless I use surround sound as default. Then, autoplay simple stop working, without any error message.
Can somebody explain how the sounds autoplay feature works or tell me what is happening?
My soundboard is a nVidia CK804 and this is my .asoundrc file:
```
#########################################################
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,0"
}

#######################################################
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want. 


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

```

Thanks in advance.

---

### Post by onon_onon on 2007-01-11
Nothing?

---

### Post by onon_onon on 2007-01-13
Sorry for this, last UP in thread.

---

### Post by BuddMan on 2007-02-04
I'd also like to know how this works, but I'm using XFCE and am not sure if it is available in XFCE.  Any info would be appreciated.

---

