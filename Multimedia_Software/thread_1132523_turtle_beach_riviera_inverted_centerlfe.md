---
title: "turtle beach riviera inverted center/lfe"
date: 2009-04-21
forum: Multimedia Software
---

### Post by badllama77 on 2009-04-21
Okay so I got a turtle beach riviera card and it works fine except for the fact that the versajack when set to center/lfe seems to invert the two.  This could be something wonky with the old logitech speakers I have but I wanted to see if there was a way to fix this, with asound or something else.

i.e. heeeelp :???: ](*,)

thanks

---

### Post by badllama77 on 2009-04-22
Ok so I think I am closer to where I need to be I found some info on using ttables to reverse channels but I am still lost on how to apply it.

I tried:
pcm.!surround51 {
type route;
slave.pcm dmix; #not sure what this should be
ttable.4.5 1;
ttable.5.4 1;
}

This produces no sound at all with 
speaker-test -c6 -Dplug:surround51

Then I just tried 
pcm.ch51 {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.2.2 1
         ttable.3.3 1
         ttable.4.5 1
         ttable.5.4 1
}

this works with speaker test but I have no earthly idea how to get myth to use it.  I tried ALSA:ch51 to no avail.

I would like to set this up as the default for surround51.
How do I do that if I try 
pcm.surround51 
{
...as above without slave
}
It complains with this because there is no slave, what would the slave be for that.

thanks

---

