---
title: "MythTv - Screwy Graphics - Ati"
date: 2009-04-05
forum: Mythbuntu
---

### Post by rukie on 2009-04-05
Hey Guys,

I just installed mythbuntu 8.10 (was using 8.04) but I'm having trouble with my ATI Radeon 2400 HD pci express card. The drivers seem to have installed fine for it, and gnome works perfectly well. Videos play fine in firefox (hulu for example). I even have the 64 bit version working with the new 64 adobe flash driver :-)

The problem though, is that when I load mythfrontend, all of the graphics are horrendously messed up. Its disfigured, and I can't see/read anything. Any ideas on what might be causing this?

Also.
I have two tv tuner cards. A phillips using bt878 drivers, and a pchdtv 5500. Neither of them are giving me audio in analog, and I can't attempt watching HD using vesa graphics. The pchdtv 5500 does have a cable that comes out the back and plugs into the line in, but does the phillips require a cable like that too? 

Thanks!

---

### Post by rob3435 on 2009-04-05
Similar to a crazy checkerboard pattern?

[http://ubuntuforums.org/showthread.php?t=966640](http://ubuntuforums.org/showthread.php?t=966640)

Add this to the end of /etc/mythtv/session-settings

```

export LIBGL_ALWAYS_INDIRECT=true

```

---

### Post by rukie on 2009-04-06
Worked like a charm, Thanks!

---

