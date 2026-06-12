---
title: "No sound in mplayer or gxine"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by diabolik on 2007-10-02
Hello all -

I'm having trouble getting any sound out of mplayer or gxine.  Rhythmbox and Totem produce sounds just fine.  I've tried pretty much every possible combination of options on the Audio preferences tab in mplayer.  The frustrating thing is that I can see the volume levels rising and falling in the Volume Meter when I set the driver to "esd", but nothing comes out of the speakers.  I spent quite a while messing with the gnome volume controls and alsamixer, cranking up every possible channel, but the speakers refuse to utter a sound.

I've been through the comprehensive sound guide, but didn't find the solution.  I do have two soundcards, which might be complicating things.  I'm trying to use the onboard sound on my Asus A7N8X deluxe (nForce2).  There's also an old Turtle Beach card in there with an Aureal Vortex au8830.

Any tips at all would be appreciated...

Thanks!
Mark

---

### Post by diabolik on 2007-10-03
In case you're all in suspense, this has been fixed!  But I have no idea how.

After about an hour of searching, config editing, and knob twiddling, I decided to try to get the Turtle Beach card working.  I was able to get the Turtle Beach to exactly the same state as the nForce2 audio - sound was working except in mplayer and gxine.

I decided to switch back to the nForce audio, since it's supposedly better, and voila... suddenly everything works.  Maybe I just had something turned down somewhere, but I swear I tried everything.  At some point I vaguely recall editing some sound file that set a preference of one soundcard over another, but it didn't seem to work at the time... maybe that combined with knob twiddling did the trick.

---

