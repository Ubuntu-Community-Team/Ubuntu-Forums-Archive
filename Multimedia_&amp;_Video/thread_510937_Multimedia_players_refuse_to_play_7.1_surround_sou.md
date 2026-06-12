---
title: "Multimedia players refuse to play 7.1 surround sound"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by Afrikaan on 2007-07-27
My on board soundcard is Soundblaster live! 24-bit.  When i test the sound with .asoundrc file edited - in order to play 7.1 -  all speakers appear to be ok, but Amarok crashes and VLC also play with no sound. Without the .assoundrc, only the two front speakers and the woofer appear to be ok. I 've tried both
```
pcm.!default {
    type plug
    slave.pcm "surround71"
    slave.channels 8
    route_policy duplicate
}
```
and
```
pcm.ca0106 {
type hw
card 0
}

ctl.ca0106 {
type hw
card 0
}

pcm.!dmix {
type plug
slave {
pcm surround71
channels 8
}
}
pcm.!default {
type plug
slave.pcm "dmix"
slave.channels 8
route_policy duplicate
}
```
but the  problem is still remaining.

I hope somebody could help.

---

### Post by deadgobby on 2007-07-27
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

---

### Post by Afrikaan on 2007-07-27
Well, when i give ```
speaker-test -Dplug:surround71 -c8 -l1 -twav
``` all speakers seem to be ok. The problem is that Amarok crashes and VLC  gives me no output.

---

### Post by Afrikaan on 2007-07-28
I think its xine's problem..

---

