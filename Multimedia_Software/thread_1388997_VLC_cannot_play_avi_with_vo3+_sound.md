---
title: "VLC cannot play avi with vo3+ sound"
date: 2010-01-23
forum: Multimedia Software
---

### Post by P3t3r on 2010-01-23
Hi,

When playing some avi files, I get 
"No suitable decoder module:
VLC does not support the audio or video format "vo3+". Unfortunately there is no way for you to fix this."

Which codec do I need for this and how do I install it best? It used to work on my old Kubuntu but now after I had to reinstall, it doesn't. I completely forgot which codecs I installed though. :(

--Peter

---

### Post by andrew.46 on 2010-01-24
Hi Peter,

> **P3t3r said:**
> VLC does not support the audio or video format "vo3+". Unfortunately there is no way for you to fix this."

Can you provide a sample or link to one of these files?

Andrew

---

### Post by mc4man on 2010-01-24
I think there may be different types of vorbis audio, some that playback in vlc or other players, others that don't

Typically vlc would use libavcodec or libvorbis ( there is also tremor.

So if you have ffmpeg installed you could try this to see if libavcodec can decode

ffplay /path/to/filename



As in aside (i think), here's some [samples]("ftp://streams.videolan.org/issues/vorbis3+/") that neither vlc or mplayer decode (one of them is totally borked

> Playing /home/doug/Desktop/vorbis3plus_sample.avi.

Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)

Opening audio decoder: [acm] Win32/ACM decoders
Loading codec DLL: 'vorbis.acm'
Win32 LoadLibrary failed to load: vorbis.acm, /usr/lib/codecs/vorbis.acm, /usr/lib/win32/vorbis.acm, /usr/local/lib/win32/vorbis.acm
Can't open library vorbis.acm
ACM_Decoder: Unappropriate audio format
Could not load/initialize Win32/ACM audio codec (missing DLL file?).
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x6771.
Read DOCS/HTML/en/codecs.html!
Audio: no sound


What's interesting ( in that another file to add to w32codecs) is by adding a win file [vorbis.acm]("http://www.free-codecs.com/Ogg_Vorbis_CODEC_for_MSACM_download.htm")
mplayer is able to play ( not vlc because it's not defined

> Opening audio decoder: [acm] Win32/ACM decoders
Loading codec DLL: 'vorbis.acm'
Loaded DLL driver vorbis.acm at 10000000
Warning! ACM codec reports srcsize=0
AUDIO: 48000 Hz, 2 ch, s16le, 450.0 kbit/29.30% (ratio: 56250->192000)
Selected audio codec: [vorbisacm] afm: acm (OggVorbis ACM)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...


---

### Post by andrew.46 on 2010-01-24
Hi mc4man,

> **mc4man said:**
> What's interesting ( in that another file to add to w32codecs) is by adding a win file [vorbis.acm]("http://www.free-codecs.com/Ogg_Vorbis_CODEC_for_MSACM_download.htm")
mplayer is able to play ( not vlc because it's not defined

Thanks for the tip, I have added the codec :). Can be seen here:

```

andrew@skamandros~/samples$ mplayer -ac help | grep vorbis
ffvorbis    ffmpeg    working   FFmpeg Vorbis  [vorbis]
vorbis      libvorbis working   OggVorbis Audio  [libvorbis]
**[COLOR="Red"]vorbisacm   acm       working   OggVorbis ACM  [vorbis.acm][/COLOR]**

```



Andrew

---

### Post by P3t3r on 2010-03-08
So all in all the answer is that it's not possible in VLC? Is that correct? Somehow I find it strange because I remember it used to work before my last crash. But I can't remember how I managed to do it then.

---

### Post by P3t3r on 2010-03-14
Anyone? No vo3+ sound in avi under linux/vlc?

---

### Post by mc4man on 2010-03-14
> Anyone? No vo3+ sound in avi under linux/vlc?
In vlc no, as described with mplayer (vorbis.acm in w32codecs

add. info
[http://lists.xiph.org/pipermail/vorbis/2003-May/023063.html](http://lists.xiph.org/pipermail/vorbis/2003-May/023063.html)

---

### Post by karmila on 2011-03-20
> **andrew.46 said:**
> Hi mc4man,



Thanks for the tip, I have added the codec :). Can be seen here:

```

andrew@skamandros~/samples$ mplayer -ac help | grep vorbis
ffvorbis    ffmpeg    working   FFmpeg Vorbis  [vorbis]
vorbis      libvorbis working   OggVorbis Audio  [libvorbis]
**[COLOR="Red"]vorbisacm   acm       working   OggVorbis ACM  [vorbis.acm][/COLOR]**

```



Andrew

Hi Andrew I need a help, 

I have the same problem with OP. I got the same message when playing an .avi video. Then I went to the link posted by mc4man before, installed it. And this is the result:
```
ari@ari-desktop:~$ mplayer -ac help | grep vorbis
ffvorbis    ffmpeg    working   FFmpeg Vorbis  [vorbis]
vorbis      libvorbis working   OggVorbis Audio  [libvorbis]
vorbisacm   acm       working   OggVorbis ACM  [vorbis.acm]

ari@ari-desktop:~$
```

But later, when I played it with mplayer I still got no sound. This is sound section from mplayer output:
```
==========================================================================
Opening audio decoder: [acm] Win32/ACM decoders
Loading codec DLL: 'vorbis.acm'
Win32 LoadLibrary failed to load: vorbis.acm, /usr/lib/codecs/vorbis.acm
Can't open library vorbis.acm
ACM_Decoder: Unappropriate audio format
Could not load/initialize Win32/ACM audio codec (missing DLL file?).
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x6771.
Audio: no sound
===========================================================================
```

Thanks...

---

### Post by andrew.46 on 2011-03-21
Hi karmila,

You may be interested to know that the newest (2011) collection of MPlayer codecs actually includes vorbis.acm, I don't think the w32codecs package provided by Medibuntu has caught up with this yet. I guess the first step is to make sure that you still have the codec:

```
sudo find /usr -iname vorbis.acm
```

will test that. On my own system:

```

root@skamandros/home/andrew# find /usr -iname 'vorbis.acm'
/usr/lib/codecs/vorbis.acm

```
 
If the codec is definitely there can you post the troublesome avi file somewhere?

Andrew

---

### Post by mc4man on 2011-03-21
Definitely would be interesting to find some common samples - 
Using the one playable one from the videolan link (vorbis3plus.avi ) I've noticed a difference between the current mplayer site vorbis.acm and the linked one
in this case the linked one works, the newer mplayer one doesn't
(ck. the size difference - 1.2 MB vs. 600.1KB

---

### Post by andrew.46 on 2011-03-21
> **mc4man said:**
> Using the one playable one from the videolan link (vorbis3plus.avi ) I've noticed a difference between the current mplayer site vorbis.acm and the linked one
in this case the linked one works, the newer mplayer one doesn't
(ck. the size difference - 1.2 MB vs. 600.1KB

Indeed I can duplicate this on my system, I will draft yet another query to MPlayer users on the weekend and see what the developers think....

---

