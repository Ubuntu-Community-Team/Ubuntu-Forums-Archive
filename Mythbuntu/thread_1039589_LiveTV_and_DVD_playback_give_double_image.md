---
title: "LiveTV and DVD playback give double image"
date: 2009-01-14
forum: Mythbuntu
---

### Post by SteveGodfrey on 2009-01-14
When running MythTV I get a double image when watching a DVD or Live/Recorded TV. Navigating the menus is fine.

Here's a screenshot.
[IMG]http://picasaweb.google.com/lh/photo/U_JReOJJs4vQEwq0oQZ23w?feat=directlink[/IMG]
[screenshot]("http://picasaweb.google.com/lh/photo/U_JReOJJs4vQEwq0oQZ23w?feat=directlink")

I'm running a combined Backend/Frontend on a HP Laptop using an ATI graphics card and the ATI driver.

Here's the relevant part from xorg.conf

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
	Option      "TexturedVideo" "on"
EndSection


Any ideas/suggestions?

Thanks

---

### Post by JugeHuge on 2009-01-15
Hullo.. Change different deinterlacer than bob from playback profiles or try differen playback profiles.. 

[Playback_profiles]("http://www.mythtv.org/wiki/index.php/Playback_profiles")

---

