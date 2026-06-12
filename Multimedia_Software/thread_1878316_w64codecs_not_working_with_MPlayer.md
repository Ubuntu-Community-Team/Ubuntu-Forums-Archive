---
title: "w64codecs not working with MPlayer"
date: 2011-11-09
forum: Multimedia Software
---

### Post by notmyidea on 2011-11-09
Hi All,

I am trying to play an XAnim Intel Indeo 4.1 video with MPlayer on Ubuntu x64.  I have w64codecs installed from medibuntu.  Issuing:

mplayer -vc help | grep Indeo

Produces:

ffindeo3    ffmpeg    working   FFmpeg Intel Indeo 3.1/3.2  [indeo3]
ffindeo2    ffmpeg    working   FFmpeg Indeo 2  [indeo2]
indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]
indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll]
indeo4      vfw       working   Intel Indeo 4.1  [ir41_32.dll]
indeo3      vfwex     working   Intel Indeo 3.1/3.2  [ir32_32.dll]
indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa]
indeo4xa    xanim     working   XAnim's Intel Indeo 4.1  [vid_iv41.xa]
indeo3xa    xanim     working   XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]
ffindeo5    ffmpeg    working   FFmpeg Indeo 5  [indeo5]
qtindeo     qtvideo   crashing  Win32/QuickTime Indeo  [QuickTime.qts]

So would seem like it is supported but when I go to play it mplayer produces this error message and I only get sound:

xacodec: failed to dlopen /usr/lib/codecs/vid_iv41.xa while /usr/lib/codecs/vid_iv41.xa: cannot open shared object file: No such file or directory
VDecoder init failed :(

Any suggestions?

Thanks.

---

### Post by andrew.46 on 2011-11-09
Try:

```
mplayer -vfm ffmpeg *[COLOR="Red"]<filename>[/COLOR]*
```

using your own filename of course...

---

### Post by mc4man on 2011-11-09
Not sure if those vids can use FFmpeg to decode. If not then w64codecs will do you no good - last I checked there were only 3 in it, 2 of which ffmpeg handles, the 3rd is an obscure quicktime one

It's possible that  "XAnim Intel Indeo 4.1 video" needs the XAnim dll's, not the intel Indeo ones. In any event I believe both are 32 bit only
(vid_iv41.xa - avaible from mplayer codecs page

---

### Post by jmate24 on 2011-11-09
just install prelink from synaptic and run:

```
sudo prelink -v -a -f
```

---

### Post by notmyidea on 2011-11-09
> **andrew.46 said:**
> Try:

```
mplayer -vfm ffmpeg *[COLOR="Red"]<filename>[/COLOR]*
```

using your own filename of course...

That produces:

Requested video codec family [indeo4] (vfm=vfw) not available.
Enable it at compilation.

```
mplayer -vfm xanim
```

produces same output as before.


```
sudo prelink -v -a -f

```

doesn't change anything (and prelinks all ELF binaries on the system).

> Not sure if those vids can use FFmpeg to decode. If not then w64codecs will do you no good - last I checked there were only 3 in it, 2 of which ffmpeg handles, the 3rd is an obscure quicktime one

It's possible that "XAnim Intel Indeo 4.1 video" needs the XAnim dll's, not the intel Indeo ones. In any event I believe both are 32 bit only
(vid_iv41.xa - avaible from mplayer codecs page 

Looks like it won't run on x64. I'll have to VirtualBox a 32 bit system to make this work.  Frustrating!!

Thanks for the help.

---

