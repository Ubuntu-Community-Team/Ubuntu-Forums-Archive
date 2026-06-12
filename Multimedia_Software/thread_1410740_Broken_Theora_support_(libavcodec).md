---
title: "Broken Theora support (libavcodec)"
date: 2010-02-19
forum: Multimedia Software
---

### Post by Emanuele_Z on 2010-02-19
Hi guys,

while writing this application ( [http://qpsnr.youlink.org/](http://qpsnr.youlink.org/) ) I noticed that Theora video streams are broken with current version of libavcodec library.
I opened a bug here: [https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812)
Apparently I have the same issue even on fresh virtualized environments.
To reproduce the issue, do the following:
1) Download [http://launchpadlibrarian.net/39358431/avcodec_sample.cpp](http://launchpadlibrarian.net/39358431/avcodec_sample.cpp)
2) Install *sudo apt-get install g++ libavcodec-dev libavformat-dev libswscale-dev*
3) Compile *g++ ./avcodec_sample.cpp -o av_test -O2 -g -pthread -lavformat -lavcodec -lswscale*
4) Download a reference OGV [http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv](http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv)
5) Execute *./av_test ./matrix-300-AQ.ogv*
Now, you should have in your directory 10 corrupted ppm images (that should be the first 10 frames of the ogv file). If instead you run *./av_test any_other_video_type* you should get the first 10 frames of the video file. It does work for all other formats but for Theora streams.

Is there anyone able/willing to confirm this?

Thanks in advance,
Regards.

---

### Post by VertexPusher on 2010-02-19
> **Emanuele_Z said:**
> 5) Execute *./av_test ./matrix-300-AQ.ogv*
Now, you should have in your directory 10 corrupted ppm images (that should be the first 10 frames of the ogv file).
This command should yield the same result:
```
ffmpeg -vframes 10 -i matrix-300-AQ.ogv frame%d.ppm
```
As you have seen in your bug report, people may tend to dispute the validity of your code rather than the validity of libavcodec. If you can showcase the bug with a standard tool such as ffmpeg, it will be easier to convince reviewers that the bug is in fact in the library rather than in your code.

---

### Post by Emanuele_Z on 2010-02-19
> **VertexPusher said:**
> This command should yield the same result:
```
ffmpeg -vframes 10 -i matrix-300-AQ.ogv frame%d.ppm
```
As you have seen in your bug report, people may tend to dispute the validity of your code rather than the validity of libavcodec. If you can showcase the bug with a standard tool such as ffmpeg, it will be easier to convince reviewers that the bug is in fact in the library rather than in your code.

I see, but the point is that my code is what is recommended by the libavcodec API, plus is short and compact. And, most of all, I'm sure that with my code I'm using libavcodec dynamically plus it works 100% with all other video streams (mpeg, mpeg2, mpeg4,wmv,flv,...).

Actually, it's very simple code, just for the purpose to show the bug.
Clearly it takes less than 5 minutes to spot any bug there.
Naturally if there's an error in API usage, please do tell me.

Cheers,

---

### Post by VertexPusher on 2010-02-19
I'm not saying that your code is wrong. But your bug report will have more impact if you make confirmation of the bug as easy as possible.

---

### Post by Emanuele_Z on 2010-02-19
**UPDATE**:

without recompiling the test executable, but recompiling the shared objects (libav*.so) from the latest cut of ffmpeg svn source code, it does work.
Basically, once recompiled all the libav*.so.* libraries, just put them in the path of the test executable and
*export LD_LIBRARY_PATH=`pwd`*
Magically the executable will now properly decode Theora video streams! :-P
If changing the libraries (again without touching the executable) makes it work, am I wrong saying that the libav*.so.* libraries used in Ubuntu are broken?
Honestly this is prof that against the default libav*.so.* theora streams can't be decoded with libavcodec.
I'll post this on the bug report as well, hopefully this time it will be taken into account.

Cheers,

---

### Post by VertexPusher on 2010-02-19
I think the reason why Reinhard is unable to confirm the bug is because he is using libavcodec52 instead of libavcodec-extra-52 (multiverse). I already mentioned this in the other thread.

I have not tested libavcodec52, but with libavcodec-extra-52 I can easily reproduce the problem with ffmpeg on the command line.

Which libavcodec package have you installed? Maybe you should add this info to the bug report as well.

---

### Post by Emanuele_Z on 2010-02-19
Hi mate,

I've been able to reproduce the issue even on *vanilla* 9.10 i386, on a virtual machine...
Btw I do not have the libav*-extra installed neither on my main x86-64 neither on the virtualized i386. 

I have installed (on both architectures):
libavcodec-dev

Really hopefully this should bring some attention.

---

### Post by Emanuele_Z on 2010-02-19
Reinhard wrote ( [https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812) ):
> 
On Fr, Feb 19, 2010 at 10:10:42 (CET), Emanem wrote:

