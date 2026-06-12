---
title: "Howto dmix and upmix?"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by swizec on 2007-06-09
Hi,

I'm having a little trouble configuring my alsa so it would both upmix to 5.1 sound and dmix so I could listen to several things at once. I've followed the upmix example and it worked nicely. Trying to add dmix was a bit less succesful as simply slapping it into /etc/asound.conf didn't work and trying to merge it into the ~.asoundrc didn't work either.

This is what I currenlty have
```

#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.
pcm.card0 {
        type hw
        card 0
}

pcm.!default {
        type plug
        slave.pcm "surround51"
        #slave.pcm "dmixer"
        slave.channels 6
        route_policy duplicate
        #slave dmixer;
}
########################################################
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
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
        type dmix
        ipc_key 1025
        slave {
                pcm "hw:0,0"
                period_time 0
                period_size 1024
                buffer_size 4096
                periods 128
                rate 44100
        }

}

```

Any help would be greatly appreciated.


Also how do I get alsamixer to save the settings forever because it keeps jumping to 100% each time I restart KDE.

---

### Post by swizec on 2007-06-09
After a lot of searching and tinkering I came up with this ... getting closer but still no dmixing.

Really could use some help people


```

pcm.!default {
        type plug
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}

pcm.!spdif {
    type plug
    slave.pcm "hw:0,1"
}

pcm.analog {
    type plug
    slave analog_slave
}

pcm_slave.analog_slave {
        pcm surround51
        slave.pcm "dmixs51"
        slave.channels 6
}

pcm.dmixs51 {
        type dmix
        ipc_key 1024
        ipc_key_add_uid false # let multiple users share
        ipc_perm 0660 # IPC permissions (octal, default 0600)
        slave {
                pcm default
                rate 48000
                channels 6
                format S32_LE
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 5120
        }
}

```

---

