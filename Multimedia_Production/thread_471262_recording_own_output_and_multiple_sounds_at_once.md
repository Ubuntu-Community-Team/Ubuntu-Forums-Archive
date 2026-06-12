---
title: "recording own output and multiple sounds at once"
date: 2007-06-11
forum: Multimedia Production
---

### Post by toasterman25 on 2007-06-11
Hi everyone,
Not heard of Ubuntu Studio - thought this could be the right place to ask...this:
Is it easily possible to record your own output? And any way to get multiple sounds?

I'm a Windows user slowly converting to Linux, I sometimes play a web stream and then record it back in (currently) Adobe Audition.
I've had a look in the mixer applications and there doesn't seem to be an option to pick the output as the input...for recording.

Playing two sounds at once on Ubuntu doesn't seem to work - I get a message that the sound device is already in use. Is there a way to split it so I can play both at once? Windows XP seems to be able to play the 3-4 at once that I occasionally need.

Any help much appreciated.

-Ben-

---

### Post by eric71 on 2007-06-14
The Jack sound server will allow you to do this. It is like a patchbay allowing you to hook the output from any jack aware program into the input of another. You will need to use an audio player with a Jack output plugin (I'm pretty sure xmms and anything using the Xine engine have this available, not sure about gstreamer based apps). Then you can use qjackctl to hook this to a recording program such as Ardour, or a recent version of Audacity that supports Jack.

---

