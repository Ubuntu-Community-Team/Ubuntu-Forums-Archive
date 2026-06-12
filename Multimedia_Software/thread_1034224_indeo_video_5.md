---
title: "indeo video 5"
date: 2009-01-08
forum: Multimedia Software
---

### Post by madsporkmurderer on 2009-01-08
I'm trying to convert some avi files to flv, it seems the video is indeo5. Ffmpeg doesn't seem to support this, is there another way to do it?

Thanks,
Mike

---

### Post by FakeOutdoorsman on 2009-01-08
mencoder with the binary codecs should be able to convert this, but you may have to compile your own mencoder.

---

### Post by andrew.46 on 2009-01-08
Hi,

MPlayer when compiled from svn and with the full codec pack seems to be able to *play* such a video:

```
andrew@skamandros~$ mplayer -vc help | grep 'indeo[0-9]'

ffindeo3    ffmpeg    working   FFmpeg Intel Indeo 3.1/3.2  [indeo3]
ffindeo2    ffmpeg    working   Indeo 2 native decoder  [indeo2]
[B][COLOR="Red"]indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]
indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll][/COLOR][/B]
indeo4      vfw       working   Intel Indeo 4.1  [ir41_32.dll]
indeo3      vfwex     working   Intel Indeo 3.1/3.2  [ir32_32.dll]
**[COLOR="Red"]indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa][/COLOR]**
indeo4xa    xanim     working   XAnim's Intel Indeo 4.1  [vid_iv41.xa]
indeo3xa    xanim     working   XAnim's Intel Indeo 3.1/3.2  [vid_iv32.xa]
```

and so presumably Mencoder could also deal with such a file and perform the conversion you are after. More than a little unusual that MPlayer is ahead of ffmpeg with encoding though :-). Is there a sample online or can you place one somewhere? Best way to carve off a piece is:

```
$ dd if=yourfile of=smallfile bs=1024k count=5
```

with 'yourfile' being your problem file and 'smallfile' being the sample produced by the command. Not sure if this will be too big for the forums though.

Andrew

---

### Post by andrew.46 on 2009-01-09
Hi again!

Just a look at the MPlayer html docs and the good news is there is an example 'Creating a Macromedia Flash video suitable for playback in a web browser with the Macromedia Flash plugin' :

```
mencoder input.avi -o output.flv -of lavf \
    -oac mp3lame -lameopts abr:br=56 -srate 22050 -ovc lavc \
    -lavcopts vcodec=flv:vbitrate=500:mbd=2:mv0:trell:v4mv:cbp:last_pred=3

```

This should be useful I suspect?

Andrew

---

