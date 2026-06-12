---
title: "Map midi keyboard controls rosegarden"
date: 2007-11-21
forum: Multimedia Production
---

### Post by mpgarate on 2007-11-21
how can I map the pretty controls on my new m audio oxygen 61 midi keyboard in rosegarden? I managed to get sound to come through and play around with the different synths, but I want to map my knobs and dials to their functions

---

### Post by Stochastic on 2007-11-22
well I'm no rosegarden expert but any midi controller with different knobs will be sending midi data on a different channel for each knob/slider/pad/joystick/pedal/etc.. so if you've got midi sending into rosegarden then it's a matter of finding which channel each knob is talking on, then setting the propper functions in rosegarden to listen to those channels.

If you get stuck trying to figure out which channels the knobs are talking on then I'd suggest working in PD for that task.  Let me know if that's the case and I'll post more info on how to do that as PD can be kinda confusing.

---

### Post by thundercles on 2008-04-11
Yeah, I had my Oxygen 61 mapped out perfectly to rosegarden and amsynth a couple years back when I had a pretty good music production setup in PlanetCCRMA on FC4 or 5. Now I have it set up again in 8 and I'm right where you're at, only it's more frustrating cause I remember what I could do with midi mapping. If all else fails there should be some promising midi controls -> GTK+ packages floating around I think I ran into a couple before and you could just map that way to anything, that's what I plan on doing for stuff like zynaddsubfx.:guitar:

Edit: oh and I used you as my referral user cause this thread finally got me to sign up for the ubuntu forums, they are always the first thing that pops up on google so I might as well even though I'm a debian and FC user. I was going to install Ubuntu and ended up helping people in the freenode #ubuntu room with problems on a couple occasions for like 3 hours each.....

---

