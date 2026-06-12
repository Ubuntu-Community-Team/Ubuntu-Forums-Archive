---
title: "Potentially beginnerish JACK problem"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by the_woof on 2007-10-21
So, I'm trying to configure JACK and JACK-RACK so I can plug in my bass and run it back out to my amp. I am able to start qjackctl and jack-rack successfully, and I can route sound from ZynAddSubFX (a soft synth) to the ALSA PCM playback device using the qjackctl interface. The problem I'm having is that my input jacks don't seem to be working with JACK. Earlier today, I somehow fanagled it to record into Ardour for a little while, but now it's stopped working again, and I can't figure out what I did (sorry :( ). 
The sound comes out of my amp when I play, but I think that's just hardware/ALSA play-through (even though I dropped all the line input-related levels in alsamixer, the sound doesn't change at *all* when I connect the input to the output in qjackctl). All that proves is that the input jack on the card is working. By the way, the card is a Creative SB Live, model CT4780. 

The bottom line is that JACK seems to think it can access the capture device, but really it can't... or something like that.

Thanks.

---

