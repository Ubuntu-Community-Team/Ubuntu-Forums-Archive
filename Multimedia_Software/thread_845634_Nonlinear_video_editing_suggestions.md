---
title: "Nonlinear video editing suggestions?"
date: 2008-06-30
forum: Multimedia Software
---

### Post by ubtutu on 2008-06-30
Can anyone recommend a way of taking 90 minutes of DV video (type2 avi), of which I intend to discard around half, and perform the following:

1.) deinterlace the footage with a bob effect (which intelligently produces frames from fields, doubling the framerate)
2.) Applying transitions to various parts of the footage
3.) Export to x264

Previously in Windows I achieved the desired effect by using a combination of AviSynth, AdobePremiere, Virtualdub, and respective filters and plugins for those programs.

How do I do the same in Ubuntu? :)

I tried Kino, which appears to allow me to manually pipe video to x264, but I cannot find for example any way to apply a bob filter to the video.
Avidemux however lets me use a bob filter, but not edit and introduce transitions.

---

### Post by ubtutu on 2008-07-02
To re-cap, I want to double the framerate with a bob filter, add transitions, export to x264.

I am starting to think that the only way I can do this is to fire up a virtual machine, and install various windows apps.

Has anyone figured out a way to do this sort of thing already? Many thanks

---

### Post by ubtutu on 2008-07-11
In the end I just used kino to add transitions, outputting to DV. Then using avidemux with the DGBob filter to encode.

Kino was a bit fiddly as I am used to multi-track video editing. I am not sure if the DV output was lossless... The transitions could not be as they are new, but as for the original frames, I cannot tell.

---

### Post by Cresho on 2009-02-03
blender!  I use it for high definition video editiong.  It will take you a long time at first but after you get your workflow, you will be fine.

this is for very advanced users mind you.
here is a pic of my setup.
[http://forums.steves-digicams.com/forums/attachment.php?id=130257](http://forums.steves-digicams.com/forums/attachment.php?id=130257)

it took me a while to configure it this way.

---

