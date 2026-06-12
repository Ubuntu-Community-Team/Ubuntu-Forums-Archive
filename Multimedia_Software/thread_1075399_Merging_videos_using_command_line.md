---
title: "Merging videos using command line"
date: 2009-02-20
forum: Multimedia Software
---

### Post by Shady3D on 2009-02-20
hi all, there was a tutorial in Linux Journal about extracting mp3 from a video, so i was thinking is there a way to merge 2 videos without using avidmux or other editing program.

---

### Post by insineratehymn on 2009-02-20
Like... video a ends and video b begins?

---

### Post by Shady3D on 2009-02-20
no, i don't want to queue them i want both be the same file

---

### Post by insineratehymn on 2009-02-20
Right... like avi1 + avi2 = comlpeteAvi

---

### Post by Shady3D on 2009-02-20
yes

---

### Post by insineratehymn on 2009-02-20
> **Shady3D said:**
> yes

```
mencoder -oac copy -ovc copy file1.avi file2.avi -o full_movie.avi
```

Try that out. Mencoder is in the console and it comes with mplayer, so you should already have it. Replace file1 and file2 with appropriate file names and you will get full_movie.avi (you can change the name of that as well).

Don't be surprised if this takes a long time depending on the size of the original files.

---

### Post by detroit/zero on 2009-02-20
or install transcode```
sudo apt-get install transcode
```this will give you *avimerge*. then it's as easy as ```
avimerge -i movie*.avi -o mergedmovie.avi
```where movie* is going to be part1.avi, part2.avi, etc..

---

### Post by insineratehymn on 2009-02-20
> **detroit/zero said:**
> or install transcode```
sudo apt-get install transcode
```this will give you *avimerge*. then it's as easy as ```
avimerge -i movie*.avi -o mergedmovie.avi
```where movie* is going to be part1.avi, part2.avi, etc..
That will work nicely as well. =)

---

### Post by Shady3D on 2009-02-20
> 
$ mencoder -ovc copy vid1.flv vid2.flv -o full_movie.flv
MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 3.40GHz (Family: 15, Model: 6, Stepping: 5)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x84c4c91
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [VP6F]  320x240  0bpp  30.667 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x46365056  size:320x240  fps:30.67  ftime:=0.0326

No audio encoder (-oac) selected. Select one (see -oac help) or use -nosound.

Exiting...



so do u know whats the problem (thats for the first code)

for the second i am downloading the program now

---

### Post by insineratehymn on 2009-02-20
Post the output of this:
```
file <name of your movie/s>
```

Replace <name of your movie/s> with one of the two files you have, do this for each.

---

### Post by Shady3D on 2009-02-20
vid1.flv: Macromedia Flash Video

---

### Post by insineratehymn on 2009-02-20
Ahh, ok. That explains it. I thought you were messing with avis. 
```
mencoder -oac copy -ovc copy -o c:\video.flv c:\a.flv c:\b.flv
```

Try that?

---

### Post by Shady3D on 2009-02-20
i didn't quite understand the last code but anyway, i managed to get over that problem by converting to avi then merged them and both scripts worked fine, and thx for ur help

---

### Post by insineratehymn on 2009-02-20
You're welcome.

---

