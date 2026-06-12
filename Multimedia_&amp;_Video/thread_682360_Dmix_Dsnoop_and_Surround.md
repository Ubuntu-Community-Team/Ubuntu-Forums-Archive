---
title: "Dmix Dsnoop and Surround"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by Statix0 on 2008-01-29
I'm trying to combine Dsnoop, Dmix, and Surround Sound on my AudigySE.

I've found so many things and combined them together in my .asoundrc and now I just have a big mess.

I can't really tell if my surround is working, but I think not. And my dsnoop input is not working at all. On the plus side dmix is.

```
# cat ~/.asoundrc
pcm.dsp0 {
    type plug
    slave.pcm "dmix"
}
# mixer0 can stay unchanged, because
# it isn't used anyway, I guess ;)
ctl.mixer0 {
    type hw
    card 0
}

pcm.dsnooped {
    type dsnoop
    ipc_key 2048
    slave {
    pcm "snd_usb_audio"
    #   rate 48000
    #   period_size 128
    }
}

pcm.ch40dup {
    type route
    slave.pcm surround40
    slave.channels 4
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
}

pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}

```

Can someone help? I want my input to come from my USB mic (snd_usb_audio which is card 1, my second card) Card 0 my first card is my sound card.

---

### Post by Statix0 on 2008-01-31
Anyone?

---

### Post by Dandeloreon on 2008-02-07
Not enough information is provided, can you please provide the output of...

```

aplay -l

```

with this i can start writing a new config file.

---

### Post by Statix0 on 2008-02-09
Thanks for the help. I also no longer need the surround.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

