---
title: "Turtle Beach Santra Cruz"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by rufus05 on 2007-05-29
I am using the Turtle Beach Santa Cruz card and I am using the primary output (green) for my headphones and I am using the PCM output to go to an receiver via digital coax.

I navigate to System -> Preferences -> Multimedia and select the different audio outputs  I am able to get sound from both but not at the same time.

When I select CS46xx the sound comes through my headphones and when I select CS46xx IEC 958 the sound comes through the receiver.

Is there a config file or something I can edit somewhere that will allow the sound to come through both at once? I'd like to be able to have sound out of both and I thought if I could just select both lines that would fix the issue.

This may not be possible, but I wanted to check and see if anyone else had done it.

Thanks.

---

### Post by michael117 on 2007-06-10
You'd need to look into some ALSA (sound for linux) configuration stuff. You would likely have to put in some stuff into your .asoundrc which is located in your home directory. It wasn't there by default for me so I just created one with settings for it. A problem I've noticed with the Santa Cruz is that once you link up the different outputs which are treated as separate devices, then the audio comes out of sync on them. I too am looking into fixing this problem and I think I might need to set up JACK which is a higher end audio thing that utilizes ALSA but I don't feel like adding more kernel modules and maybe even having to recompile my kernel with realtime support. Check out the ubuntu documentation about sound too. It's late and I don't feel like going into more detail or getting the links, sorry.

---

