---
title: "Rosegarden Soft Synths"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by RGBrasel on 2008-03-15
I'm primarily a Logic Express user, with hopes to upgrade to Logic Pro, once I can afford a Mac Pro (with Final Cut Pro), so in the interim,  I want to use Rosegarden with my old recently converted G4 Sawtooth and dual-boot XP box.  

I have two questions:

Where can I download the equivalent AU/VSTI softsynths for Rosegarden?

What development platform/SDK can I use to create soft synths for Rosegarden?  I'm a novice programmer (VB .NET--sorry, my job is in a VB.NET house for legacy code migration purposes--and a smattering of C++ and Java) and would like to start simply, like emulating the Prophet 600, ARP Solus, or Roland Juno 106.  (I'm also an analog/modular synth junky.)

Thanks!

Russell

P.S.  This is off thread topic, but does anyone know of a good relational database app?

---

### Post by eric71 on 2008-03-18
The equivalent in linux right now for VSTi is DSSI. The LV2 plugins are coming along, but not many hosts use them yet. Rosegarden can use DSSI plugins internally, and can even host most of your VSTi plugins via dssi-vst and wine. Rosegarden, can also output your MIDI tracks to external softsynths. For instance, if you want to use soundfonts, you can use the fluidsynth DSSi, or the external stand-alone Qsynth (which also uses the fluidsynth engine). 

For DSSI plugins, many of which are available in the standard Ubuntu repositories, read here:

[http://dssi.sourceforge.net/](http://dssi.sourceforge.net/)

For some good standalone synths that can be linked to Rosegarden with Jack google for qsynth, zynaddsubfx, phasex, whysynth, aeolus, and hexter.

---

