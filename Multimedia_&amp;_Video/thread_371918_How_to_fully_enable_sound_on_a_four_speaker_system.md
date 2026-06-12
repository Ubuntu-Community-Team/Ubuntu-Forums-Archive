---
title: "How to fully enable sound on a four speaker system?"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by benton on 2007-02-27
Hi there, 

I installed Ubuntu 6.10 and now have a dual-boot box. My sound card is the Creative Audigy (an early model) and my speaker setup is two front speakers, two rear speakers, and a subwofer.

Under Windows XP the sound comes out of the four speakers (after setting my speaker setup properly On Windows Control Panel.) 

In Ubuntu I get sound only from the two front speakers, and the volume is rather low.

So how do I enable 4-speaker sound in Ubuntu?

Thanks for any help,

-Benton

---

### Post by Daveth on 2007-02-28
try installing gnome alsa mixer in Synaptic - lots of tweaking possibilities and 5.1 sound. Worked a treat with my Audigy2.

---

### Post by stueyboy on 2007-02-28
I'll second that one. Just make sure that the ALSA mixer is enabled then go into the speaker settings and add the relevant speaker volume controls as the default seems to be for the extra ones (i.e. not the front or sub-woofer) to be on minimum volume. Took me a while to work that out but the sound is smashing on my 6.1 audigy 2 system (even in Quake3Arena)

Stu

---

### Post by benton on 2007-02-28
> **stueyboy said:**
> I'll second that one. Just make sure that the ALSA mixer is enabled then go into the speaker settings and add the relevant speaker volume controls as the default seems to be for the extra ones (i.e. not the front or sub-woofer) to be on minimum volume.

Thanks, folks. That's exactly what I did and it worked wonderfully. Ubuntu forever! :)

Regards,

-Benton

---

### Post by Daveth on 2007-03-01
excellent news then !
Enjoy.

---

### Post by mac.ryan on 2007-03-01
> **Daveth said:**
> try installing gnome alsa mixer in Synaptic - lots of tweaking possibilities and 5.1 sound. Worked a treat with my Audigy2.

I tried the same (my laptop' integrated subwoofer doesn't work), but I can't get the mixer seeing the audio card: the only sound device the mixer sees is the modem one.

From the sound option / volume control, of course, I can choose between the two sound devices, yet... :-/

Any clue?

I tried "man gnome-alsamixer" to see if there is any option to run, but the man is just 21 lines...

Thanks!
I run on edgy.

---

