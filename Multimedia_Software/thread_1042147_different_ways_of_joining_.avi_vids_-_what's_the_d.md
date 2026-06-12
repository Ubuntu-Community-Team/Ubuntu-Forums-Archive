---
title: "different ways of joining .avi vids - what's the difference?"
date: 2009-01-17
forum: Multimedia Software
---

### Post by joshzam on 2009-01-17
I've found two working solutions on this forum to my question: how can I combine two .avi files into a single video file? They are as follows:

using transcode:
```
avimerge -o new_file.avi -i file1.avi file2.avi
```

using mencoder:
```
mencoder -forceidx -ovc copy -oac copy -o new_file.avi file1.avi file2.avi
```

Can anyone explain the differences between these two methods? How will the resulting files be different? Is there any re-compressing going on?

---

### Post by andrew.46 on 2009-01-17
Hi,

Can I add to the confusion by also suggesting a method given in the ffmpeg FAQs:

```

$ ffmpeg -i input1.avi -sameq intermediate1.mpg
$ ffmpeg -i input2.avi -sameq intermediate2.mpg
$ cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg
$ ffmpeg -i intermediate_all.mpg -sameq output.avi

```

Further details can be found here: [How can I join video files?]("http://ffmpeg.mplayerhq.hu/faq.html#SEC30")

Andrew

---

### Post by joshzam on 2011-04-03
Still haven't found an answer to this. Anybody know?

---

