---
title: "filesize limitations of using mencoder to convert mkv to avi on PS3?"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by johnzbesko on 2008-03-25
After much searching, I discovered several ways to convert mkv files to avi for playing on a PS3. Unfortunately, the conversion only seems to work if the mkv file is less than 2 GB. (I think.) All my conversions seem to be 2-2.2 GB even though the source is over 4GB. The source files originally came from a Blu-ray disc. I'm running x86 32bit Kubuntu 7.10.

What is odd, is that xine plays the entire converted movie, but when I stream it (using MediaTomb) to the PS3, the movie stops about halfway thru. Transferring the file to the PS3 hard drive does not help, so I don't think the problem is MediaTomb.

The conversion scripts/commands all seem based on mencoder. I also tried used PS3 Video 9 from Red Kawa in a virtual XP environment, which produced a 3GB mp4 file, but even xine couldn't play it.

What is wrong? Smaller mkv files have converted fine. Do I have to compile mencoder from source with some special setting? Do I need to move to 64bit Kubuntu? Any help is greatly appreciated.

---

### Post by warp99 on 2008-03-25
How about using ffmpeg instead? 

```
ffmpeg -formats | grep matroska

D  matroska        Matroska file format

```

I don't believe there is a limitation with ffmpeg since mkv is just a container for storing or streaming video and audio files. If you want to use ffmpeg and output to a mp4 it would look like this:

```
ffmpeg -i foo.mkv -sameq -vcodec mpeg4 -acodec aac -ab 128  foo.mp4
```

This will give you an mp4 file at the same video quality with an aac encoding at a bitrate of 128. If you want to ouput to an avi file your command string would look like this:

```
ffmpeg -i foo.mkv -sameq -vcodec mpeg4 -acodec mp3 -ab 128  foo.avi
```

This will give you an avi with the same video quality with an mp3 encoding at a bitrate of 128. I would first check the audio bitrate for your .mkv file first:

```
ffmpeg -i foo.mkv
```

Then match the audio bitrate to your output files. Type 'man ffmpeg' for more information on additional settings. :)

---

### Post by johnzbesko on 2008-03-26
Thank you for your suggestion. I had tried ffmpeg before trying other methods, but I tried your command and produced a new mp4 file. Unfortunately, the sound and video become increasingly out of sync, I believe as a result of errors I see when converting. Here is the tail end of the conversion:

Error while decoding stream #0.0
[h264 @ 0xb7ecba68]AVC: nal size 2027578224
[h264 @ 0xb7ecba68]no frame!
Error while decoding stream #0.0
[h264 @ 0xb7ecba68]AVC: nal size 20275782242.6 bitrate=2789.2kbits/s
[h264 @ 0xb7ecba68]no frame!
Error while decoding stream #0.0
[h264 @ 0xb7ecba68]AVC: nal size 2027578224
[h264 @ 0xb7ecba68]no frame!
Error while decoding stream #0.0
frame=239633 q=0.0 Lsize= 3564912kB time=6632.7 bitrate=4403.0kbits/s
video:3002350kB audio:155946kB global headers:0kB muxing overhead 12.874556%

Other methods that first split the audio from the video and then recombined them also had problems- that's when I started with the mencoder scripts. Your post suggests checking the audio bit rate with:

ffmpeg -i foo.mkv

but the output from this command simply says:

[matroska @ 0xb7f6e610]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7f6e610]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb7f6e610]Unknown track header entry 0x6d80 - ignoring
Input #0, matroska, from 'foo.mkv':
  Duration: 01:50:32.9, bitrate: N/A
  Stream #0.0: Video: h264, yuv420p, 1280x528, 23.98 fps(r)
  Stream #0.1: Audio: ac3, 48000 Hz, 5:1
  Stream #0.2: Audio: ac3, 48000 Hz, 5:1
Must supply at least one output file

So again, I'm stuck. :-/  Any other ideas?

---

### Post by warp99 on 2008-03-26
Try to just past the video and audio as a copy with the following string:

```
ffmpeg -i foo.mkv -vcodec copy -acodec copy foo.mp4
```

or just encode the audio

```
ffmpeg -i foo.mkv -vcodec copy -acodec aac -ar 48000 foo.mp4
```

This will do basically the same thing, extract the mkv file from it's container. You can also try this with mencoder:

```
mencoder foo.mkv -ovc copy -oac copy -o foo.mp4
```

Since there is no encoding it may just work on the larger files that you have. You can always convert the video into an .avi after the extraction. Good luck. :)

---

### Post by johnzbesko on 2008-03-28
Again, thank you for your suggestions. Alas, none of the commands produced a file I could play on the PS3. Using ffmpeg produced the most errors in the conversion process.(Something about frame errors.) Mencoder did not even convert the whole file before crapping out (except when I -ovc  and -oac copied to foo.avi, which worked but didn't play on the PS3.) 

I tried using Kino to convert the file. It produced an intermediate DV file that was 5X larger than the original. Kino then exported that into an mpeg2 file that was half the size of the original. It didn't play on the PS3. I noticed that Kino uses mencoder underneath the GUI.

I would post the conversion errors, but my internet connection at home died and I have to write this reply from work.

I'm still puzzled that several different methods worked with smaller files, but not a whole HD movie file. Does choice of file system (ext3, XFS, ReiserFS) make a difference?

---

### Post by warp99 on 2008-03-28
Well at least you got the file out of the mkv container by using the mencoder copy parameters so the file can now be converted into something that the PS3 can read. Here is a post that may help you read the files on the PS3:

[http://ubuntuforums.org/showthread.php?t=600022](http://ubuntuforums.org/showthread.php?t=600022)

Edit: Read the last post in the thread.

---

### Post by blazerte on 2008-04-10
I think the filesize limitations you are having relate to the PS3 and avi/divx files, not to the transcoders or ubuntu. The recent V2.2 PS3 upgrade was supposed to eliminate a 2GB limitation on avi/divx files, but it didn't for me and for many others on the web, so going to an mp4 container with h.264 video and aac audio may be the best solution.

---

