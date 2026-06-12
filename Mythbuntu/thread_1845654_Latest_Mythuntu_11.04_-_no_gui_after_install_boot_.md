---
title: "Latest Mythuntu 11.04 - no gui after install boot -SOVLED"
date: 2011-09-17
forum: Mythbuntu
---

### Post by romanyiv on 2011-09-17
Been using ubuntu for few years now - and myth - so I'm not a complete newbie.  Did a brand new wipe and load to the latest mythbuntu release - installed fine - but the gui would not start.  CTRL-DEL-F1 would give you a console.  If you looked at dmesg it looked like the video driver was not loading....had RmInitAdapter failure.  After a lot of trial and error I saw  one thread where someone had reverted back to an older kernel - booted into the gui - and re-installed the newer gui.  That worked for me....I downloaded the next to the most recent kernal (and headers) - 2.6.38-10-generic-pae - booted up on that version (and it worked w/o any issues).  While on that version I removed 2.6.38-11-generic-pae and re-installed.  Rebooted - came up under that version....on to the next thing.   I like ubuntu because they do come out with new releases sooner but you do have this downside....

---

