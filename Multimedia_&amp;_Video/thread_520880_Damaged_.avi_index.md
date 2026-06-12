---
title: "Damaged .avi index"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by Pitbull11188 on 2007-08-08
I have a 15 .avi files with damaged indexes. When running them under windows on the family computer using XP and VLC, vlc automatically fixes the index and plays the file flawlessly. I put them on my computer running feisty and VLC just plays them, the problem is there is a 1inch greenbar at the top of the screen that "pushes" the video down and cuts off the bottom.

Could anyone help me fix these, I couldn't find anything (non windows) and I googled for 30 minutes.

---

### Post by benanzo on 2007-08-08
Mencoder/MPlayer will fix the indexes on broken files.

```
mencoder damaged_file.avi -idx -oac copy -ovc copy -o fixed_file.avi
```
**-idx** tells it to fix and rewrite the index
**-oac** is the audio codec to use (in this case just copy it as-is)
**-ovc** is the video codec to use (in this case just copy it as-is)

Good Luck!

---

### Post by iNfernum on 2007-11-09
I have the same problem. tried what mentioned above, worked but it only retrieved 7 mins from a 45min avi file.

---

