---
title: "Swapping left and right sound channels"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by roadkill on 2008-03-06
Awkward placement of a the power socket means I've had to swap the position of my left and right speakers for the cord to reach.  Is there a way to swap audio channels, so I can have the left hand channel on the right hand speaker and vice versa?  I haven't been able to find a setting that allows it.

---

### Post by thirdhaf on 2008-04-05
I was struggling with this myself and I found the following which may be useful if you are using ALSA.  First of all the ALSA FAQ is where I got this information: [http://alsa.opensrc.org/FAQ#How_can_I_tell_ALSA_to_swap_the_left_and_right_stereo_channels_on_my_soundcard.3F](http://alsa.opensrc.org/FAQ#How_can_I_tell_ALSA_to_swap_the_left_and_right_stereo_channels_on_my_soundcard.3F)

If you want the swap to work universally you need to create a file called 

```
/etc/asound.conf
```

In this file should be the following lines:

```
pcm.swapped {
    type         route
    slave.pcm    "cards.pcm.default"
    ttable.0.1   1
    ttable.1.0   1
}

pcm.default      pcm.swapped
```


And now you should be all set, hope this solves your problem.

---

