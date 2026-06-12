---
title: "nuvexport as an user job"
date: 2010-09-11
forum: Mythbuntu
---

### Post by avelach on 2010-09-11
Hi,

I've created two user jobs for exporting recordings to xvid and mp4 respectively (the nuvexportrc file is the default one):

nuvexport --infile="%FILE%" --path=<my_videos_path> --mode=mp4

nuvexport --infile="%FILE%" --path=<my_videos_path> --mode=xvid

The second job works flawlessly but the first one does not: logs show that ffmpeg starts, shows zero percent frames processed and then it finishes with no other warning/error.

However, when invoked in a shell as a normal user, both lines work flawlessly.

What can be wrong?

Thanks in advance.

---

