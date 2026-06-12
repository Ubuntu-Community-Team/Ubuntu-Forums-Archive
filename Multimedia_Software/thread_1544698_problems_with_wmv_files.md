---
title: "problems with wmv files"
date: 2010-08-02
forum: Multimedia Software
---

### Post by GregD001 on 2010-08-02
hello, i have some wmv files i am trying to play.  And am getting errors when playing.
In totem movie player it looks for windows media audio 9 decoder.  But it cannot find it.
in vlc  i get the error
VLC does not support the audio or video format "wmap". Unfortunately there is no way for you to fix this.

searching these forums i found this post
[http://ubuntuforums.org/showthread.php?t=537065](http://ubuntuforums.org/showthread.php?t=537065)
which said to install these codecs
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

However i am still having the problem.

any ideas?
thanks

---

### Post by GregD001 on 2010-08-02
its actually visual studio training.
But I would like to just watch on my dell mini 9 / ubuntu laptop.  if i could.

---

### Post by mc4man on 2010-08-02
post what release of ubuntu you're using.

---

### Post by wookieshaver on 2010-08-02
Follow the instructions here: [http://ubuntuforums.org/archive/index.php/t-537065.html](http://ubuntuforums.org/archive/index.php/t-537065.html) as this solution worked for the same issue with wmap files!

---

### Post by GregD001 on 2010-08-02
Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 

I will take a look at the link

thanks

---

### Post by SunnyRabbiera on 2010-08-03
WMV is probelmatic, its much like AVI...
I will paraphrase what i said earlier on the subject:

Certain formats are a little shaky on linux, especially WMV as some WMV vidoes work and some dont.
This is because WMV is a microsoft format, and as such does not play nice with others.
Not all the time this is the case mind you but some WMVs do have coding for windows media player 11 and above and linux can do up to WMP 10 thanks to the reverse engineered codecs.
you may wish to install realplayer as it does have compatibilty for later versions of the format.
Linux does have its drawbacks though most of them are easy enough to get around

Try installing mplayer, all gstreamer packages (good bad ugly) and windows media codecs.
Medibuntu also helps

---

### Post by mc4man on 2010-08-03
> Ubuntu 10.04 
If you add this ppa and update your gstreamer plugins then you will get pretty full wmv and wma support in gstreamer apps (32 and 64 bit installs
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Note: this ppa is from the same people who maintain the ubuntu plugins - highly trusted imo

These are the 3 plugins needed overall
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

On lucid
> doug@doug-laptop:~$ gst-inspect plugin ffmpeg | grep wma
  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder
  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder

doug@doug-laptop:~$ gst-inspect plugin ffmpeg | grep wmv
  ffenc_wmv1: FFmpeg Windows Media Video 7 encoder
  ffenc_wmv2: FFmpeg Windows Media Video 8 encoder
  ffdec_wmv1: FFmpeg Windows Media Video 7 decoder
  ffdec_wmv2: FFmpeg Windows Media Video 8 decoder
  ffdec_wmv3: FFmpeg Windows Media Video 9 decoder


(in the upcoming maverick this is the default for gstreamer and  also for vlc

---

