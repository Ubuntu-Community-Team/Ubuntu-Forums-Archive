---
title: "Ffmpeg to convert HD .mkv to .avi"
date: 2010-01-13
forum: Multimedia Software
---

### Post by jjmatt on 2010-01-13
So I've got a bunch of HD files in .mkv format that I want to convert to a format that the 360 will read (currently just trying .avi files) so I can stream the media to my xbox360. I'd rather avoid transcoding the entire file, so I tried unpacking the .mkv file into audio and video (and subtitle if necessary) and repacking said file into avi using ffmpeg. The repacking is where I am having the problem. Here's the commands I tried at first (it might look familiar):

```
mkvextract tracks file.mkv 1:temp_video.avi 2:temp_audio.ogg 3:temp_sub.srt
ffmpeg -i temp_video.avi -i temp_audio.ogg -vcodec copy file.avi
```

However, I keep getting this annoying error:

```
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
```

Where stream #0.1 is the output audio stream to the .avi file. I think I have narrowed it down to the fact that the input streams are all 6 channel (5.1 surround sound) which mp2 doesn't support (the ffmpeg audio default) so I did this instead:

```
ffmpeg -i temp_video.avi -i temp_audio.ogg -vcodec copy -acodec libmp3lame file.avi
```

I'm still getting the same error, but when I use

```
ffmpeg -i temp_video.avi -i temp_audio.ogg -vcodec copy -acodec libmp3lame -ac 2 file.avi
```

to change the sound to stereo it works. Problem is I'd like to keep my media in surround sound. Any thoughts on how to get all 6 channels in the new mp3 file? I'm fairly certain that mp3s support 5.1. And after some messing around, I haven't found that my ffmpeg can transcode audio format from 5.1 back to 5.1. 

So since (I think) the 360 can play .ac3 files I decided to just copy both the video and audio file to the .avi file sans transcoding using ```
ffmpeg -i temp_video.avi -i temp_audio.ogg -vcodec copy -acodec copy file.avi
``` however now about halfway through, I run into this error:

```
NULL @ 0x22f3a00]error, non monotone timestamps 62562 >= 62562
av_interleaved_write_frame(): Error while opening file
```

I can't seem to find any solution to this problem anywhere online, does anyone know how to get around this? I'd prefer to use ffmpeg for this if possible. (so I can write a script and just attack an entire directory at once)

For what it's worth, I'm using the latest ffmpeg in the ubuntu (karmic) default repositories.

---

### Post by FakeOutdoorsman on 2010-01-14
Development of FFmpeg is quite active and as of now there have been 1,857 updates since Karmic's FFmpeg revision.  Using a recent FFmpeg will allow you to rule out any bugs that may have already been fixed:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

It's worth a try, although you may still get the error.  Could you show the details of your original MKV?

```
ffmpeg -i file.mkv
```

---

