---
title: "no sound-card... tried everything?"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by scacinto on 2007-01-11
Hi All,
     This is my first post as I've been relatively self-sufficient to this point.  Problem is, (apparently) the last kernel update broke my sound.  I've attempted every step as outlined in the "Comprehensive Sound Problems Solutions" page 

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

but still no go.  I have uninstalled, reinstalled, and reconfigured alsa, twice.  The module-assistant didn't work, so I went with downloading the drivers from alsa (1.0.13) and compiling them myself with my sound-card in the configure line  (--with-cards=ice1712).  As stated, i have a Delta 44 with the ice1712 chipset.  When I try alsamixer, the old error "No ice1712 cards found" pops up.

Any ideas?  Anything is appreciated.

Thanks,

-S

---

### Post by scacinto on 2007-01-11
Solved my own problem.  (I think).   After reconfiguring, in the shell, type

sudo /etc/init.d/alsasound restart

Now at least I have the alsamixer... we'll see about sound.

-S

---

