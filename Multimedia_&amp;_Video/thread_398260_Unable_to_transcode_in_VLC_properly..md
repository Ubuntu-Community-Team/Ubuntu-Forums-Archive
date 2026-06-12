---
title: "Unable to transcode in VLC properly."
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by Prestwick on 2007-03-31
Hello there,

Using Ubuntu 6.10 server with ffmpeg (fixed using [po-rums method]("http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu-edgy/") of fixing ffmpeg) and vlc 0.8.6.

I am trying to transcode a DIVX video file to mpeg4 for video and MP3 or Mpeg4 audio for audio and then stream it via HTTP.

However for some reason, ffmpeg comes up with the error "cannot find encoder" when it tries to find either the mpeg4 codec or the lame codec.

The full log is -> [here]("http://www.wilde-world.co.uk/vlc-log.txt"), scroll down to the bottom for the video encoding error.

Now, I have 'fixed' ffmpeg to include every codec under the sun that didn't appear under the release of ffmpeg that comes with ubuntu. So therefore, why can't VLC see the encoder enclosed within ffmpeg? How can I get it working properly?

Thanks in advance!

---

### Post by LCC on 2007-03-31
I have a similar problem but I am trying to record a stream, the video is alright but no sound at all!

My post without an answer
[http://ubuntuforums.org/showthread.php?p=2377081#post2377081](http://ubuntuforums.org/showthread.php?p=2377081#post2377081)

---

### Post by Prestwick on 2007-03-31
Yeah, I can stream in H.264 but with no sound because ffmpeg can't find the mp4 audio or MP3 Lame plugins.

If we can get an answer or at least an explanation on whats going on that would be great.

---

### Post by Prestwick on 2007-04-01
***BUMP***

I think it is because ffmpeg cannot find any of the codecs that are meant to be attached to it. 

The reason why the standard Ubuntu ffmpeg can't find them is because it is not installed with things like xvid, lame, etc and the reason why the special "fixed" ffmpeg can't find them is....well...I don't know why because the fixed verion of ffmpeg is compiled with everything before being installed using "checkinstall" so thats bizare. 

Sorry guys, but I **really** do need an answer. Can anyone tell me how to get this fixed?

---

### Post by LCC on 2007-04-01
I`m eager for an answer too mate, but so so far we have had no luck, perhaps it should be reported as a bug?!?

---

### Post by asbani on 2007-11-03
I want an answer too. I'm recordgin stuff online via VLC Transcode. but only video will work, no sound...

---

### Post by sjforrester on 2007-12-28
bump

---

### Post by P5ych0Gigabyte on 2007-12-30
I',m having a similar problem. I try to encode to mp4 but get no sound. [http://ubuntuforums.org/showthread.php?t=652277](http://ubuntuforums.org/showthread.php?t=652277)

Anyone have any ideas?

---

### Post by deboest on 2008-01-28
Prestwick:

I'm surprised this has been unanswered this long. Hopefully you already got it working, but in case you haven't, I'll suggest something to try that worked for me.

One of the error message you are getting is misleading. Glancing through the log, it is easy to focus on the last error you see:

stream_out_transcode error: cannot find encoder ((null))
ffmpeg debug: ffmpeg codec (MPEG-4 Video) stopped

However, the important error actually occurs a few lines earlier:

ffmpeg warning: timebase not supported by mpeg 4 standard
 (mpeg4@0x81ba4b0)

I think your source video has a timebase that is not compatible with mpeg4, so ffmpeg is refusing to do the transcoding with the arguments you have given it. I couldn't find where you had posted the command you used, but try adding 
fps=25
to the "transcode" section on the command line. 

I've received similar errors with various codecs when using incompatible bitrate and such, too. Although probably not the problem in this particular case, it is something to keep in mind in case you come across similar errors in the future.

Hope that helps.

---

### Post by wounsel on 2008-04-07
This is how I fixed it:
Go to Open Capture Device> Advanced Options
Now look at the option for audio channel. Mine was default (-1), once I bumped that up to '0' then sound started working after transcoding for me!
Hope that helps :)

---

