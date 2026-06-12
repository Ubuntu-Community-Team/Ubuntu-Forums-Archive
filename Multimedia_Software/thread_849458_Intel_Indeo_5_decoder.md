---
title: "Intel Indeo 5 decoder"
date: 2008-07-04
forum: Multimedia Software
---

### Post by nuwuck on 2008-07-04
Hiu guys  i get an error message when trying to watch a cam recording telling me that i need the intel indeo 5 decoder,  ive googled for it but to be honest im lost..very lost.

Can someone please give me the most simple explanation of what i need to do to get it all working.

Thanks in advance.

---

### Post by kostkon on 2008-07-04
What media player are you using?

I think you need to install the *w32codecs* (windows codecs) package that is offered by the [*Medibuntu*]("http://medibuntu.org/") repository.

Add this repository to your software sources list and the install this codecs package.

If you are using *Totem*, also check if the *gstreamer0.10-pitfdll* package is already installed in your system.

---

### Post by nuwuck on 2008-07-11
Im trying to use totem,vlc and m player, vlc wont open the file at all, and the other 2 tell me i need intel indeo 5 decoder, ive installed all gstream thingys available and no success thus far.

Is there  just a whole package i can install which has everything youll ever need to play any kind of file?

---

### Post by malapet on 2008-12-29
You need win32 codex and 32bit version of ubuntu to play it.
On 64bit system you cant play it even you have win64 codex installed.
I hope somebody fixing that soon on the next upgrade.

---

### Post by Eggz Ackley on 2009-01-28
I have the same problem when I try to open avi video files made by my security camera using totem movie player, it says I have to install intel indeo 5 decoder plug-in, it looks for it and tells me that it can not be found. If I have 64 bit ubuntu, how do I get thsi codec installed??

---

### Post by andrew.46 on 2009-01-31
Hi,

I have some vague memories of this coming up on these forums before? MPlayer should be able to play these files as the full codec pack appears to hold a suitable codec:

```

andrew@skamandros~$ mplayer -vc help | grep -i 'indeo5'
indeo5ds    dshow     working   Intel Indeo 5  [ir50_32.dll]
indeo5      vfwex     working   Intel Indeo 5  [ir50_32.dll]
indeo5xa    xanim     working   XAnim's Intel Indeo 5  [vid_iv50.xa]

```

Just so it does not seem as if I am talking rubbish I downloaded a sample indeo5 file:

[http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi](http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi)

and I attach a screenshot of this fairly forgettable video clip playing successfully. This is all done with the svn MPlayer and a full codec pack, directions are contained in a guide somewhere here on the forums :-).

Andrew

---

### Post by Artou on 2009-02-02
This is the thread I found with the "almost" the solution to play Indeo 5 vids within mplayer/Ubuntu 64, if this is your problem, as it should run OK with 32 bits version. I had some problems compiling though, don't know if it was a problem with current svn. I am still trying to get the gui running.

