---
title: "Can't play WM9 Audio"
date: 2010-01-16
forum: Multimedia Software
---

### Post by Emanuele_Z on 2010-01-16
Hi guys,

When I try to play one movie with WM9 audio all I get is:
```

Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0x7f1b7a5b6a80]Extra data: 8 bits left, value: 0
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)

```
My mplayer has the following codecs enabled:
```

wma9dmo     dmo       working   Windows Media Audio 9 DMO  [wma9dmod.dll]
wmadmo      dmo       working   Windows Media Audio DMO  [wmadmod.dll]
wma9spdmo   dmo       working   Windows Media Audio 9 Speech DMO  [wmspdmod.dll]
wma9spdshow dshow     working   Windows Media Audio 9 Speech DShow  [wmavds32.ax]

divx        acm       working   DivX audio (WMA)  [divxa32.acm]
ffwmav1     ffmpeg    untested  DivX audio v1 (FFmpeg)  [wmav1]
ffwmav2     ffmpeg    untested  DivX audio v2 (FFmpeg)  [wmav2]

```
I'm using Ubuntu 9.10 x86-64.
Any Idea how to fix this?
Do I have to recompile mplayer to support this?
Because when I use the default player (totem?) it says:
```

No packages with the requested plugins found
The requested plugins are:

Windows Media Audio 9 decoder

```
I tried w64codecs from medibuntu but it doesn't work...

Cheers,

