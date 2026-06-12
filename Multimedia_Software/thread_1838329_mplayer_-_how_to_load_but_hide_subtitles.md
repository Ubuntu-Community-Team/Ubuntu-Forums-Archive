---
title: "mplayer - how to load but hide subtitles"
date: 2011-09-03
forum: Multimedia Software
---

### Post by buffay on 2011-09-03
I'm using mplayer, subtitles are automatically loaded and visible, but I want to them to start them invisible so I could call them at any time later by pressing &quot;v&quot;. Now I have to press &quot;v&quot; every time I start the movie just to get rid of them. Is it possible?

---

### Post by SeijiSensei on 2011-09-03
You can do it in **smplayer** by toggling Subtitle Visibility in the Subtitles menu.  If you close the program with the subtitles toggled off, the next time you use smplayer it will remember that setting.

I looked in vain for a way to do this using mplayer itself.  I tried the -nosub option, but I then couldn't toggle the subtitles off and on.  Using -nosub appeared to disable them entirely.  (I tested on a Matroska file with embedded *SS subtitles; I don't know what would happen if the subs were in a .srt file.)  I looked at all the subtitle options in "man mplayer" without success.

---

