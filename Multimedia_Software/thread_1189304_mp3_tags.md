---
title: "mp3 tags"
date: 2009-06-16
forum: Multimedia Software
---

### Post by gramsyn on 2009-06-16
I have some mp3 files and their tags were written in Greek language. However the Rhythmbox Music Player and the Easy Tag Creator cannot read some tags (when I write Greek tags in my system, they are identified normally). Is there any possibility to read them (by changing a language encoding perhaps)???

Thanks in advance

---

### Post by _whistler_ on 2009-07-03
I had the same problem. The problem weren't the fonts used by rythmbox, but the tags themselves. I installed EasyTAG (sudo apt-get install easytag) and used it to update my tags. Specifically, I selected the mp3s with the unreadable characters, clicked on the Scan File(s) button and scanned the selected files. This resulted to their tags being rewritten in readable form. 

Note: I first wet to Settings>Preferences and selected the UTF-8 (unicode) character set, in the Character Set for writing ID3 tags group. I don't know however if this affected the final result.

Hope it works for you.

Cheers

---