Ps. Video is form here: [http://www.projectoffset.com/media/Video/Meteor.wmv](http://www.projectoffset.com/media/Video/Meteor.wmv)

---

### Post by fancypiper on 2010-01-16
I can play the video very slowly, but with no sound.  I don't believe there is a fix unless you can run something through wine.

By the time the devs reverse engineer WM9 Audio, Microsoft will come out with WM10 :eek:

---

### Post by mc4man on 2010-01-16
> Do I have to recompile mplayer to support this?
If you where to build your own mplayer than you would get wma3 support thru libavcodec (built-in

What you could also do without building is install an mplayer from a ppa who's build doesn't depend on your ubntu shared ffmpeg libs - from [here ]("https://launchpad.net/~rvm/+archive/mplayer")should probably be good.

As far as your video am dl'ing now to test, considering it's vc1/wma3 you may wish to glance [here]("http://ubuntuforums.org/showthread.php?p=8674045#post8674045") - the audio will be interesting, showing as 

> Windows Media Audio 10 Professional - 440 kbps, 96 kHz, 2 channel 24 bit 2-pass VBR

---

### Post by mc4man on 2010-01-16
> am dl'ing now to test
Turns out it's not vc1 video or not one that would need ffvc1, in any event plays fine in mplayer without the use of any dmo decoders (which are only available in 32 bit
So while I use 32 bit, forced mplayer to use  only ff for decoding
> doug@doug-laptop:~$ mplayer -vc ffwmv3 '/home/doug/Desktop/dmmplayer/Meteor.wmv'
Playing /home/doug/Desktop/dmmplayer/Meteor.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  1920x1080  24bpp  1000.000 fps  8000.0 kbps (976.6 kbyte/s)
...clipped
Forced video codec: ffwmv3
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0x8aefbc0]Extra data: 8 bits left, value: 0
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg WMV3/WMV9)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 96000 Hz, 2 ch, floatle, 440.0 kbit/7.16% (ratio: 55000->768000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
AO: [pulse] 96000Hz 2ch floatle (4 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 


(also plays fine in a built vlc using only ffmpeg (avcodec)  - heavily clipped the terminal output
> vlc -vv '/home/doug/Desktop/dmmplayer/Meteor.wmv' 
VLC media player 1.0.4 Goldeneye
[0x999a168] main input debug: creating demux: access='' demux='' path='/home/doug/Desktop/dmmplayer/Meteor.wmv'
[0x999d1c8] asf stream debug:   - codec[0] audio name:"Windows Media Audio 10 Professional" description:"440 kbps, 96 kHz, 2 channel 24 bit 2-pass VBR" information_length:2
[0x999d1c8] asf stream debug:   - codec[1] video name:"Windows Media Video 9" description:"Professional" information_length:4
[0x99a21d0] avcodec decoder debug: ffmpeg codec (Windows Media Audio Professional) started
0x999df08] avcodec decoder debug: ffmpeg codec (Windows Media Video 3) started
ect. ect.
So a built or probably ppa mplayer and you should be good to go, vlc is a bit more involved

(another option, though I don't think needed, is to build and install a 32 bit mplayer - have a post and links if desired

---

### Post by Emanuele_Z on 2010-01-16
Why do you recommend the 32 bit build when I'm using 64 bit OS?
Anyway, should I use that ppa?
What is the issue with the audio anyway? Codec not supported yet or patent encumbered that can't be included in default distro?

Cheers,

---

### Post by mc4man on 2010-01-16
> Why do you recommend the 32 bit build when I'm using 64 bit OS?

Where did I say use a 32 bit build except in a final comment that also included this
> (another option, though I don't think needed, .....

> What is the issue with the audio anyway?
The issue, that I thought was made clear here or in post linked to (and in numerous other similar threads) is that wma3 decoding needs either a dmo which is only available in 32 bit (w32codecs) OR a player that has wma3 decoding enabled thru libavcodec, whether built-in to the player or thru a shared libavcodec

A shared libavcodec that's wma3 capable is not yet nor has ever been available in ubuntu thru ubuntu repo's ( and by extension any player doing the decoding thru libavcodec

---

### Post by andrew.46 on 2010-01-16
Hi mc4man,

> **mc4man said:**
> [...] wma3 decoding needs either a dmo which is only available in 32 bit (w32codecs) OR a player that has wma3 decoding enabled thru libavcodec, whether built-in to the player or thru a shared libavcodec

In this particular clip I believe that ffwmv3 playback is superior to wmv9dmo playback on my low budget system. ffwmv3 shows better detail, colours are better and playback is smoother. Good news for 64bit users with no easy access to the external codecs :).

@Emanuele_Z: nice clip, is this part of an animated movie?

**Edit:** Mind you a bit of FFmpeg magic can show that these Microsoft codecs are pretty easily matched by open source alternatives. Have a look at this quick effort:

```
wget http://www.andrews-corner.org/samples/meteor_redux.mp4
```

I had to resize a little so my poor system could play it back, and note that the sound crumbles at the end of the original clip as well, but I guess the point is that playback (as mc4man has pointed out) and conversion (as I have demonstrated) is possible...

Andrew

---

### Post by Emanuele_Z on 2010-01-17
Thanks mate.
Unluckily is not my stuff! :-)
This should be a real time engine called offset, that was done a an ISV bought in 2008 by Intel to produce some *ready-to-go* software for their new manycore videocards (Larrabee).

How do I use the ffwmv3 without having to recompile anything (if that's possible)?

Poking around with other multimedia editors/converter I noticed that many of them don't dynamically link the libraries but use static library linking (ie. import the code from the .a). I don't understand this, because if you dynamically link then next time there's an upgrade of the library you get it *for free* in your application...

Cheers,

Ps. I donwloaded and forced install of w32codecs but nothing as well...

---

### Post by andrew.46 on 2010-01-18
Hi Emanuaele,

> **Emanuele_Z said:**
> How do I use the ffwmv3 without having to recompile anything (if that's possible)?

I suspect a newer version of MPlayer would be a step in the right direction and, as mc4man has previously suggested, perhaps the easiest way is to install a copy of MPlayer from a PPA. One with a good reputation can be seen here:

[https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa)

complete with directions for use. It would be an idea to pick up a copy of SMPlayer as well from here.

All the best,

Andrew

---

### Post by sports.car.guy on 2010-01-18
If you are using Nvidia hardware and their drivers you could always try VDAPU which supports WM9 through hardware.

---

### Post by TwistedTripper on 2010-01-18
I downloaded that Meteor.wmv and played fine in totem using x64 Karmic but I have the Fluendo 10 codecs installed which aren't free but work pretty well.

---

