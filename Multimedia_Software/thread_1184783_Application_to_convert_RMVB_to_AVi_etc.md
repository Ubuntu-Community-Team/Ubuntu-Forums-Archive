---
title: "Application to convert RMVB to AVi etc?"
date: 2009-06-11
forum: Multimedia Software
---

### Post by joey-elijah on 2009-06-11
I have realplayer installed which plays RMVB's, but i'd prefer to convert them to AVI for burning purposes etc.

Handbrake doesn't convert RMVB and nor does DeVeDe (my dvd 'creator' applicaion).

What's the best way to convert RMVB in Ubuntu?

Thanks :)

---

### Post by andrew.46 on 2009-06-11
Hi joey-elijah,

> **joey-elijah said:**
> What's the best way to convert RMVB in Ubuntu

MPlayer will play RMVB files and thus MEncoder will transcode these files to avi:

```

andrew@skamandros~/samples$ **[COLOR="Purple"]mplayer -vc ffrv40 -ac ffcook samplerv.rmvb[/COLOR]**
MPlayer SVN-r29352-4.2.4 (C) 2000-2009 MPlayer Team

Playing samplerv.rmvb.
REAL file format detected.
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 0
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  720x576  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 copyright: (C) 2005
==========================================================================
Forced video codec: ffrv40
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffrv40] vfm: ffmpeg (FFmpeg RV40)
==========================================================================
==========================================================================
Forced audio codec: ffcook
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 6 ch, s16le, 131.3 kbit/3.10% (ratio: 16408->529200)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio)
==========================================================================
AO: [oss] 44100Hz 6ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x576 => 720x576 Planar YV12 
A:  79.2 V:  79.2 A-V:  0.007 ct: -0.632 1967/1967 34%  1%  1.9% 1 0 

Exiting... (End of file)

```

Mind you this jogged my memory a little and I have found an older post on exactly this issue and even the same file:

[http://ubuntuforums.org/showpost.php?p=6999270&postcount=3](http://ubuntuforums.org/showpost.php?p=6999270&postcount=3)

I had no feedback on this syntax but it certainly worked well enough on my own system.

Andrew

---

### Post by joey-elijah on 2009-06-12
Thanks for the reply, that seems ideal... however when i run the command on an .rmvb file, the video is not detected but the audio is.

Any ideas why that might be/what i'm doing wrong? 

Thanks :)

---

### Post by andrew.46 on 2009-06-12
Hi joey-elijah,

> **joey-elijah said:**
> however when i run the command on an .rmvb file, the video is not detected but the audio is.

Hmmmm.... try the following download:

```
sudo apt-get install libstdc++5
```

and this may allow you to transcode successfully. If not can you perhaps try playing the file I have here? It can be found here:

```
wget http://samples.mplayerhq.hu/real/AC-cook/cook_5.1/samplerv.rmvb
```

and if you run it from the commandline:

```
mplayer -v samplerv.rmvb
```

and post the full commandline output here there should be some hints there. 

All the best,

Andrew

---

