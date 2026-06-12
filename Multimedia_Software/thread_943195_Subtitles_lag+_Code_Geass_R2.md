---
title: "Subtitles lag+ Code Geass R2"
date: 2008-10-10
forum: Multimedia Software
---

### Post by FLCL on 2008-10-10
Alright, this is killing me. For whatever reason season 2 of Code Geass just keeps having subs that are behind. I've tried gg and eclipse, no problem with any other anime at all, just this season :(
.mkv files
using Mplayer(wont even play in vlc x.x)
soft subs

Like i said, it's only this one season, sorta annoying..making me sad that i can't watch it. Anyone else have this problem? know how to fix it? Please tell!

---

### Post by FLCL on 2008-10-10
Bump

---

### Post by aeiah on 2008-10-10
i dont know why its happening other than that they're badly encoded, but in mplayer you can adjust subtitle delay with the z and x buttons. - and + on the numpad do the same for audio, which i find useful.

---

### Post by FLCL on 2008-10-10
Thanks, i've tried that already though and it has seemingly no effect on the subs. Im going to try on another computer and see if it lags on there as well. I've noticed there is typically only 1 person out of like 80 comments that say they havet his problem...im so unlucky haha.

---

### Post by shirilover on 2008-10-11
The files you are referring to are encoded at 720p with h.264.
Also the subtitles need to be rendered onto the video as well.
These two things need significant processing power to achieve smooth playback.

You may want to try using the following switches for mplayer:
-lavdopts fast:threads=2:skiploopfilter=all

---

### Post by FLCL on 2008-10-20
How do i go about using this switch? I havnt toy'd with Mplayer all that much. Do i use it in terminal or a configuration file?

---

### Post by shirilover on 2008-10-21
Probably easier to edit ~/.mplayer/config and add the following:

lavdopts=fast:threads=2:skiploopfilter=all

---

### Post by belwar on 2009-04-27
Where do you guys go to download [code geass r2]("http://www.playtech-asia.com/p1001/Code-Geass-R2-Lelouch-Of-The-Rebellion-%28TV%29:-Complete-Box-Set/product_info.html")?

---

