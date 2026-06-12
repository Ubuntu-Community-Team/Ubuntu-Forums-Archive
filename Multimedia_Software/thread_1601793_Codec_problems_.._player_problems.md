---
title: "Codec problems .. player problems"
date: 2010-10-20
forum: Multimedia Software
---

### Post by jfbooth on 2010-10-20
Linux noob.  Running Xubuntu 10.04 Lucid Lynx.

Have a 'movie viewer' named Totem Movie Player 2.30.2.  Inserted an old CD containing .avi video clips.  Tried playing one with the viewer.  Get:

[B]The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.[/B]

and I commence the search.  It is looking for Intel Indeo 5 Decoder.  The search FAILS to find the needed 'software'.

I installed VLC VIDEO LAN player .. 1.0.6 GOLDENEYE.  Attempted to play the same .avi clip and got:

[B]No suitable decoder module:
VLC does not support the audio or video format "IV50". Unfortunately there is no way for you to fix this.[/B]

Pretty much at a loss for what to do next.  Any help greatly appreciated.

---

### Post by cchhrriiss121212 on 2010-10-20
Open software center, and install xubuntu-restricted-extras, it will pull in all the codecs you need. Apart from DVD playback, which requires libdvdcss2 from medibuntu. See here for that:
[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs")

---

### Post by lukeiamyourfather on 2010-10-20
That sounds like the Indeo video codec. An open source implementation doesn't exist as far as I know, only the proprietary encoders and decoders were used. It has been defunct for over a decade. If you have access to a Windows or Apple machine there might still be support in Windows Media or Quicktime. Or they might have removed the codecs from the software since it has been so long ago, but worth a try anyway.

---

### Post by jfbooth on 2010-10-20
> **cchhrriiss121212 said:**
> Open software center, and install xubuntu-restricted-extras, it will pull in all the codecs you need. Apart from DVD playback, which requires libdvdcss2 from medibuntu. See here for that:
[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs")

thank you immensely.  Will try that as soon as the upgrade to Xubuntu 10.10 finishes. I 'ran across' that as I was looking for a codec solution.  I do not have a DVD drive on the computer . only CD .. so thank you for your advice.  Will close this as solved as soon as I 'get her done' and everything works.

---

### Post by mc4man on 2010-10-20
If you're going to 10.10 you should be ok as far as Indeo 5, most players should be able to play thru ffmpeg or in the case of gstreamer (totem) the gstreamer-ffmpeg plugin

> $ gst-inspect plugin ffmpeg |grep indeo
  ffdec_indeo2: FFmpeg Intel Indeo 2 decoder
  ffdec_indeo3: FFmpeg Intel Indeo 3 decoder
  ffdec_indeo5: FFmpeg Intel Indeo Video Interactive 5 decoder


Note that in 10.10 u-r-e (x-r-e) has been split - x-r-addons is probably what you want
or for most decoding support simply
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

---

### Post by wojox on 2010-10-20
Did you install

```
sudo apt-get update; sudo apt-get install xubuntu-restricted-extras
```

Also look here after [PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by andrew.46 on 2010-10-20
Hi jfbooth,

Looks like your query has mostly been answered :). Nevertheless I had a quick look at the following indeo 5 clip:

```
wget 'http://samples.mplayerhq.hu/V-codecs/IV50/JessicaAlba_(Intel_Indeo5).avi'
```

and if you view this with the native (libavcodec) codec:

```

andrew@skamandros~/Desktop$**[COLOR="Red"] mplayer -vc ffindeo5 JessicaAlba_\(Intel_Indeo5\).avi [/COLOR]**
MPlayer SVN-r32518-4.3.3 (C) 2000-2010 MPlayer Team

Playing JessicaAlba_(Intel_Indeo5).avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [IV50]  384x288  24bpp  15.000 fps  919.8 kbps (112.3 kbyte/s)
Clip info:
 Software: C:\PROGRAMMI\BOEDER\TVBOEDER.EXE -AVICAP32- MSVIDEO: Brooktree PCI Video Capture Driver, Version:  4.1.8.8
 Digitization Time: Fri May  5 18:15:33 2000
==========================================================================
Forced video codec: ffindeo5
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
**[COLOR="Red"]Selected video codec: [ffindeo5] vfm: ffmpeg (FFmpeg Indeo 5)[/COLOR]**
==========================================================================
Audio: no sound
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x8b05960]using unscaled yuv410p -> yuv420p special converter
VO: [xv] 384x288 => 384x288 Planar YV12 
V:  45.2 679/679  7%  0%  0.0% 0 0

```

you will notice that this is a great example of how the native decoder gives much better playback than the external, windows codec:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -vc indeo5ds JessicaAlba_\(Intel_Indeo5\).avi [/COLOR]**
MPlayer SVN-r32518-4.3.3 (C) 2000-2010 MPlayer Team

Playing JessicaAlba_(Intel_Indeo5).avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [IV50]  384x288  24bpp  15.000 fps  919.8 kbps (112.3 kbyte/s)
Clip info:
 Software: C:\PROGRAMMI\BOEDER\TVBOEDER.EXE -AVICAP32- MSVIDEO: Brooktree PCI Video Capture Driver, Version:  4.1.8.8
 Digitization Time: Fri May  5 18:15:33 2000
==========================================================================
Forced video codec: indeo5ds
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 IYUV UYVY YV12 I420 
Decoder is capable of YUV output (flags 0x2f)
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 384x288 => 384x288 Planar YV12 
**[COLOR="Red"]Selected video codec: [indeo5ds] vfm: dshow (Intel Indeo 5)[/COLOR]**
==========================================================================
Audio: no sound
Starting playback...
V:  45.2 679/679  3%  0%  0.0% 0 0 


Exiting... (End of file)
andrew@skamandros~/Desktop$ 

```

You will have access to indeo5ds under a 32bit installation of MPlayer if you have installed the MPlayer codecs, usually under Ubuntu by installing the w32codecs held in the MEdibuntu respository. My own copy of vlc choked on this file which I will investigate a little more closely after I have mowed the lawn :). Edit: vlc screenshot attached...

Andrew

---

### Post by jfbooth on 2010-10-22
Thank you ALL for the great replies.  The solution resolved itself when I installed Xubuntu 10.10.

I really appreciate your time and good advice.

---

