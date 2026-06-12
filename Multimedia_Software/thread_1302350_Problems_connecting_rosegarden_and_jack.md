---
title: "Problems connecting rosegarden and jack"
date: 2009-10-27
forum: Multimedia Software
---

### Post by redwasp on 2009-10-27
I just bought myself a fancy little USB MIDI controller, and I've been trying to make this work all night. My controller (Korg NanoKey) shows up on jack connect, and seems to work with rosegarden. The issue seems to be that rosegarden only has an input port on jack, and refuses to play back audio. I have no idea how to remedy this.
If you need anything else, I can post it.
Thanks!

---

### Post by markbuntu on 2009-10-28
I have a nanokey that I use with rosegarden and jack with no problems. What you need to do is connect the rosegarden midi out through a midi emulator like ZynAddSubFX or Tmidity and connect that output to jack. I usually run everything into ardour for recording/mixing/adding effects etc. Get patchage and use it to manange your connections. It makes it very easy.

There is a really good tutorial here:

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

---

