---
title: "Metadata on a DVD video - possible?"
date: 2012-09-21
forum: Multimedia Software
---

### Post by George Heine on 2012-09-21
Is there a place to write metadata on a DVD video disc?  (for home videos, this might be information about location, time, persons, equipment used, chapter offsets, etc.)  Of course, it would be possible to write the data to a graphics file, convert that into a short video clip, and add it to the DVD.  But I'm talking about metadata in the form of a text file or database.

Looked at several commercial DVDs, assuming there might be a file on there somewhere with copyright information, etc.    Most of them have two directories, "AUDIO_TS" and "VIDEO_TS".   AUDIO_TS seems to be always empty (on one DVD it was missing).   The VIDEO_TS diretory has a number of files with extensions BUT, IFO, and VOB.   The BUT and IFO seem to be very sparse data files, although sometimes there were short text strings at offsets 0x000 and 0x100.

Did find one DVD that had a third directory, "JACKET_P", which contained three MP2 files.

Anyway, no luck on finding any actual metadata, except for possibly the short text strings at the beginning of VIDEO_TS.IFO and VIDEO_TS.BUT .  Is it possible at all to write metadata to a DVD video?  

thanks for any help!

---

### Post by George Heine on 2012-10-07
Did some further research and experimenting on this topic.  The DVD-video format seems to be at least partially proprietary.  But I did find some examples of DVDs that had other things besides the AUDIO_FS and VIDEO_FS directories, mostly Windows executable (.exe) files for unknown purposes.

So, I decided to try something out.  Created a DVD with the [tovid]("http://ubuntuforums.org/showthread.php?t=183936") command line suite.  At the last step, after creating the menu and dvdauthor XML file, I used ```
tovid dvd <xml-file>
``` (*without *the **-burn** option) to build a copy of the DVD file structure on my hard disc.  Manually typed in a short text file and copied it to the top level directory of the file structure.  After verifying with ```
du -csk <location of top-level directory>
``` that the amount of data did not exceed capacity of the disk, ran```
 tovid dvd -burn <location of top-level directory> 
``` The resulting disc, with the text file, loads with no problems on two different DVD players.  So the answer seems to be "yes", it is possible to include some metadata text on a DVD video disc.

Am marking this thread Solved, but will continue to experiment and report on any limitations of this method.

---

