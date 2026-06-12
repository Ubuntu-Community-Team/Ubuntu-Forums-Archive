---
title: "mov to avi conversion"
date: 2012-03-21
forum: Multimedia Software
---

### Post by stevebu56 on 2012-03-21
Can someone tell me what's going on when I run these two commands.  I am pulling a video off of my iPhone and then converting it to avi.  The video is rotated so I rotate it with the second command.  

My question is why is the file size shrinking after the rotation?  I read through the documentation for the commands but nothing is jumping out at me.  I'm guessing it has something to do with the codecs used with these commands.  Any help or explanation would be helpful.  Thanks.

```

ffmpeg -i chase_eating_noodles.mov -sameq -vcodec mpeg4 -acodec libmp3lame chase_eating_noodles.avi

mencoder -of avi -oac mp3lame -ovc lavc -vf rotate=1 -o chase_eating_noodles.avi cen.avi 

```

---

### Post by ron999 on 2012-03-21
> **stevebu56 said:**
> 
My question is why is the file size shrinking after the rotation?
Hi
It's probably because MEncoder is using a lower bitrate than the original iPhone video.

Can you show details about that original iPhone video.
Paste the result from a command like this:-
```
ffprobe chase_eating_noodles.mov
```

---

### Post by pixiq on 2012-03-21
If you use ffmpeg also to rotate, you should have no problems with quality caused by mencoder.

[[COLOR="Green"]_http://phayz.wordpress.com/2011/10/28/howto-rotate-a-video-using-ffmpeg/_[/COLOR]]("http://phayz.wordpress.com/2011/10/28/howto-rotate-a-video-using-ffmpeg/")

Add this option to the command (before the output file)
```
 -vf "transpose=1"
``` or "transpose=2" if you want to rotate the other way.

*Nota bene*: This only works with rather new versions of ffmpeg compiled with *filters*, for example version 0.8-4:0.8-1ubuntu2, that is obtained via ```
sudo apt-get install ffmpeg
``` in Precise beta (Ubuntu 12.04). Actually, it is recommended to use *avconv* instead, which has the same syntax, so I guess it is built from the same source code, and further developed.

---

### Post by stevebu56 on 2012-03-21
@ron999 Here's the info from ffprobe for the mov file and the avi file respectively. 

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'cen.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2012-03-21 20:27:18
    encoder         : 5.1
    encoder-eng     : 5.1
    date            : 2012-03-17T09:36:08-0500
    date-eng        : 2012-03-17T09:36:08-0500
  Duration: 00:00:49.78, start: 0.039955, bitrate: 769 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, mono, s16, 62 kb/s
    Metadata:
      creation_time   : 2012-03-21 20:27:18
    Stream #0.1(und): Video: h264 (Main), yuv420p, 480x272, 704 kb/s, 30 fps, 30 tbr, 600 tbn, 1200 tbc
    Metadata:
      creation_time   : 2012-03-21 20:27:18

Input #0, avi, from 'cen_rotated.avi':
  Metadata:
    encoder         : MEncoder SVN-r33713-4.6.1
  Duration: 00:00:49.76, start: 0.000000, bitrate: 912 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 272x480 [PAR 1:1 DAR 17:30], 30 tbr, 30 tbn, 30 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, mono, s16, 102 kb/s
```

---

### Post by stevebu56 on 2012-03-21
@pixiq  I was able to add the transpose option and that works fine with one less command to remember when I'm editing.  Thanks.

---

### Post by pixiq on 2012-03-22
> **stevebu56 said:**
> @pixiq  I was able to add the transpose option and that works fine with one less command to remember when I'm editing.  Thanks.
I'm glad it works for you too :-)

When you feel like it, please mark this thread as SOLVED clicking on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page!

---

