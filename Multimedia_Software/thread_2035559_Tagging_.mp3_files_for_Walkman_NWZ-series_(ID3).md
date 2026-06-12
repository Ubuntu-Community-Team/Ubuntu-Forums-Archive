---
title: "Tagging .mp3 files for Walkman NWZ-series (ID3)"
date: 2012-07-30
forum: Multimedia Software
---

### Post by newb85 on 2012-07-30
I haven't seen anyone ask yet, but this is an issue that caused me a lot of headaches before I figured it out.  My specific player is an NWZ-E345, but I'm sure this is applicable to several similar models.  Except for these issues, I love the player, which was inexpensive, has great battery life, and is virtually indestructible.  

Problem #1 - The player will not read ID3v2.4 tags at all, which is problematic since 2.4 is currently the default in the Linux world.

Problem #2 - The player will read ID3v1.x tags, with the exception of the track numbers, which means that if 1.x tags are present, the songs will be played out of order.

Problem #3 - If both 1.x and 2.x tags are present, the player reads the 1.x tags (which makes no sense), resulting in Problem #2 persisting despite the presence of 2.x tags.

Conclusion - To avoid these problems, use tagging software that allows you to force the tags to 2.3 and strip any 1.x tags.  I use EasyTag (from the repositories).  It takes a little to learn, but it's powerful and good for large batch processes.

Hope someone finds this useful!

---

