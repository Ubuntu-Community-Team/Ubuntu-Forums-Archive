---
title: "MP4Box importing h264 video with wrong dimensions (16x96 instead of 1280x720!)"
date: 2011-12-16
forum: Multimedia Software
---

### Post by beccatoria on 2011-12-16
Hi!  

So, I've used mkvextract and MP4Box in conjunction before to change the container of an .mkv to .mp4 without having to re-encode it.  It always worked fine.  

However, trying it with an .mkv file I generated myself via ffmpeg (converted from an .avi), yields seriously weird results.  

Basically, when MP4Box imports the h264 video, it imports it with dimensions of 16x96, when the video should be 1280x720.  Sure enough, the finished result is a tiny rectangle in the middle of the screen.  I have absolutely no idea why this is happening and was hoping someone could shed some light on it.  Here's a breakdown of the commands I used and the results:  

1) For background, I'm using Ubuntu 10.04 64 bit.  

2) mkvinfo shows that the video track should, indeed, be 1280x720:  

```
becka@flipper:~$ mkvinfo test.mkv
+ EBML head
|+ EBML version: 1
|+ EBML read version: 1
|+ EBML maximum ID length: 4
|+ (Unknown element: EBMLMaxSizeLength; ID: 0x42f3 size: 4)
|+ Doc type: matroska
|+ Doc type version: 2
|+ Doc type read version: 2
+ Segment, size 542043104
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 147)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: Lavf53.26.0
| + Writing application: Lavf53.26.0
| + Segment UID: 0x9e 0xa6 0x3e 0xd0 0x19 0x25 0xb3 0x46 0xb1 0x95 0xc7 0x85 0x23 0xe7 0xde 0x49
| + Duration: 264.932s (00:04:24.932)
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 1
|  + Lacing flag: 0
|  + Language: und
|  + Codec ID: V_MPEG4/ISO/AVC
|  + Track type: video
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 720
|   + Display width: 1280
|   + Display height: 720
|   + Display unit: 3
|  + CodecPrivate, length 39
| + A track
|  + Track number: 2
|  + Track UID: 2
|  + Lacing flag: 0
|  + Language: und
|  + Codec ID: A_MPEG/L3
|  + Track type: audio
|  + Audio track
|   + Channels: 2
|   + Sampling frequency: 48000
|+ Tags
| + Tag
|  + Targets
|  + Simple
|   + Name: ENCODER
|   + String: Lavf53.26.0
|+ Cluster

```

2) So next up, I split the file with mkvextract like so:  

```
becka@flipper:~$ mkvextract tracks test.mkv 1:test_video.h264 2:test_audio.aac
Extracting track 1 with the CodecID 'V_MPEG4/ISO/AVC' to the file 'test_video.h264'. Container format: AVC/h.264 elementary stream
Extracting track 2 with the CodecID 'A_MPEG/L3' to the file 'test_audio.aac'. Container format: MPEG-1 Audio Layer 2/3
Progress: 100%

```

That seems to go without a hitch.  When I open the .h264 file in VLC, it plays at normal size.  So I don't think the problem is occurring at this stage.  

So next I, 

3) mux 'em back together with MP4Box and the following happens:  

```
becka@flipper:~$ MP4Box -fps 23.976 -add test_video.h264 -add test_audio.aac test.mp4
AVC-H264 import - frame size 16 x 96 at 23.976 FPS
Import results: 6352 samples - Slices: 26 I 6326 P 0 B - 1 SEI - 26 IDR
AAC import - sample rate 16000 - MPEG-2 audio - 1 channel
Saving to test.mp4: 0.500 secs Interleaving
```

As you can see, it imports the video at 16x96, which is just totally bizarre and sure enough, playing it back, that's what displays.  

I was just wondering if anyone had any suggestions as to why this could be happening, or what I can do to fix it?  

I'm not enormously used to working with the command line, and MP4Box's syntax has me a little confused (I've found references to a layout command where widthxheight can be specified, but have been unable to get it recognised when I try to use it), so if there's something I'm missing out, I'd appreciate knowing where to put it in the command as well as what it is.  

Just let me know if there's any extra information you need.  

Thank you all!  :)

---

### Post by andrew.46 on 2011-12-17
Sounds a little odd, are you using the latest mkvextract? Latest is:

```

andrew@skamandros~$ **[COLOR="Red"]mkvextract --version[/COLOR]**
mkvextract v5.1.0 ('And so it goes') built on Dec 12 2011 18:29:01

```

If not mosu has packages here:

[http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu)

Maybe this will correct this odd problem :).

---

### Post by FakeOutdoorsman on 2011-12-17
I'm not sure of the cause, but you could try FFmpeg to mux into mp4. Using FFmpeg from repository:
```
ffmpeg -i input.mkv -vcodec copy -acodec copy output.mp4
```
Or if using recent FFmpeg that you compiled:
```
ffmpeg -i input.mkv -c copy output.mp4
```

---

### Post by beccatoria on 2011-12-17
Thanks for the suggestion to update mkvextract.  Unfortunately, that didn't help.  However!  I did manage to get the job done using ffmpeg.  Thanks guys!

---

### Post by andrew.46 on 2011-12-18
Good to hear that the problem is resolved but I confess that I am still a little curious as to what was going wrong. Is there any chance you can post the original file somewhere so I can see if I can duplicate the error? Or even better suggest a resolution using mkvextract and MP4Box.....

---

