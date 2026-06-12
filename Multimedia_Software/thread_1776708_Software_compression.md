---
title: "Software compression"
date: 2011-06-06
forum: Multimedia Software
---

### Post by timbim on 2011-06-06
I'm head engineer for a community radio station.  One of our compressors has recently died and I want to replace it with software compression on our streaming machine.

I've been looking at VST/LADSPA/JOST etc and I've got nothing but confused.  Hence I'm coming here looking for help.

My spec is this.  We need a system to run a compressor and EQ, probably a graphic and a parametric.  The compressor needs to be multiband and have proper control of the compression curve.  A way of configuring it without too much command line work would be an advantage.  All needs to run on an Ubuntu server with not massive overhead as it's not exactly the latest hardware.  I suspect it would be possible to run WINE for windows requiring VSTs if needed.

I was hoping some of you good people might be able to point me in the direction of a suitable host and plugins to achieve the effect described.

Tim

---

### Post by Joe of loath on 2011-06-06
You're looking at JACK and Jackrack I believe.

---

