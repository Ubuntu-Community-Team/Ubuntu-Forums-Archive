---
title: "amr to mp3"
date: 2009-02-24
forum: Multimedia Software
---

### Post by sn0m on 2009-02-24
hi guys, is there any way to convert amr to mp3. I tried sound convert but no luck.
Reg Sokol

---

### Post by FakeOutdoorsman on 2009-02-24
I'm assuming you are using Intrepid.  You can do this with FFmpeg, but it will take some work.

1. Enable the [Medibuntu Repository](http://medibuntu.org/).

2. Update your repository and install libamrnb-dev and libamrwb-dev.
```
sudo apt-get update
sudo apt-get install libamrnb-dev libamrwb-dev
```
3. Follow this guide: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

4. Stop at step 5 in the linked guide.  Add some additional parapeters to the FFmpeg configuration line so it looks like this:
```
./configure --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-nonfree --enable-libamr-nb --enable-libamr-wb
```
5. Finish the guide and then try the following command:
```
ffmpeg -i input.amr output.mp3
```

If you are using Hardy, just enable the Medibuntu repository and then install FFmpeg from that.  There is no Medibuntu FFmpeg for Intrepid and the unstripped version in the Ubuntu repository doesn't support AMR.

There's probably an easier way to do this (online converters, other programs) but I'm a FFmpeg nerd.

---

