---
title: "Convert .mp4 to .mov for Cinelerra?"
date: 2012-12-07
forum: Multimedia Software
---

### Post by LinuxNubian on 2012-12-07
Hello, I'm trying to use cinelerra and it seems to require one to convert all video files to .mov before allowing one to edit the video. I have been looking for hours for a way to convert mp4 to mov, but there is no forthcoming solution for Linux. Is there a way to convert .mp4 files to .mov with Linux or should I just switch back to Windows or get a Mac until Linux is more mature? I like the idea of an open source operating system; but, seriously, I am spending way too much time researching how to do things with Linux that are very simple with Windows and Mac. :/
Any ideas?
Thx

---

### Post by SeijiSensei on 2012-12-07
I know for sure that Cinelerra accepts other formats besides .mov because I have used Cinelerra, and I have never used the .mov container.  Apple likes QuickTime because it's their baby.  Most of the rest of us prefer either Matroska (.mkv) or the MP4 container.

That said, take a look at [WinFF]("http://winff.org/html_new/"), a GUI front-end to ffmpeg.

---

### Post by dannyboy79 on 2012-12-07
it sounds like you don't have the correct codec's installed. cinerella should be able to edit pretty much any filetype IF you have the correct codec's installed. I know I use kdenlive and can edit .mov because I have the libavformat-extras-52 or whatever it's called. you may try to enable the medibuntu repos to get these extra ffmpeg libraries.

---

### Post by SeijiSensei on 2012-12-07
If it's a problem with restricted codecs, then all you need to run is:

```
sudo apt-get install ubuntu-restricted-extras
```

If you're using a variant like kubuntu or lubuntu replace "ubuntu" with the name of your variant.

---

### Post by evilsoup on 2012-12-07
An MP4 file almost certainly contains h.264 video and AAC audio, both of which are compatible with the Quicktime MOV container, and should be readable by cinelerra. You can do this with avconv, from the command-line (this will be completely lossless):
```
avconv -i input.mp4 -c copy output.mov
```

This will take approximately as long as copying the file from one directory to another.

HOWEVER, h.264 is highly compressed; this makes it an excellent delivery format, but for editing it will put a lot of strain on your computer. If you're just making quick youtube videos, you might be OK, but standard practice on every platform for serious video editing is to convert your video to an intermediate, relatively decompressed format. Apple's Final Cut Pro straight-up won't allow you to use h.264 video, or even compressed audio, for example.

If you follow my advice, you should convert the audio to WAV, and the video to huffyuv (a lossless video codec). DISCLAIMER: I haven't used cinelerra for years, so I can't remember if it supports these codecs; check yourself with a small piece of video*. Again, from the command-line:
```
avconv -i input.mp4 -c:a pcm_s16le -c:v huffyuv output.avi
```

This will create fuckoff huge files (on my system, a 25 MB MP4 file ended up at 1.4 GB using this), but should give you a smoother (and less crash-prone) editing experience. This will take a bit longer than copying the audio streams to another container, but it will be fairly quick (on an atom netbook, it encoded at 159 frames per second).

Extra bonus: to convert every MP4 in a directory to an avi using these options:
```
for f in *mp4; do avconv -i "$f" -c:a pcm_s16le -c:v huffyuv "${f/%mp4/avi}"; done
```

----
*: to encode a thirty-second clip, use "-t 30" before "output.avi"

---

### Post by LinuxNubian on 2012-12-08
Thx all for straightening things out for me and for the pointers (I look forward to experimenting). Not only does Cinelerra handle mp4 but changing from mp4 to mov is simple. I think my codecs were the problem as, after I reinstalled Cinelerra (after I installed Lubuntu in place of Ubuntu for other causes), all is well. For the record, I found an ffmpeg command that converted .mp4 to .mov :

$ ffmpeg -i /home/user/videos/videoname.mp4 -acodec copy -vcodec copy -f mov /home/user/videos/videoname.mov

Thx, again, now I just need to figure out how to transfer files from Android 4.0.x ICS to (L)Ubuntu and I will be one happy Linux user ):P

---

### Post by evilsoup on 2012-12-08
Glad to help, if your problem is solved, please mark the thread as 'solved' with the 'thread tools' button at the top of your first post. I would suggest opening a different thread for help with transferring files from your Android.

---

