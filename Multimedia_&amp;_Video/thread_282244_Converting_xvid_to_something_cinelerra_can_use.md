---
title: "Converting xvid to something cinelerra can use"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by honda on 2006-10-22
Hello, I'm trying to edit some videofiles from my digital camera with cinelerra. They are encoded in mpeg4 in an AVI container (xvid I think...) Cinelerra can open them directly but it behaves strangely, crashes and is generally unusable. 

I got the impression that it is stable with the right video format, but I need some advice how to convert it to something usable. So far I have tried
importing the avi file in Kino and exporting as quicktime. That works very well in cinelerra but the quality is lousy, seems as Kino cuts fps from 30 to something that lookes like 12 when importing mpeg4 for some reason. 

If anybody succeeded in editing mpeg4 with cinelerra I would be happy for some advice how to get there.

---

### Post by honda on 2006-11-13
So, I gave up on cinelerra for a while. But then after installing edgy I found this howto compile the new cinelerra 2.1 myself, so I thought I'd give it a try: 
[http://forum.ubuntu-fi.org/index.php?PHPSESSID=32e8eb5dff21756ed9032dfbfb8b4030&topic=6301.msg45334](http://forum.ubuntu-fi.org/index.php?PHPSESSID=32e8eb5dff21756ed9032dfbfb8b4030&topic=6301.msg45334)
I had no trouble following the guide and cinelerra now behaves really well. (After converting the .avi's to .dv with mencoder. Didn't work before, so it was actually old cinelerras fault and not my files...)

---

### Post by rudlavibizon on 2006-11-30
can you post the syntax for converting avi to dv please. I tried recently something similar but with no success.

---

### Post by honda on 2006-12-01
Hmm, actually I don't remember what I did. When I had compiled cinelerra 2.1 I found a file named .dv that I had created with mencoder (I think) some months ago that now really worked with cinelerra 2.1, but then I gave up again cause cinelerra wasn't really usable on an athlon 1800. It did work without crashing, just too slow to be usable.

---

