---
title: "How to convert AVI video to smaller format"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by geovino on 2007-11-12
I have a 43MB AVI video and I would like to convert it to another video format that makes it a smaller size. What program can do this and what file type should I convert it to?

---

### Post by Unterseeboot_234 on 2007-11-12
ffmpeg is the library that can be used stand-alone with the command line. google for the discussion list and some people use quite lengthy command lines with tweaked option flags to convert.

I like the GUI front-end for ffmpeg -- Kdenlive. Pretty good at release .5. You might grab 8 seconds of trimmed video from your original video and experiment with the various formats and picture sizes. I would guess that the Flash .swf will be the smallest file size, but on the other hand Shockwave Files are youtube size and picture quality.

Both ffmpeg and Kdenlive are in the repositories.

---

### Post by erginemr on 2007-11-12
ffmpeg is a pretty good video converter indeed. You can install it with:
sudo aptitude install ffmpeg. 

The package also includes a simple video player (ffplay). In its simplest form, you can convert a movie with:
ffmpeg -i input.ext1  output.ext2 

and the type of ext2 defines the output format. It supports quite a few of different popular video formats out of the box, including avi, mpeg, mov, wmv, ogg and what not.

---

### Post by TKR101010 on 2007-11-12
Personally I use Kino and convert the videos to .flv format and that usually makes them a lot smaller than they started.

---

### Post by erginemr on 2007-11-13
Kino is very good, but it needs to import the files into DV format, which takes some time. Another graphical program you can use is Avidemux, which also allows converting video files to different versions and doing some simple tasks on them such as trimming and appending.

---

### Post by geovino on 2007-11-13
I installed Avidemux and I'm trying to open the AVI file and convert it to a lighter weight format. Where do you convert the file?

---

### Post by erginemr on 2007-11-13
You should select the video and audio codecs from the main menu and use "save as". I know it is a strange way to convert, but this is how it is...

You may also try kino, which uses the ffmpeg backend that we have mentioned before for conversions and has a more familiar conversion interface with video-audio quality settings.

---

### Post by eye208 on 2007-11-13
> **geovino said:**
> I installed Avidemux and I'm trying to open the AVI file and convert it to a lighter weight format. Where do you convert the file?
Conversion is done on saving the file.

You can control the output format using the controls on the left. By default both video and audio stream formats are set to "copy" which means the streams are copied to the output file without modification. Of course this is not what you want, so you have to choose some other format instead of "copy". x264 will give you the smallest video file sizes, i.e. minimal loss of quality. AAC is the smallest for audio. You can also adjust the bitrates, use multi-pass encoding for optimized quality etc. If the video has black borders, you might also want to crop the picture to remove them. You can also scale the video down to a smaller size before encoding to the final format. There are lots of options to play with.

---

### Post by erginemr on 2007-11-13
> **eye208 said:**
> Conversion is done on saving the file.

You can control the output format using the controls on the left. By default both video and audio stream formats are set to "copy" which means the streams are copied to the output file without modification. Of course this is not what you want, so you have to choose some other format instead of "copy". x264 will give you the smallest video file sizes, i.e. minimal loss of quality. AAC is the smallest for audio. You can also adjust the bitrates, use multi-pass encoding for optimized quality etc. If the video has black borders, you might also want to crop the picture to remove them. You can also scale the video down to a smaller size before encoding to the final format. There are lots of options to play with.

One thing I am not sure of is the "Format" combo box. You can select the video and audio settings from the other drop down menus, so what on earth is this Format menu doing there? Do you know what it is for?

---

### Post by eye208 on 2007-11-13
It's the container format that the video and audio streams get encapsulated in. AVI is a well-known container format, but there are others such as MOV (Quicktime), OGM, MKV, MP4 ...

Not every container format works with every stream format, but AVI will work for almost anything.

---

### Post by erginemr on 2007-11-13
> **eye208 said:**
> It's the container format that the video and audio streams get encapsulated in. AVI is a well-known container format, but there are others such as MOV (Quicktime), OGM, MKV, MP4 ...

Not every container format works with every stream format, but AVI will work for almost anything.

OK. Now I see. Like AVI uncompressed, AVI encoded in DIVX, AVI encoded in XVID, et al. 

Thank you.

---

### Post by the-neural-observer on 2007-11-17
> **geovino said:**
> I have a 43MB AVI video and I would like to convert it to another video format that makes it a smaller size. What program can do this and what file type should I convert it to?


Recompile ffmpeg for xvid and h264 support.
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

then use this app to do your conversions

[http://www.kde-apps.org/content/show.php/Avi+2+iPod+%2B+PSP+%28mp4%29?content=56915](http://www.kde-apps.org/content/show.php/Avi+2+iPod+%2B+PSP+%28mp4%29?content=56915)

its a KDE app but works fine for ubuntu. kommander is required. (sudo apt-get install kommander)

---

### Post by ubuntu-freak on 2007-11-18
Try WinFF [http://biggmatt.com/winff/](http://biggmatt.com/winff/)

---

