---
title: "6 channel sound Nforce"
date: 2005-12-08
forum: Multimedia &amp; Video
---

### Post by SuperCzar on 2005-12-08
Ok who's the genious that knows how to get proper alsa 6 channel sound with my nforce2 on board audio...

I'm at wits end and just want my speakers to all work.

Heres my .asoundrc its basically all from a post on the ALSA project site.

```


### .asoundrc for nforce2 apu


pcm.nforce-hw {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "nforce"
}

pcm.nforce {
type dmix
ipc_key 1234
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
}

ctl.nforce-hw {
type hw
card 0
}

```

If you need anything else, I know my way around pretty well so just ask.

Thanks for even reading this far.


-- SuprCzr
5.10, KDE 3.5, NForce2 Chipset, AMD 2600+, Radeon 9800 Pro, Dual CRTs with Xinerama

---

### Post by PsyberOneZero on 2005-12-09
If your're connecting through coax or optical than this might help:
[http://ubuntuforums.org/showpost.php?p=553082&postcount=5](http://ubuntuforums.org/showpost.php?p=553082&postcount=5)

Else, what does your mixer look like (i.e. options switches) and what's the name of the mixer.

---

### Post by kscelt on 2005-12-10
[http://www.ubuntuforums.org/showthread.php?t=96370](http://www.ubuntuforums.org/showthread.php?t=96370) might help, depends on your board and setup configuration.

---

