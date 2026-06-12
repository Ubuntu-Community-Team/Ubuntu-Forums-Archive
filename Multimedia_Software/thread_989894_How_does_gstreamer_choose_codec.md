---
title: "How does gstreamer choose codec?"
date: 2008-11-22
forum: Multimedia Software
---

### Post by ar-jar on 2008-11-22
Hi, I have a bunch of wma files (no DRM) created on Windows. On one of my Ubuntu systems I can show the Album and Year metadata using the Gnome Properties->Audio dialog. On the other system these are labeled "Unknown" in the same dialog on the same file. The dialog indicates different codecs on the two systems. I have the same difference in Totem when displaying the files in the playlist. I suspect that it is the wma codec that is used to extract this info and that I have a different set of codecs on my systems. Thus:

How can I see which codec the system uses for a certain media type?
Can I change this w/o uninstalling the codec (and without compiling)?

In Windows there is the MERIT parameter that you can change for each DirectShow filter. I'm looking for something similar but haven't found it after quickly browsing through some gstreamer docs.

Thanks!

Arto

---

### Post by ar-jar on 2008-11-22
After some more experimenting I realize that management of metadata varies: With m4a files created with Sound Juicer you see (at least with my codec pack) the album title but not the year. With ogg and mp3 the year is shown too. Is this just a fact of life or is there a fix? And how do I know which codecs that support which metadata?
-Arto

---

