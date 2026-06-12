---
title: "HOWTO: Thomson Scenium 30LCDB03B LCD TV"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by bedfojo on 2007-07-19
Just thought I'd post this as a HOWTO in case anyone else might be suffering too!

I have a Thomson Scenium 30LCDB03B TV (LCD flat screen). I also have a new media PC (built to spec running Ubuntu 7.04). I had a horrible time getting the TV to display in widescreen - the TV always defaulted to a 1024x768 display even if X was outputting widescreen. NB I have a nVidia Corporation G70 [GeForce 7600 GS] graphic card.

I loaded the newest nvidia drivers using Envy. But did not use autoconfigure, as it just borked X. 

NB: I'm using a DVI cable connector.

In the end I hacked my xorg.conf file (relevant parts attached). The key parts are where it says:

Option		"UseEDID"		"False"
Option		"ConnectedMonitor"	"DFP"
Option		"ExactModeTimingsDVI"	"True"
Option		"ModeValidation"	"NoDFPNativeResolutionCheck"

This is because the TV lies really badly with its EDID info and even about its maximum screen resolution.

Hope this helps anyone else with this TV. It now looks lovely in Ubuntu.

As an aside I suspect this would have been impossible under another well-known OS. +1 for linux.

---