> And I used against this reference:
> [http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv](http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv)

this file is broken even with current trunk of ffmpeg, so updating
ffmpeg would not help anyways.

please report it upstream using these guidelines:
[http://ffmpeg.org/bugreports.html](http://ffmpeg.org/bugreports.html)

note that there are already a lot of other open issues with avcodecs
theora decoder.


So, as seen as that file ( [http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv](http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv) ) is **not broken** (according to Theora devs that file is made against the finalized Theora video stream format) libavcodec and the other ffmpeg libraries (I suppose) are broken in current Ubuntu packages.
Or better, it doesn't support the finalized Theora format...
Why are you able to playback that file with other players? Because probably those players are statically linked against an updated version of libavcodec...

As I wrote over there, when are we going to support the finalized format of Theora through libavcodec in Ubuntu?

Should the fact that Theora is **the** open source format should catch special attention of maintainers?

Cheers,

---

### Post by mc4man on 2010-02-19
The ffmpeg ver. in karmic and lucid cannot decode video encoded with the new theora - libtheora-1.1.X (has nothing to extra or not

This has been discussed on launchpad previously for karmic and **there is no intention of using a newer ffmpeg version **for either karmic or lucid.

( The 0.5 vs. 0.6 arg. is a bit of a mystery, the version used now is 0.5+svn20090706, there is actually no great reason why +svnXXXXXXXX can't be moved forward - while the benefit of doing that may be minimal to gstreamer apps/plugins it would be seen in vlc, mplayer, and some other apps, both in repo and ppa versions.


What you may wish to try is to build the karmic/lucid ffmpeg source off of the newer libtheora-1.1, and see if it makes a difference, don't know here as I don't use the repo supplied ffmpeg or the shared libs, (odds are it won't

(I always replace the shared once per install with newer deb packages, ffmpeg itself is updated quite often

---

### Post by Emanuele_Z on 2010-02-19
Thanks for confirmation... 
This makes sense, as seen as I'm able to encode/decode with a lot of software which links to libavcodec statically or use other libraries to encode/decode video.

But what you call *new theora* is the **finalized** format/bitstream.
So actually I guess that not ffmpeg, but the underlying libraries should be updated.

Cheers,

---

### Post by mc4man on 2010-02-19
Seeing as though libtheora 1.1.X is the current lib in lucid then the lucid ffmpeg should decode ogv encoded with it. A quick test with your sample does not decode on lucid with the stock ffmpeg.

After work I'll rebuild the lucid ffmpeg source using the newer theora and see if it then does. If so then that's something that could be addressed - as far as trying to get a newer ffmpeg build in lucid I'm not wasting my time anymore...

---

### Post by Emanuele_Z on 2010-02-19
> **mc4man said:**
> Seeing as though libtheora 1.1.X is the current lib in lucid then the lucid ffmpeg should decode ogv encoded with it. A quick test with your sample does not decode on lucid with the stock ffmpeg.

After work I'll rebuild the lucid ffmpeg source using the newer theora and see if it then does. If so then that's something that could be addressed - as far as trying to get a newer ffmpeg build in lucid I'm not wasting my time anymore...

Indeed, because libavcodec in Karmic is not up-to-date as well.
When, as I wrote previously, just moved in the current test applet directory the shared objects (libraries) taken from latest ffmpeg svn cut, everything (*magically* i'd say :-P) worked.
Imho is just that current (in Ubuntu, not ffmpeg) libavcodec don't support proper theora decoding.

Thanks again, let us know your findings! :-)

---

### Post by mc4man on 2010-02-19
Well as I thought the ffmpeg source used in karmic and lucid is too old to support the new libtheora (will build off of without error, won't decode. (did both a static and full debian package builds inc. the extra ver.'s, ect.

So maybe you can make a case there for a newer ffmpeg source - though good luck there...

Had previously tested using more up to date shared ffmpeg libs in karmic and while I certainly didn't try all apps, found only 1 regression - the ffmpeg export in audacity. (and that's because audacity is patched only to accept a specific major/minor version of some ffmpeg libs, a re-build with an adjusted patch fixed that.

And as previously mentioned the whole 0.5 vs. 0.6 is somewhat utter nonsense. (from my perspective which is admittedly more narrow

---

### Post by andrew.46 on 2010-02-19
Hi Emanuele,

> **Emanuele_Z said:**
> So, as seen as that file ( [http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv](http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv) ) is **not broken** (according to Theora devs that file is made against the finalized Theora video stream format) libavcodec and the other ffmpeg libraries (I suppose) are broken in current Ubuntu packages.

I have come rather late into this thread but I suspect Reinhard is correct in that the *most current libavcodec*, let alone the older Ubuntu version, struggles with this particular file:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -vc fftheora matrix-300-AQ.ogv [/COLOR]**
MPlayer SVN-r30637-4.3.3 (C) 2000-2010 MPlayer Team

Playing matrix-300-AQ.ogv.
[Ogg] stream 0: video (Theora v3.2.1), -vid 0
Ogg file format detected.
VIDEO:  [theo]  640x272  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: fftheora
**[COLOR="Red"]Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family[/COLOR]**
[theora @ 0x8954c00]Missing extradata!
Could not open codec.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x6F656874.
==========================================================================


Exiting... (End of file)

```

But the file itself is playable with *external* codec:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]mplayer -vc theora matrix-300-AQ.ogv [/COLOR]**
MPlayer SVN-r30637-4.3.3 (C) 2000-2010 MPlayer Team

Playing matrix-300-AQ.ogv.
[Ogg] stream 0: video (Theora v3.2.1), -vid 0
Ogg file format detected.
VIDEO:  [theo]  640x272  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: theora
Opening video decoder: [theora] Theora/VP3
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [xv] 640x272 => 640x272 Planar YV12 
**[COLOR="Red"]Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))[/COLOR]**
==========================================================================
Audio: no sound
Starting playback...
V: 219.2 5261/5261  4%  1%  0.0% 0 0 

Exiting... (End of file)

```

Andrew

---

### Post by mc4man on 2010-02-19
> ...correct in that the most current libavcodec
Interesting, didn't look at that file in  itself. I guess something to try is encode a video using the current theora and see ...

Anyway here the file in question does play back with ffplay, and if avcodec is forced in vlc it also plays back fine (vlc defaults to theora module

mplayer does exactly as you've shown.
> 
most current

Well that can be a subjective thing, in ubuntu maybe there is a need for a more current version.

> [0x8f1bed0] avcodec decoder debug: ffmpeg codec (Xiph.org's Theora Video) started
[0x8f1bed0] main decoder debug: using decoder module "avcodec"

(vlc 1.05 w/ ffmpeg 21785

---

### Post by Emanuele_Z on 2010-02-19
Hi guys,

first of all thanks for you support.
In all honesty I think is pretty simple issue:
*The libraries (libavcodec/libavformat/...) that are in 9.10 (and apparently even 10.04) are **old** and don't support the **finalized** theora format (and given all the emphasis that Mozilla/Opera are giving regarding the html video tag this seems quite frankly important issue).*
Now, working applications or are using libtheora or a static up-to-date libavcodec implementation (so the latter applications don't rely on the default system's broken libavcodec).
The good thing about shared objects (dynamic libraries) is that if the ABI doesn't change (and it did not) you just update the libraries and all the applications will benefit.
So I guess the solution is straightforward...we don't need to update ffmpeg *per se*, rather the underlying libraries.

Thanks again for your help/tests,
let me know what you think!
I don't know you, but this is very important to me because we're talking about **open format/open standards**. And **Ubuntu imho can't afford not to fully support these**...

Cheers,

Ps. please do post your opinions in the bug here: [https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812) but keep on discussing on the forum! :-D
PPs. I just replace the updated binary libav* shared libraries on my system to test it and...*magic*! As expected it works!

---

### Post by andrew.46 on 2010-02-19
Hi mc4man,

> **mc4man said:**
> Interesting, didn't look at that file in  itself. I guess something to try is encode a video using the current theora and see...

I have produced a simple one to investigate a little further:

```
wget http://www.andrews-corner.org/samples/Rammstein_Du_Hast.ogv
```

and it looks like I must eat my words a little as ffplay has no trouble with this file, it is just MPlayer that barfs...

**Edit:** MPlayer playback with libavcodec possible with *-demuxer lavf* .... Hmmmm.. maybe if I don't post in this thread any more people will forget my idiocy..

Andrew

---

### Post by Emanuele_Z on 2010-02-20
Hi guys.

I've compiled the latest svn libav* for x86-64.
If you want to test the sample av reference program against the finalized format ogv without specifying any additional command line parameter just do the following:
1) download the libraries : [http://rapidshare.com/files/353246095/libav_all.tar.bz2.html](http://rapidshare.com/files/353246095/libav_all.tar.bz2.html)
2) extract the libraries
3) type
```

export LD_LIBRARY_PATH=`pwd`:$LD_LIBRARY_PATH

```
4) get the reference movie here: [http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv](http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv) (this is from a theora dev page)
5) run the sample program
```

./av_sample ./matrix-300-AQ.ogv

```

And it will work!

Cheers,

Btw, how can we ask Ubuntu packages maintainers to fix it?

---

### Post by mc4man on 2010-02-20
> Btw, how can we ask Ubuntu packages maintainers to fix it?
> So I guess the solution is straightforward...we don't need to update ffmpeg per se, rather the underlying libraries.

By requesting they use a current or more current ffmpeg source (ffmpeg), and the odds are, as mentioned here and in lp, they atm won't..

---

### Post by Emanuele_Z on 2010-02-21
Hi mate,

I just don't understand why.
Why do you think they would not?

Cheers,

---

