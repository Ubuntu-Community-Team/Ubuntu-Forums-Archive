---
title: "Strange video conversion error with ffmpeg"
date: 2009-06-28
forum: Multimedia Software
---

### Post by Wug on 2009-06-28
I am using ffmpeg to convert some *.rmvb (real media variable bitrate) files, and they mostly seem to work fine.  however, one of them gets to 18%, puts up a warning saying 
> [warning]0xHEXSTUFF first frame is no keyframe
then hangs.  takes up all available processing power, but stops updating the terminal.  Is this a known issue, or is my video corrupted?  is there a fix?  Can I force a keyframe to be created?  Or can I just skip that frame or write the previous one to it?

THX in advance

Im on windows XP
im using ffmpeg svn snapshot 18639

---

