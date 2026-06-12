---
title: "How to get subtitles working with TV out on ATI"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by jdusablon on 2006-12-29
Just building a simple multimedia box for movies, photos & music on my TV using ATI TV-out.

My first problem was getting TV out working at all with my ATI 9600 AGP, but I solved that by simply installing fglrx driver. Plenty of guides on that out there, so I won't go into it.

The irritating problem was the lack of subtitles showing on tv output... worked fine on VGA out. I just wanted to watch DivX video with japanese audio and built-in subtitles **(READ, no separate SRT files!)** This also works correctly with my DivX-compliant DVD player (NTSC.)

**The issue is overlay.**

To manually disable overlay, edit **/etc/X11/xorg.conf** and find the following section:```
Option      "VideoOverlay" "on"
```and change it to read:```
Option     "VideoOverlay" "off"
```******* This may slow down your system if you're using an older/slower CPU and this may not be the answer you're looking for, since disabling Overlay makes the CPU to the job of hardware acceleration for video.

The more elegant solution is to change the way the fglrx driver either clones or mirrors video output for multi-headed cards so that overlay is enabled on both/all video outputs. I don't yet know how to do that.

Any input on the better and more elegant solution is welcome!

Cheers.

---

