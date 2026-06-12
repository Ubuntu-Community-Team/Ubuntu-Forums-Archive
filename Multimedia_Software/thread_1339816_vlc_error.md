---
title: "vlc error"
date: 2009-11-27
forum: Multimedia Software
---

### Post by sudoer541 on 2009-11-27
When I try to stream a tv show I get this error: 



 p, li { white-space: pre-wrap; }  **[COLOR=#FF0000]No suitable decoder module:[/COLOR]**
 **[COLOR=#000000]VLC does not support the audio or video format "VP62". Unfortunately there is no way for you to fix this.[/COLOR]**
 [COLOR=#000000][/COLOR]


I go to media> service discovery > shoutcast TV listings and I select a program to watch (any) and I get the error above.

---

### Post by Yellow Pasque on 2009-11-28
Perhaps try the w32codecs package from medibuntu: [http://packages.medibuntu.org/karmic/w32codecs.html](http://packages.medibuntu.org/karmic/w32codecs.html) . It has a vp6 decoder in it.

EDIT: You'll also have to use some video player that uses ffmpeg/libavcodec, like totem or xine.

---

### Post by mc4man on 2009-11-28
vp6 and earlier decoding can be thru avcodec in vlc and others (mplayer, totem-xine, ect. with either libavcodec or w32codecs
The only thing that can't be decoded is vp6 audio, but usually the audio is aac or mp3.

As far as your shoutcast video's, if you have a decent vlc, either built off of or in the presence of a un-neutered libavcodec they should play back. (though the quality is fairly low, see screen

You could test your players (and libavcodec) by trying any of these vp6-e,s samples - [sd here]("http://www.on2.com/index.php?566"), [hd here]("http://www.on2.com/index.php?591") ( the sd's can be grabbed from /tmp after buffering, the hd can be dl'ed. 

ex.'s of vlc from debug with normal vp6 and vp6-e (flash

> [0xb7004fc0] avcodec decoder debug: ffmpeg codec (On2's VP6.2 Video) started
[0xb7004fc0] main decoder debug: using decoder module "avcodec"

> [0xb7031898] avcodec decoder debug: ffmpeg codec (On2's VP6.2 Video (Flash)) started 

(( [vp7]("http://www.on2.com/index.php?617") can only be done I believe thru mplayer, though  enabling in vlc source maybe possible

> Loaded DLL driver vp7vfw.dll at 10000000
[PP] Using codec's postprocessing, max q = 9.
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1920x816 => 1920x816 Packed YUY2 
Selected video codec: [vp7] vfm: vfwex (On2 VP7 Personal Codec)


---

### Post by sudoer541 on 2009-11-28
I installed the W2codecs and libavcodec but I get audio and no video.
When I had ubuntu  9.04 vlc worked great with ubuntu restricted extras? why I am having this problem on 9.10?

---

### Post by Yellow Pasque on 2009-11-28
Start vlc in terminal and post the log?

---

