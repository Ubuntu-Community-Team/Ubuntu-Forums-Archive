---
title: "No picture but sound VLC"
date: 2011-05-27
forum: Multimedia Software
---

### Post by NewReformist on 2011-05-27
So some videos works correctly played in VLC (1.1.9), but some doesn't.

For instance I tried to play a VMW file (the video codec for that video in particular is : Windows Media Video VC1 (WVC1) )...

The file plays with sound, but the picture is just black so no video picture. 

Now I have the regular codec package installed and in most cases everything works fine, but for instance this video doesn't and there have been similar cases in the past aswell.

---

### Post by papibe on 2011-05-27
Hard to say. May be the file was coded incorrectly, is corrupted, or has DRM.

It would be interesting to know if other players can read reproduce it. Try  Totem Movie Player (installed) or mplayer/smplayer.

Regards.

---

### Post by dFlyer on 2011-05-27
Try searching and installing w32codecs_20110131-0.1medibuntu3_i386.deb. This fixed some of my problems with vmw files.

---

### Post by andrew.46 on 2011-05-27
A recent copy of MPlayer should be able to play your file:

```

andrew@skamandros~$ [COLOR="Red"]**mplayer -vc help | grep -i VC1 **[/COLOR]
ffwmvp      ffmpeg    problems  FFmpeg WVC1  [wmv3]
ffvc1       ffmpeg    problems  FFmpeg WVC1  [vc1]
ffvc1vdpau  ffmpeg    problems  FFmpeg WVC1 (VDPAU)  [vc1_vdpau]
ffvc1crystalhd ffmpeg    problems  FFmpeg WVC1 (CrystalHD)  [vc1_crystalhd]
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [wvc1dmod.dll]

```

with either a windows codec (wvc1dmod.dll) or from libavcodec. Can you post the problem file somewhere?

**Edit: **I note also that a copy of vlc compiled against a recent avcodec plays [these files]("http://samples.mplayerhq.hu/V-codecs/WVC1/Test_1440x576_WVC1_6Mbps.wmv") as well, I attach a screenshot...

---

