---
title: "ffmpeg script help"
date: 2011-07-20
forum: Multimedia Software
---

### Post by Plasma_NZ on 2011-07-20
Ok here's what i want to achieve...

have some folders with avi files inside them, some of them have screwed up metadata, and couple that with vlc's current release there's a bug causing the files to be renamed to the metadata info.....

now...  i have this found this to work 

```
ffmpeg -i input.avi -metadata title="" -metadata author="" -metadata copyright="" -metadata comment="" -acodec copy -vcodec copy output.avi
```

I was wondering how to write a small script that would, scan through the folder, remove all files metadata and retain the original file-name using the above code, and if possible delete the old file that contains the screwed up metadata

---

### Post by andrew.46 on 2011-07-21
Perhaps something like the following would work:

```

for i in *.avi
do 
ffmpeg -y -i $i acodec copy -vcodec copy \
       -metadata title="" -metadata author="" \
       -metadata copyright="" -metadata comment="" \
       $i
done

```

Just be aware that the [COLOR="Red"]**-y**[/COLOR] option allows FFmpeg to *overwrite* the original file so I would test this first on a backup copy of your original .avi files to make sure it is exactly what you want.

---

