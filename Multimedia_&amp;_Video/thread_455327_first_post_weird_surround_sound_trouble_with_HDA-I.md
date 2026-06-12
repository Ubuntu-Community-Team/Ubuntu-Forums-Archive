---
title: "first post: weird surround sound trouble with HDA-Intel ALSA driver"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by ckirov on 2007-05-26
Hi,

I'm running a stock feisty 32bit install on a gigabyte 965p-ds3 motherboard with integrated Realtec ALC883 7.1 sound. ALSA sets the sound driver as  HDA-Intel. Unfortunately, the driver does not work correctly with Logitech X-540 5.1 speakers.

In ALSA's view, the rear speaker port and side speaker port are switched. This means that using the surround51 mode from ALSA (e.g. when watching a DVD), there is no rear signal from the surround speakers unless they are plugged into the side speaker port. When the rear speakers are plugged into the rear port, they act as duplicates of the front channels (as the side speakers normally would for a 5.1 device).

Normally, this wouldn't be a problem, as I can just switch the cables. However, I dual-boot with Windows XP (where everything works perfectly, incidentally) and I don't want to reach to the back of my PC everytime I switch OSes.

My solution was to use a custom ALSA pcm device defined in ~/.asoundrc:

pcm.my51 {
     type route
     slave.pcm "surround71"
     slave.channels 8
     ttable.0.0 1
     ttable.1.1 1
     ttable.2.6 1
     ttable.3.7 1
     ttable.4.4 1
     ttable.5.5 1
     ttable.6.6 0
     ttable.7.7 0
}

This routes the rear speaker signal to the side speaker port. However, since it is based on the 7.1 surround71 device, it only seems to work on players that can be told I have 7.1 speakers. At this point, I can only get Xine to behave correctly.

Any ideas? Does this seem like a bug in the HDA-Intel driver (someone misread a diagram of the speaker ports)?

Sorry for the long first post.

Thanks.

---

