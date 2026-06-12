---
title: "Use Can VLC select Audio Stream for Transcoded File?"
date: 2012-02-26
forum: Multimedia Software
---

### Post by gbrowning on 2012-02-26
Have been trying for a few days to force VLC to use an English audio stream when transcoding. I have been using the transcoding wizard and cannot find a setting which does the trick.  I have searched for command line solutions but have not been able to find those either.
   The video file is H264 MPEG4 AVC and the two audio streams are
   Mpeg AAC Japanese
   Mpeg AAC English
Every attempt at transcoding has resulted with only the Japanese audio stream.  Settings for VLC have been changed to "eng" for every instance of reference to language I can find.  Perhaps there are some I have missed.
   Any help will be greatly appreciated.

---

### Post by papibe on 2012-02-26
Another option could be to first extract the tracks, video, audio1, and audio2. Then transcode if needed, and finally to put the ones you need into a container (mkv, mp4, etc).

What is the container of the original video?

Regards.

---

### Post by gbrowning on 2012-02-28
The original is MKV.  I was able to specify the audio track in DeVeDe and the resulting file is of acceptable quality. I want to be able to do this using VLC.  Let me attept your suggestion and perhaps ask for more help.

---

### Post by papibe on 2012-02-28
You can do most the work, if not all, in the command line.

There's a package called mkvtoolnix, that includes a command called mkvextract. You can easily get the video and audio tracks out the container.

Something like this for example:
```
mkvextract tracks Pioneer.One.S01E06.720p.x264-VODO.mkv 1:video.264 2:audio1.ac3 3:audio2.ac3

```
Then depending if you want a new mkv or an mp4, you can use mkvmerge or MP4Box (from the package gpac).

Just some thoughts. Tell us how it goes.
Regards.

---

### Post by gbrowning on 2012-02-29
Thank you Papipe.  I am relatively new to command line linux and am excited yet trepidacious when using the command line packages. My greatest disability is that I do not know how to find these tools for myself. In additions finding the correct syntax for the exact process is often trial and error. Have not yet blown anything up beyond repair so....
Will look at these packages and let you know what happens.  Trying my best to use only VLC but much of the power in that package is in the command line anyway so might as well grab other tools.
   Thanks again!

---

### Post by papibe on 2012-02-29
There are several graphical tools that are specifically designed for transcoding or repacking video, and there are far more easy to use than VLC. From the top of my mind: avidemux and mkvmerge-gui.

If you share what is the final format/codec you are looking for, I would gladly recommend one of them for you.

Regards.

---

### Post by gbrowning on 2012-03-02
Papipe:
   I am not certain which is the most appropriate format and container but in the end consistency is the key.  I have been trying to use MP4, MPEG4/AVC. The results have been mixed and why some play on one DVD machine and do not play on a different bluray is problem which still needs to be resolved.  Really, transcoding is a deep field and my hat is off to those of you who have kept up with all the issues.
   I have begun with GUI based packages and have used CLI to a limited extent. The developers of the GUIs have gone through the trouble of concentrating the most important features and presenting them in a logical and sometimes intuitive manner.  These have been teaching tools for me.  It does seem now, though, that I need to turn this on its head and get to the nuts and bolts level.
   Thank you for your help Papipe.  It will take a while for me to understand how to use the tools you have shown me.

---

