---
title: "Reverse sound from speakers"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by ddygu on 2006-06-05
Hello

Since I updated recently to newest ubuntu, sound in video games (I assume any where else also, can't really test it) is reversed. Stuff that happens on my left comes out from the right speaker, and the left speaker plays stuff that happens on my right. I had the same problem before, after updating to new ubuntu also. I solved the problem by plugging in headphones to the headphone jack on the speakers, and that seemed to fix it. After some other updates, the problem went away completely, and I did not have to use headphones. After this update, the problem is back, and even plugging in headphones trick doesnt work. 

I'm using ALSA.

Any help is appreciated.

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

