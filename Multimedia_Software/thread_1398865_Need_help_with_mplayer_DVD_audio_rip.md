---
title: "Need help with mplayer DVD audio rip"
date: 2010-02-05
forum: Multimedia Software
---

### Post by PatrikG on 2010-02-05
I'm trying to rip the audio from a Depeche Mode DVD which has audio in DTS and Dolby Digital (AC3). I want to play the resulting file on my Squeezebox with 5.1 audio.

I have so far tried

[PHP]mplayer -vc null -vo null -aid 137 -channels 6 -ss 00:00:00 -endpos 00:04:21 -ao pcm:fast -ao pcm:file=Track01.wav DVD://07 -DVD-DEVICE /media/cdrom0[/PHP]

But the resulting file is huge and the Squeezebox reports a bit rate of 2300kbps(!). And then I get some memory error and everything breaks down...

I have tried adding -lvcac3enc=1:192 to get a lower bit rate and get it coded to AC3 directly but mplayer reports that this filter is unavailable. When I did that I changed -aid 137 to -aid 128 for the AC3 track.

So does anybody know how I can:
- get AC3 coding to work
- reduce the bit rate

All help appreciated.

Edit
Now solved by doing:
mplayer -vc null -vo null -aid 137 -channels 6 -ac hwdts, -ss 00:00:00 -endpos 00:04:21 -ao pcm:fast -ao pcm:file=Track01_DTS.wav DVD://07 -DVD-DEVICE /media/cdrom0

The DTS stream is now played through my amplifier in 5.1 surround.

---

