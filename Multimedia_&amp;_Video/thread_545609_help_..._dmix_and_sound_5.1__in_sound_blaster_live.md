---
title: "help ... dmix and sound 5.1  in sound blaster live 24 bits!"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by dzapata on 2007-09-07
Hello everybody ... First place, sorry because I don't know to write very good english but I will try it. I write this post because I have a problem with my sound blaster live 24 bits card. The problem is that I don't found an asound.conf file that allows dmix and 5.1 sound, and I wish to have both things. I found two configurations that individually allows, that is to say, one script allows dmix and the other allows 5.1 sound. 

 dmix configuration:

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
period_size 2048 #1024
buffer_size 32768 #4096
#periods 128
rate 48000 #44100
}
bindings {
0 0
1 1
}
} 

5.1 Sound configuration:

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
} 

I would wish add to dmix configuration the 5.1 sound but my attempts have been insolvent.

¿May I add to this dmix configuration the 5.1 sound ?
¿How I do it?

Thanks for your help and for my bad english

---

