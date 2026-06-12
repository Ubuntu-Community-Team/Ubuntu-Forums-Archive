---
title: "Re-encoding .avi files with h264"
date: 2009-07-18
forum: Multimedia Software
---

### Post by aerojad on 2009-07-18
Greetings.

I have a stack of .avi files that I have encoded over time and I was attempting to play them on my PS3.  I got an error that the data was not supported and after some digging around I found that PS3 loves .mpeg files with the h.264 codec.  I did not have that codec until a few moments ago when I apt-get'd the *x264* package.

My question is, how would I re-encode a directory full of .avi files with mencoder to .mpeg files and force mencoder to use the x264 codec instead of whatever else it uses by default?

Thanks for your help.

---

### Post by aerojad on 2009-07-18
So I toyed around some more and tried this at the command line:

mencoder input.avi -of mpeg -ovc lavc -oac copy -o output.mpeg

This worked, but the file size was 13% smaller than the original.  Is there any way I can transcode with no loss?

---

### Post by andrew.46 on 2009-07-19
Hi aerojad,

Unless you really have your heart set on MEncoder you would be better to use FFmpeg IMHO. Have a look at:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Andrew

---

### Post by vinutux on 2009-07-19
perhaps....avidemux fix your problem..there is GUI settings for output format (container) , audio and video encoders ..etc

```
sudo apt-get install avidemux
```

---

