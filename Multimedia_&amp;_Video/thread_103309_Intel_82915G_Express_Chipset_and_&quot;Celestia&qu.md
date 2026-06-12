---
title: "Intel 82915G Express Chipset and &quot;Celestia&quot;"
date: 2005-12-13
forum: Multimedia &amp; Video
---

### Post by gbutler69 on 2005-12-13
I have Intel 82915G Express Chipset video. The DRI and correct Xorg drivers appear to be loaded (i810). However, thought most 3D things work ("Tux Racer" e.g.) I find that "Celestia" does not work correctly. In particular, it does not render planets images (Earth, Mars, etc). Instead, it only renders faint and garbled outlines of the planets (when "Show Clouds" is on, if off, shows nothing). "Celestia" is the one 3D application I'm really interested in using. The games and such don't matter to me at all. I've noticed, that if I login as "Different User" (creating a 2nd X Session), and run Celestia in there, it runs via Mesa Software emulation rather than DRI and it appears to work (though extremely slowly). This seems like a 3D driver problem to me. Something with rendering "Textures" or something like that. Any ideas what to do or how to proceeed? Thanks in Advance.

---

### Post by jobezone on 2006-02-14
I'm having the exact same problem as you, and haven't solved it yet.

I'm thinking of installing a snapshot of the i810 driver found at [http://dri.freedesktop.org](http://dri.freedesktop.org), but because this computer is not mine, I don't want to possibly screw it up, and not having a easy way to get the old working driver back.

Hopefully, celestia 1.3 in dapper will have this fixed.

---