[http://ubuntuforums.org/showthread.php?t=739011](http://ubuntuforums.org/showthread.php?t=739011)

#Mauro

---

### Post by komputes on 2009-11-29
Playback fails in karmic. Every gstreamer plugin package is installed including pitfdll. win32codecs from medibuntu is installed as well.

totem-> no codec->gnome-app-install gives the following error after looking for a codec

No packages with the requested plugins found
The requested plugins are:
Intel Indeo 5 decoder


-

VLC reports the following error when opening the video:

 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "IV50". Unfortunately there is no way for you to fix this.[/COLOR]


Why is this codec not supported by any of the packages? I have opened a bug, please visit [http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi](http://samples.mplayerhq.hu/V-codecs/IV50/indeo50.avi) and confirm if you still have this issue with this codec in karmic.

[https://bugs.launchpad.net/bugs/490084](https://bugs.launchpad.net/bugs/490084)

---

### Post by mc4man on 2009-11-29
To get out of the way - vlc won't decode IV50, even if you have a dmo loader enabled vlc. There is no fourcc entry in /modules/codec/dmo/dmo.c, though it may be possible to enable

Technically totem should thru pitfdll/w32codecs but it doesn't. Actually pitfdll seems to be somewhat broken in karmic - for instance in hardy I get wma3(pro ) playback thru gstreamer players, not so in karmic.

In karmic (32 bit) mplayer and xine based players will decode. (I happen to have a working totem-xine in karmic that plays your test file fine

So the bug should probably be against gstreamer0.10-pitfdll 

> doug@doug-laptop:~$ gst-inspect pitfdll
Plugin Details:
  Name:			pitfdll
  Description:		DLL-loader elements
  Filename:		/usr/lib/gstreamer-0.10/libpitfdll.so
  Version:		0.9.1.1
  License:		GPL
  Source module:	pitfdll
  Binary package:	PitfDLL
  Origin URL:		[http://ronald.bitfreak.net/pitfdll/](http://ronald.bitfreak.net/pitfdll/)

  qtadec_bin: quicktime binary audio decoder
  dmodec_wmspdmodv1: DMO wmspdmod decoder version 1
  dmodec_wmadmodv3: DMO wmadmod decoder version 3
  dmodec_wmadmodv2: DMO wmadmod decoder version 2
  dmodec_wmadmodv1: DMO wmadmod decoder version 1
  dmodec_wmvdmodv3: DMO wmvdmod decoder version 3
  dmodec_wmvdmodv2: DMO wmvdmod decoder version 2
  dmodec_wmvdmodv1: DMO wmvdmod decoder version 1
  dmodec_wmv9dmodv3: DMO wmv9dmod decoder version 3
  dshowdec_ir41_32v4: DS ir41_32 decoder version 4
  dshowdec_ir50_32v5: DS ir50_32 decoder version 5

---

### Post by six^letters^digits on 2009-12-31
> **mc4man said:**
> vlc won't decode IV50, even if you have a dmo loader enabled vlc. There is no fourcc entry in /modules/codec/dmo/dmo.c

Technically totem should thru pitfdll/w32codecs but it doesn't. Actually pitfdll seems to be somewhat broken in karmic - for instance in hardy I get wma3(pro ) playback thru gstreamer players, not so in karmic.

In karmic (32 bit) mplayer and xine based players will decode. (I happen to have a working totem-xine in karmic that plays your test file 

[Ronald's Room: Pitfdll (Archive.org 2007-01-16)]("http://web.archive.org/web/20070116235424/http://ronald.bitfreak.net/pitfdll/")
[Ronald's Room: Pitfdll]("http://ronald.bitfreak.net/pitfdll.php"):```
PitfDLL
  PitfDLL is a GStreamer plugin that allows the use of binary files, 
such as Quicktime QTX or Directshow/DMO DLL files, 
for use as a playback codec in GStreamer-based media applications, 
such as Totem. With this plugin, people can playback proprietary file formats 
for which no free software implementation exists yet.
  I started the project in 2005. Back then, we had no "native" decoders for 
commonly used + popular media codecs such as 
Windows Media Video 9, Windows Media Audio 9 (WMA-PRO) and alike. 
Back then, I had no idea how to "fix" this codec deficiency. 
All we had was the Windows DLLs that provide playback functionality to 
Windows Media Player or Quicktime Player.
  I started this project so that people using GStreamer could use these Windows DLLs 
and use them to play back media in GStreamer. 
This worked, and still works. 
According to Google Analytics, I get +/- 100 page views per day on this page alone.
  I discontinued development in 2007, and shortly after (early 2008), the project died. 
The remainders can be found on SourceForge and 
anyone is free to use them in whatever way you see fit, 
as long as you comply with the license (GPL). See below for downloads / etc.
  I discontinued the project because I no longer believe this is the right way to go. 
PitfDLL is based on a x86-only DLL loader from Wine 
(also used in Xine, mplayer, avifile). 
Although this might appear to work in practice, it fails in the long run:
    * Technology: it provides us with no insight into how these codecs work, 
and as a result we can also not write native encoders for this format;
    * Portability: it only works on x86 computers, 
and only on the few OSes that the Wine port works on;
    * Bugs: it provides us with no way to fix bugs that exist in the original codebase;
    * Development: we can not add new features to the codecs, 
because we don't have access to their source code;
    * Optimizations: we can not add new optimizations to the codecs,
because we don't have access to their source code.
  The proper way to go - I decided - is to discontinue this project and
focus on writing native implementations of those codecs of interest. 
I do that by contributing to FFmpeg. 
If you want to see native implementations of codecs, please contribute to FFmpeg.
  Features
PitfDLL currently supports:
    * Windows Media Video 7, 8 and 9
    * Windows Media Audio 7, 8 and 9
    * QDesign Music 2 (QDM2)
    * Intel Indeo 5 (IV50)
Requirements
    * GStreamer 0.8.6
    * GStreamer plugins 0.8.8 (0.8.9 or CVS required for QDM2)
    * DLL files, e.g. from the mplayer website
  Availability
PitfDLL is hosted on SourceForge, and file releases are available from there, too.
The latest available release is 0.8.2, which was released on November 14th, 2005.
Information on CVS access is available on SourceForge, too.
FAQ
    * Where does the name come from?
      The name stands for "pitfall", but with a 'd' instead of 'a' for obvious reasons.
Any other naming associations are interesting, but unintended.

```
[GStreamer DLL loader plugin (pitfdll) at SourceForge.net]("http://sourceforge.net/projects/pitfdll/")
PitfDLL is based on a x86-only DLL loader from Wine 
Architecture : i386
[http://packages.ubuntu.com/hardy/gstreamer0.10-pitfdll](http://packages.ubuntu.com/hardy/gstreamer0.10-pitfdll)
[http://packages.ubuntu.com/jaunty/gstreamer0.10-pitfdll](http://packages.ubuntu.com/jaunty/gstreamer0.10-pitfdll)
[http://packages.ubuntu.com/karmic/gstreamer0.10-pitfdll](http://packages.ubuntu.com/karmic/gstreamer0.10-pitfdll)

[http://www.mplayerhq.hu/DOCS/codecs-status.html](http://www.mplayerhq.hu/DOCS/codecs-status.html)
XAnim's Intel Indeo 5  IV50 iv50  vid_iv50.xa  YVU9
MPlayer codecs : [all-20071007.tar.bz2]("http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2")
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
[http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/)
[http://www.3ivx.com/download/unix.html](http://www.3ivx.com/download/unix.html)
[XAnim Video Decompression DLLs]("http://web.archive.org/web/20021206182757/xanim.va.pubnix.com/xa_dlls.html")

[google: "Indeo 5"|iv50|"vid_iv50.xa" MPlayer|totem|xine amd64]("http://www.google.com/search?hl=en&safe=off&num=100&q=%22Indeo+5%22|iv50|%22vid_iv50.xa%22+MPlayer|totem|xine+amd64")

[MPlayer SVN Windows with SMPlayer GUI (via WINE)]("http://downloads.sourceforge.net/smplayer/smplayer-0.6.8-win32.exe")

---

### Post by sensory on 2010-04-17
Not really a solution, but you can re-encode the file with mencoder.

mencoder input.avi -o output.avi -ovc xvid -oac mp3lame -xvidencopts bitrate=687

All I have installed for the pitfdll gstreamers.

---

### Post by Galdor on 2010-08-15
> **komputes said:**
> Playback fails in karmic. Every gstreamer plugin package is installed including pitfdll. win32codecs from medibuntu is installed as well.

totem->  error after looking for a codec
...
VLC reports the following error when opening the video:
VLC does not support the audio or video format "IV50". 
...
Why is this codec not supported by any of the packages? 

I have opened a bug, 
[https://bugs.launchpad.net/bugs/490084](https://bugs.launchpad.net/bugs/490084)

Hello komputes,
I am using karmic -Ubuntu 9.10- the codec is supported, though vlc and totem throwing still the same error message.
I just installed w32 codecs and the xine player.
With the w32 codecs from medibuntu xine is playing the video flawlessly. :)
Hope this helps.
Nethertheless, vlc & totem should do the same as well as xine.
regards

---

