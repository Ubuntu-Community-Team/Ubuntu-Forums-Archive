---
title: "WMA songs causing an bizarre problem"
date: 2010-07-07
forum: Multimedia Software
---

### Post by Trilby on 2010-07-07
Something rather odd has just happened with my music collection. Most of the songs I have are mp3's, but I have a few wma's kicking about. Up until recently, I've never had any difficulty in playing them (I use Rhythmbox). However, with warning, I find myself unable to play my wma's. Instead, I get the message:

> **Search for suitable plugin?**
The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?
The search will also include software which is not officially supported.

The search is unsuccessful and I get the message:

> **No packages with the requested plugins found**
The requested plugins are:
Windows Media Audio 8 decoder

This seems very strange since my mp3's still play and there was no problem with anything a few days ago. I know I could convert my wma's into mp3's or ogg's but it's still inconvenient not to be able to play wma's.

I've tried installing/reinstalling a number of packages and pluggins, but to no effect.

Thanks for any help given,
Trilby


*Please take note that I am running a 64 bit system.*

---

### Post by hansdown on 2010-07-07
Hi Trilby.

Do you have

```
ubuntu-restricted-extras

```

installed, from synaptic?

---

### Post by mc4man on 2010-07-07
If you didn't get it going install this
```
 sudo apt-get install gstreamer-tools
```

Then run
```
gst-inspect | grep wma
```

A fully enabled gstreamer in lucid would report this, but you're only concerned with what I've marked in bleu

> doug@doug-desktop1:~$ gst-inspect | grep wma 
ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
ffmpeg:  [COLOR="Blue"]ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder[/COLOR]
ffmpeg:  [COLOR="Blue"]ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder[/COLOR]
ffmpeg:  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder



---

### Post by Yellow Pasque on 2010-07-08
[http://ubuntuforums.org/showthread.php?t=1520301](http://ubuntuforums.org/showthread.php?t=1520301)

---

### Post by Trilby on 2010-07-08
> **hansdown said:**
> Hi Trilby.

Do you have

```
ubuntu-restricted-extras

```

installed, from synaptic?

Yes

>  fully enabled gstreamer in lucid would report this... 

I get this:

```
:~$ gst-inspect | grep wma
typefindfunctions: video/x-ms-asf: wmv, [COLOR="Red"]wma[/COLOR], wm, asf
```

wma appears in red on my terminal screen.

> [http://ubuntuforums.org/showthread.php?t=1520301](http://ubuntuforums.org/showthread.php?t=1520301)

Um, that went over my head slightly; I'm not quite sure what I need to do.

---

### Post by Trilby on 2010-07-10
Never mind. For unrelated reasons, I've had to do a clean install and now everything works again.

Thanks anyway guys :-)

---

### Post by rtruth on 2010-07-10
Hello Friends,

I've recently installed Ubuntu 9.04. After being a Windows user for close to 10 years, for the first time in my life I am trying a new Operating System such as Ubuntu.

First and foremost I would like to thank the developers of Ubuntu 9.04 for comming up with such an excellent product. It is way better than Windows. I am impressed by it's security, free open source softwares, and it's loading time. 

Now I have a little problem with the audio properties of Ubuntu. When I play an audio, the clarity is excellent no doubt about it. It's way better than Windows. But when I leave Ubuntu idle for about 10 minutes the audio stops automatically. And only when I move the mouse pointer or press any key in the Keyboard, as the audio continues to play.

Kindly help me out in finding what is the issue all about and what is the best way to fix it.

Thanks in advance,
A. Alex.

---

