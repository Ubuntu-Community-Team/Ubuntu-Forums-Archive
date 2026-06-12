---
title: "Banshee can't stream rtmp..."
date: 2010-04-09
forum: Multimedia Software
---

### Post by Igneo676 on 2010-04-09
Can't seem to get a few of my favorite radio stations on Banshee unfortunately: they use rtmp streams and I can't seem to get any extensions that could potentially solve my issue. I know flvstreamer and red5 have the capabilities? But I can't find anything to bring their capabilities to Banshee...

...anyone know a solution or shall I be barred forever from my lovely radio stations? :(

---

### Post by andrew.46 on 2010-04-09
Hi Igneo676,

Can you give the address of these streams?

Andrew

---

### Post by Igneo676 on 2010-04-09
[http://boss.streamos.com/wmedia-live/emf/6503/32_emf-klove_040506.asx](http://boss.streamos.com/wmedia-live/emf/6503/32_emf-klove_040506.asx)

rtmp://emf.fl.miisolutions.net/air1-live01/air1/air1_high

hmm, guess I didn't take a look at the first one...
...it doesn't appear to be what I am talking about but still doesn't work. Someone had declared it to be rtmp, but the latter one certainly is.

---

### Post by andrew.46 on 2010-04-09
Hi Igneo,

> **Igneo676 said:**
> [http://boss.streamos.com/wmedia-live/emf/6503/32_emf-klove_040506.asx](http://boss.streamos.com/wmedia-live/emf/6503/32_emf-klove_040506.asx)

If you have a look inside the asx information you will see the problem with this particular file:

```

Sorry, the file you have requested has exceeded its bandwidth allotment.
Please feel free to contact Customer Care if you have further questions
about this content.

```

> 
rtmp://emf.fl.miisolutions.net/air1-live01/air1/air1_high


I had some hope that the newest MPlayer might have some success with this one but it failed miserably :(.

Andrew

---

### Post by Igneo676 on 2010-04-09
Hmm, that is quite sad...
...thanks for your help, but does this mean I am doomed forever to listen to it on the *shivers* radio >.<?

Edit: oh, hey, that was an old link for the first stream:

mms://wm-live.world.mii-streaming.net/live/klove/high_01

or, they also have

rtmp://emf.fl.miisolutions.net/klove-live01/klove/klove_high

I was searching so much for a solution that I didn't double check if the streams I was given were correct. Got these myself off their website

The second stream was good, but ALSO I found an mms...
...can't seem to manage to get em to work in Banshee though

Edit2:

Even more odd, my banshee doesn't support it on my desktop but does on my laptop...

---

### Post by Igneo676 on 2010-04-09
I'll go ahead and say this is solved, thanks man. It's obvious not the fault of Banshee that it can't stream these mms streams and a product of recent tinkering with my desktop. I use my laptop for stuff at school and keep it tinkering-free so that explains it

Doesn't help that I'm using an experimental version of Banshee, so yeah, :P

Thanks again

---

### Post by andrew.46 on 2010-04-10
Hi Igneo,

I will admit that I am not a Banshee user but the mms streams run well enough in MPlayer:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer mms://wm-live.world.mii-streaming.net/live/klove/high_01[/COLOR]**
MPlayer SVN-r31028-4.3.3 (C) 2000-2010 MPlayer Team

Playing mms://wm-live.world.mii-streaming.net/live/klove/high_01.
STREAM_ASF, URL: mms://wm-live.world.mii-streaming.net/live/klove/high_01
Resolving wm-live.world.mii-streaming.net for AF_INET6...
Couldn't resolve name for AF_INET6: wm-live.world.mii-streaming.net
Resolving wm-live.world.mii-streaming.net for AF_INET...
Connecting to server wm-live.world.mii-streaming.net[64.191.193.123]: 1755...
Connected
unknown object
file object, packet length = 5976 (5976)
unknown object
stream object, stream ID: 1
unknown object
unknown object
data object
mmst packet_length = 5976
Cache size set to 64 KBytes
Cache fill:  0.00% (0 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16002->176400)
**[COLOR="Red"]Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:507518.4 (140:58:38.4) of 1844674428928.0 (512409563:35:28.0)  9.0% 21% 

```

and a quick look with vlc confirmed it also plays there. Still no luck with the rtmp stream though :(.

Andrew

---

### Post by WinterRain on 2010-04-10
> **Igneo676 said:**
> 

mms://wm-live.world.mii-streaming.net/live/klove/high_01



That stream plays fine in vlc. Just open vlc, media>open network stream and paste link and hit play.

---

