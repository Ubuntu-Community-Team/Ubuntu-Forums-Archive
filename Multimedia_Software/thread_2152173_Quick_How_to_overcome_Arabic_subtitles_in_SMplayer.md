---
title: "Quick How to overcome: Arabic subtitles in SMplayer are displayed from left to right"
date: 2013-06-07
forum: Multimedia Software
---

### Post by ENigma885 on 2013-06-07
**The Problem:**

Arabic, and generally right to left languages, subtitles appear flipped from left to right. (As viewed in the following screen)

[IMG]http://i3.minus.com/i1tUrjxE0Fulb.jpg[/IMG]

**Solution:**
I have encountered many posts suggesting to disable SSA/ASS Subtitles in SMPlayer (*Preferences>Subtitles>Fonts and colors>Enable normal subtitles*).
The solution works but deprives the user of controlling the subtitles' border, color, shadow, etc.

**[COLOR="#FF0000"]_A more logical solution_[/COLOR]** is to disable subtitle flipping MPlayer option. Here's how to do that:
1- Open SMPlayer *Preferences*
2- Select *Advanced* (from right menu)
3- Select *Options for MPlayer* 
4- In the *Options* box paste ```
-noflip-hebrew
```
*Note*: the Hebrew part in the option above does NOT change with Arabic. So, just paste it as it is with any Right-to-Left language.
5- Make sure you click *OK* to exit the Preferences window

**Final Result:**

With border, shadow and color configured as desired from SSA/ASS Subtitles option in SMPlayer's preferences

[IMG]http://i3.minus.com/ibudUJJCrapzut.jpg[/IMG]

***Note to moderators**: I've searched for a "How to" or "Tutorials" section but didn't find any. Please move the post to the correct section if there's one.*

---

