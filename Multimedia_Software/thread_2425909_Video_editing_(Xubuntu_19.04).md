---
title: "Video editing (Xubuntu 19.04)"
date: 2019-09-01
forum: Multimedia Software
---

### Post by bold33 on 2019-09-01
Admin, relocate if needed. Thanks!

Im editing a video. I don't need to change its quality, fps' or the audio stream.

I only want to get rid of 30 seconds at the beginning and 40 at the end of the mkv file. This file is 600 MiB in size. I have tried both openshot and flowblade. No matter what profile I choose to save, the size of the resulting file is much bigger than the original file (a 20 factor).

How do I simply cut, without changing any other property of the original file?

Another question: If I use mkvtoolnix to mkv a file, it takes much less time than editing a video with flowblade or openshot. Why?

---

### Post by wildmanne39 on 2019-09-01
*Thread moved to **Multimedia Software a more appropriate sub-forum**.*

---

### Post by TheFu on 2019-09-02
**mkvmerge** can do this.  There might be a GUI version of that tool. I've never used it.

If the file is 60:00 long, then 
```
mkvmerge -o output-file.mkv  --split parts:0:30-59:20  some-input-file.mkv
```
This will only split on keyframes found after the time points listed, so it won't be exact frame splits most of the time.  No transcoding will happen. It is as fast as a file cp.

To my knowledge, mkvmerge is THE ONLY cutting tool that honors multiple audio tracks, subtitles and captions correctly with the splits too.  No video editor that I've tried does it correctly.

There is a tool called vidcutter, that is in a flatpak.  I pulled it down last month to try it again - used it 2 years ago and the developer was really responsive.  Since then, the packaging has been broken and the flatpak has never worked for me.  Definitely worth a try, might not work if you don't have the KDE libraries installed, though the flatpak includes 3-5 of them. It is nearly 1GB in side for the 33MB program. ;(

---

### Post by vanadium on 2019-09-02
With these full-fledged non linear video editors such as flowblade or openshot, you are transcoding the video and audio streams when you write out the edited result. This means that the video and audio is decompressed from the source files, then recompressed in the desired format for the output file. This is why it takes time, possibly a lot of time.

The size of the output file depends on the codec used and encoding settings. In your case, the result of codex and quality settings yields files that are significantly bigger. Decreasing the quality settings and/or changing the codec could result in a smaller file.

However, if all you want to do is trim pieces of the video away, you certainly should try to do this without reencoding. That way you do not loose any quality, because the streams remain unaltered, and it goes much faster. 

ffmpeg is another tool command line tool with which you should be able to cut without transcoding, even if it contains a range of streams. It will work on a multitude of container formats, not only mkv. Avidemux is a graphical linear video editor, also allowing to cut without reencoding, however I have the impression that it might not always work correctly.

---

### Post by TheFu on 2019-09-02
**mkvmerge** doesn't require that the input file use an mkv container.  I've not found any codecs it didn't support, but the output file must go into an mkv container.

ffmpeg is pretty amazing and it can be used to copy streams.  The format of the options have changed a number of times so which format is needed for the specific variant installed on a system may not work like it did 3 yrs ago. I find it frustrating, but it can definitely be used, once the correct method of specifying the options needed is discovered.

---

