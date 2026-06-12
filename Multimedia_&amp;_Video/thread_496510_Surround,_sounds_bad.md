---
title: "Surround, sounds bad"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by freespirit83xyz on 2007-07-09
Hi.
I'm wandering from forum to forum looking for a solution to my problem.
I've a Asus M2NPV-VM series motherboard and I've some problem with surrond.
My rear speakers don't work. Like Simon$Garfunkel's song "Sound of silence"!
This is my asound.conf

##GreatSound
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

##Surround
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
        slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

##Skype
pcm.skype {
type asym
playback.pcm "skypeout"
capture.pcm "skypein"
}

pcm.skypein {
type route
slave {
 pcm "skypedsnoop"
 format S16_LE
}

ttable {
 0 {0 0.5}
 1 {0 0.5}
}

}

pcm.skypeout {
type plug
slave {
 pcm "dmix"
}
}

pcm.skypedsnoop {
type dsnoop
ipc_key 1133
slave {
 pcm "hw:0,0"
 period_size 256
 periods 16
 buffer_size 16384
}
bindings {
 0 0
}
}

Where is the problem?

Help me please...

---

