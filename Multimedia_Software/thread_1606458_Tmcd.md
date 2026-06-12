---
title: "Tmcd"
date: 2010-10-26
forum: Multimedia Software
---

### Post by editorreilly on 2010-10-26
I read on another forum that I can access the starting timecode on a quicktime clip on "Stream #0.2" Quicktime/AVID now embeds the stating time code from a video clip exported from an AVID.   I can see that it has this info by doing a ```
ffmpeg -i videoclip.mov
``` the output is ```
Stream #0.2(eng): Data: tmcd / 0x64636D74
``` along with a bunch of other info.  But what I'm most interested in is accessing the data from Stream #0.2. Particularly the tmcd code. Could anyone direct me into the right direction.  I've googled this death and nothing pops up.  

Thanks for any help.

---

