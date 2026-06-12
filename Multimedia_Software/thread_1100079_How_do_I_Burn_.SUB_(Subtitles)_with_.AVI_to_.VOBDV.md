---
title: "How do I Burn .SUB (Subtitles) with .AVI to .VOB/DVD?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by OzzyFrank on 2009-03-18
OK, this is the first time I have come across **.sub** files, but have already figured out how to load them into a player like **SMPlayer** while watching the **.avi** (helps if the prefix for both, and the corresponding **.idx** file, is exactly the same!). My question now is how do I get this to be included when I use a program like **tovid GUI** to convert the **.avi** into a DVD-compatible **.mpg** or into a ready-to-burn DVD structure with **.vob** files? I've seen some talk in forums about a few pieces of Windows software that can automagically include the subtitles as long as the filename prefixes are the same... so was wondering if there was something similar for Ubuntu. Thanks in advance.

---

### Post by pytheas22 on 2009-03-18
One solution would be to use avidemux to embed the subtitles into your .avi file--instructions [here]("http://en.flossmanuals.net/Avidemux/OverlayingSubtitles").  Then load the new .avi file with the embedded subtitles into tovid for burning.

Of course, the downside of this approach is that there's no way to turn the subtitles off--they're there permanently.  I'm sure there's a more flexible solution and hope someone else will point you towards it.

---

### Post by OzzyFrank on 2009-03-19
Thanks - while I prefer the option to be able to turn subtitles off, I've kept this tutorial for future reference, as there will be times embedding sustitles will be what I want.

---

### Post by MoonRiver on 2009-05-26
Mac users can try out freeware **ffmpegX**,which can merge videos and subtitles .srt and .sub to one files, and then you can burn merged Videos to DVD.

You can consult this guide:

[_**How to add subtitle files sub /srt  and videos to dvd on mac**_]("http://www.dvdburnermacosx.com/tutorial/how-to-burn-srt-sub-subtitle-to-dvd-on-mac.html#129")

---

