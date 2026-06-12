---
title: "Phonograph conversion in Feisty?"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by christian.convey on 2007-07-05
Can anyone recommend a good tool or set of tools for ripping a phonograph in Feisty?

I've tried Audacity, but it's noise reduction filter really killed the recording.

I've looked at gramofile, but it won't (happily) install on Feisty due to package conflicts.  Too bad, because it's reported to have an excellent noise / pop filter.

- Christian

---

### Post by John.Michael.Kane on 2007-07-05
Most of the guides I've seen on this call for Audacity or GramoFile.

Heres some guides that may help with any issues or errors.

[http://junocake.blogspot.com/2007/03/ripping-vinyl-with-gnulinux.html](http://junocake.blogspot.com/2007/03/ripping-vinyl-with-gnulinux.html)
[http://home.att.net/~halbower/music.html](http://home.att.net/~halbower/music.html)
[http://www.linux-sxs.org/multimedia/vinyl.html](http://www.linux-sxs.org/multimedia/vinyl.html)


Another option is to have a chat with ubuntustudio folks here [http://ubuntuforums.org/forumdisplay.php?f=254](http://ubuntuforums.org/forumdisplay.php?f=254) or on irc #ubuntustudio

---

### Post by dabl on 2007-07-05
I use Audacity to do the capture, and Gnome Wave Cleaner (gwc) to do the de-clicking, de-crackling, and de-noising.

Don't use Audacity to do the noise filtering, just to normalize the level.  I capture at 48,000, 32 bits, and save that file as a .aup.  Then I export it to a 16-bit .wav to process with gwc.  You should review the gwc material at [http://gwc.sourceforge.net/](http://gwc.sourceforge.net/)

Don't forget the cartridge and stylus -- that is probably the biggest opportunity to get good quality. :popcorn:

---

