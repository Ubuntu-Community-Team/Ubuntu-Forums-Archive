---
title: "Problem Playin Music"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by Qwerty) on 2007-03-01
I have everything up and running but have a problem playing music when using 5.1 surround.  

This is the file I used .asoundrc
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

The sound in ubuntu works, as well as games.  When I play any audio format it starts skipping like crazy.  When I delete the file 5.1 goes off and the music files play pefectly.  If someone knows a fix that would be great, I would love to have 5.1 in music and games :)

---

### Post by Qwerty) on 2007-03-01
Okay using this:
pcm.dshare {
    type dmix
    ipc_key 2048
    slave {
        pcm "hw:0"
        rate 44100
        period_time 0
        period_size 1024
        buffer_size 8192
        channels 6
    }
    bindings {
        0 0
        1 1
        2 2
        3 3
    }
}
pcm.frontx {
    type plug
    slave {
        pcm "dshare"
        channels 6
    }
    ttable.0.0 1
    ttable.1.1 1
}
pcm.rearx {
    type plug
    slave {
        pcm "dshare"
        channels 6
    }
    ttable.0.2 1
    ttable.1.3 1
}




I get 5.1 sound now without   choppy music, however, the back speakers are very quiet.  I tried using the fader on my speaker control, but that didnt work.  Is there an option to trn up the volume.  I loked in the mixer and everything is maxed atm.

---

