---
title: "Re VLC MKV bug &quot;hevc&quot; strange error"
date: 2015-08-30
forum: Multimedia Software
---

### Post by Blake_Crawford on 2015-08-30
I have some MKV files aqquired in the Wild which work on my Android installation of VLC. However, under Ubuntu fully updated, I get an error for unsupported format "Hevc".  

Being the smart ass that I am, I just installed Wine, and installed the Windows version of VLC within it.  

While performance is lack-luster, I am able to watch the videos in the emulated enviornment.  

My question is:

Can this even be fixed? Or am I just boned until VLC decides to update the Ubuntu build?

Interesting bit of useless info, if I constantly wiggle my cursor over the video in wine the frame rate is normal.

Codec MPEG-H part2/HEVC (h.265) 
This is what the windows version has to say about the codec.

Last update:
The Wine version if VLC actually appears under my "open with" options, and using that link and full-screening the video renders 95% normal frame rates.  

So, if you have this issue and hate windows as much as I do, this is an 'acceptable' work around. 

But I'd love to hear options.  VLC says "unfortunately there is no way for you to fix this" to which I must reply "you don't know me" ;)

---

### Post by mc4man on 2015-08-30
hevc support in vlc depends on whether hevc is supported in the libav or ffmpeg version vlc is built off of. 
Assuming you have **14.04 **then vlc uses libav9 so no hevc support.

Options:
1. build your own vlc using a current statically linked libav (libav11) or FFmpeg
2. use a ppa version of vlc built off of  either libav11 or FFmpeg
3. use a ppa version of vlc (2.2.1) built off of libav9  with vlc-plugin-libde265  package suitable for vlc-2.2.1
4. use current vlc from ubuntu repo (vlc-2.1.6) with vlc-plugin-libde265 suitable for 2.1.6

For option 4 use plugin from here - [https://launchpad.net/~strukturag/+archive/ubuntu/libde265](https://launchpad.net/~strukturag/+archive/ubuntu/libde265)

---

### Post by Blake_Crawford on 2015-09-01
Well after a hard fought night trying to compile VLC from source and getting dragged ever deeper down a rabbit hole, I gave in and installed 15.04.  Little things like "install the latest codec" can be such a huge seemingly ridiculous battle on Ubuntu.  For an OS that touts being universally accessible, it can really be a galactic pain in the ass to accomplish something a trained gorilla could accomplish in windows by accidentally clicking "okay" when the player asks to search for codecs.  

All ranting aside I'm happy to say I can now watch my video file without a laggy work around.

---

### Post by SeijiSensei on 2015-09-01
I haven't found anything I can't watch with mpv and SMPlayer as the graphical front-end.

---

### Post by mc4man on 2015-09-01
> **Blake_Crawford said:**
>  it can really be a galactic pain in the ass to accomplish something a trained gorilla could accomplish in windows by accidentally clicking "okay" when the player asks to search for codecs.  

All ranting aside I'm happy to say I can now watch my video file without a laggy work around.
Well I use Windows quite often though I doubt any gorilla, trained or otherwise, could playback a flac file in media player easily.
So the point is no matter what Os a little research *before* acting can prove fruitful.

---

### Post by Yellow Pasque on 2015-09-01
> **SeijiSensei said:**
> I haven't found anything I can't watch with mpv

I use mpv as well (either by itself or with bomi fronetend), but just like VLC, it depends on what libav/ffmpeg you built against.

---

