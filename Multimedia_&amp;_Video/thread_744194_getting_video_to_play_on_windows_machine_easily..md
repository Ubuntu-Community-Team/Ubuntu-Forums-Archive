---
title: "getting video to play on windows machine easily."
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by Nutopia on 2008-04-03
Hello,

I created a video using gtkRecordMyDesktop. This created a .ogg file. 

At the end of the day, I need to put this video online for people to download. Most of the people downloading the file will be on Windows or Mac, and we have to assume that they won't be able to do much more than double-click the file and expect it to work. 

I tried to encode the ,ogg to avi using the following command:

```
mencoder <INPUT_FILE_NAME.ogg> -ovc lavc -oac lavc -ffourcc DX50 -o <OUTPUT_FILE_NAME.avi>
```

In ubuntu, the resulting .avi file plays perfectly. However, when I download the file to a Windows machine and try to run it with QuickTime, it is looking for more codecs (I think it wants the Divx one...? but I'm not sure?) 

Unfortunately, this will end up being much too complicated for the audience who needs to view the video. Does anyone have an idea on how I can easily get my .ogg video into a format that will be supported on a windows machine simply? 

I'm at a loss. If I can get this file playing on Windows in an easy way I will be saving myself about 1 extra hour every day!

---

### Post by xc3RnbFO8P on 2008-04-03
I convert .ogg to .avi with Devede, open (all files) 
input file (68 sec) 16.2 mb, output file 3.8 mb (MPEG-4 (DivX5, ffmpeg  720 x 576,  25 fps))

---

