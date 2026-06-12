---
title: "HOWTO: ATI, audio over HDMI :)"
date: 2008-07-04
forum: Multimedia Software
---

### Post by terrax on 2008-07-04
I have read alot of threads, plz trying getting audio over hdmi to work. Actually its not that hard, so I wrote a little guide, which worked perfectly for me.

It might work out of the box (can't say if it did for me, because I did alot of driver installations undtil I found the magic solution).

1:First do this:
```

aplay -l

```

Mine looked like this:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My hdmi device is card 1, device 3. That means it exist out of the box!

All I had todo, was to unmute the card, because it is muted default.

```

alsamixer -c 1 # Where 1 is the card number

```

Now in alsamixer, unmute your hdmi card with "m",
Voila, and there is sound on my hdmi movies.

If this isnt working, try install the 8.6 catalyst driver, and the newest alsa-driver. Worked for me.


:guitar:

---

### Post by wu-stix on 2008-07-08
Hey,
Thanks for the post I have been struggling with this problem for the past week.  Now if only I could get my card to output at 1080p widescreen.

---

### Post by boubou91 on 2008-07-10
> **terrax said:**
> 

If this isnt working, try install the 8.6 catalyst driver, and the newest alsa-driver. Worked for me.



When you say the newest alsa driver you mean the driver from alsa?

Which version did you compile?

Thanks in advance ;)

---

### Post by lessthantom on 2010-12-18
hey

i was having issues for a while with this. i have an ati radeonhd 3200 (i think) with a dvi to hdmi cable

turns out the reason it wasnt working was the ATI propreitary drivers it worked when i installed ubuntu 10.10 then stopped after a installed the drivers. Uninstalled and then it worked again so. people having issues try that

---

