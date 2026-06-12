---
title: "kino framerate problem?"
date: 2009-09-30
forum: Multimedia Software
---

### Post by josvanr on 2009-09-30
hi

I'm using kino to edit files from my camcorder. I do some preprocessing
with mencoder: speed up the movie and mirror & flip:

mencoder CLIP0003.AVI -o clip0003.avi -speed 18 -nosound -ovc lavc -lavcopts vbitrate=16000 -vf mirror,flip

The resulting avi looks good when I play it back in totem. Now I 
convert it to .dv to do further editing in kino:

ffmpeg -i clip0003.avi -target ntsc-dv clip0003.dv

Now, when I load the .dv file in kino and play it back there, the 
play back goes way to fast (10 seconds or so while it should be 5 minutes). I don't understand what is going wrong. Any clues anyone?

josvanr

---

