---
title: "nuvexport and ffmpeg problem"
date: 2009-06-13
forum: Mythbuntu
---

### Post by drjenk on 2009-06-13
Hi,
I have been able to fix every little problem so far with some searches on the various docs and wikis, but haven't been able to find one for this. 
 
I can get videos to transcode ok into a *.nuv file.  When I run nuvexport to try and export some shows, I get the following:
 
Using ffmpeg for exporting.
What would you like to do?
 
  1. Export to XviD (disabled)
  2. Export to SVCD
  3. Export to VCD
  4. Export to DVCD (VCD with 48kHz audio for making DVDs)
  5. Export to DVD
  6. Export to DivX (disabled)
  7. Export to ASF (disabled)
  8. Export to MP3
  9. Export to PSP (disabled)
 10. Export to MP4 (iPod) (disabled)
 11. Export to .nuv and .sql
 
  q. Quit
 
 
Why all the "(disabled)"? I do see on a page somewhere I found, something to the effect "you need to get the latest ffmpeg". I went into the package manager, it appears I have the latest ffmpeg, and libvcodecs. What can I be missing? I'd sure like to copy of some shows for a vacation I have coming up shortly.
 
thanks for any help/suggestions.

---

### Post by klc5555 on 2009-06-13
> **drjenk said:**
> Hi,
I have been able to fix every little problem so far with some searches on the various docs and wikis, but haven't been able to find one for this. 
 
I can get videos to transcode ok into a *.nuv file.  When I run nuvexport to try and export some shows, I get the following:
 
Using ffmpeg for exporting.
What would you like to do?
 
  1. Export to XviD (disabled)
  2. Export to SVCD
  3. Export to VCD
  4. Export to DVCD (VCD with 48kHz audio for making DVDs)
  5. Export to DVD
  6. Export to DivX (disabled)
  7. Export to ASF (disabled)
  8. Export to MP3
  9. Export to PSP (disabled)
 10. Export to MP4 (iPod) (disabled)
 11. Export to .nuv and .sql
 
  q. Quit
 
 
Why all the "(disabled)"? I do see on a page somewhere I found, something to the effect "you need to get the latest ffmpeg". I went into the package manager, it appears I have the latest ffmpeg, and libvcodecs. What can I be missing? I'd sure like to copy of some shows for a vacation I have coming up shortly.
 
thanks for any help/suggestions.

Don't you just hate ffmpeg sometimes? Most of the time? I know I do.

Anyway, usually you get the "(disabled)" outputs when your ffmpeg has not been compiled with those particular options included. Unfortunately, you may also get that particular type of output when a library or dependency for that particular option has not been properly met, or even when ffmpeg is not running at all. Try running "ffmpeg -version" from a prompt to see what ffmpeg thinks it's able to do, and what options it's been compiled against. If it fails of a particular library or dependency, then you know where to begin.

But a couple of general observations. First, despite its name, nuvexport handles .mpg files perfectly well, so you don't need to transcode mythtv recordings from .mpg to .nuv before using it. The unnecessary extra transcoding just lowers the quality of the final product.

Second, ffmpeg may be the fastest encoding option for nuvexport, but it's not necessarily the best one. For the formats that they're able to handle --they can't handle them all --transcode and mencoder consistently produce higher quality output than ffmpeg. Now, I don't know what format you're exporting to, but running "nuvexport --transcode" or "nuvexport --mencoder" rather than the default with ffmpeg might be worth experimenting with.

Don't forget to consult the nuvexport wiki page at: [http://www.mythtv.org/wiki/Nuvexport](http://www.mythtv.org/wiki/Nuvexport)

Good luck!

---

