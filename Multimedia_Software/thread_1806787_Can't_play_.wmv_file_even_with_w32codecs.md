---
title: "Can't play .wmv file even with w32codecs"
date: 2011-07-18
forum: Multimedia Software
---

### Post by The_Eddster on 2011-07-18
I have this .wmv video I'm trying to play in movie player, but I get this error: ```
video/x-asf-unknown decoder
```
and then it plays just the audio. When I try vlc, it just says ```
VLC does not support the audio or video format "G2M4"
```. I have installed the ubuntu-restricted-extras and w32codecs as instructed [here]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-on-ubuntu-11-04-natty.html") 

How do I fix this problem?

I'm using Ubuntu 11.04 32-bit

---

### Post by nomko on 2011-07-18
Did you try to play the file with Vlc? 
Vlc is a audio/movie player which plays almost everything without any extra plugins.

---

### Post by qamelian on 2011-07-18
It looks like you're trying to play a video the requires the go-to-meeting codec. There is no version of this codec for Linux, but you may find the site below to be helpful:

[http://onlinemeeting.lefora.com/2009/12/08/guide-to-using-gotomeeting-on-linux/](http://onlinemeeting.lefora.com/2009/12/08/guide-to-using-gotomeeting-on-linux/)

---

### Post by nomko on 2011-07-18
> **qamelian said:**
> It looks like you're trying to play a video the requires the go-to-meeting codec. There is no version of this codec for Linux, but you may find the site below to be helpful:
 
[http://onlinemeeting.lefora.com/2009/12/08/guide-to-using-gotomeeting-on-linux/](http://onlinemeeting.lefora.com/2009/12/08/guide-to-using-gotomeeting-on-linux/)
 
Normally there's no need for extra plugins/tools. Vlc can play .mwv files perfectly. I never had any issues with such kind of files when using Vlc.

---

### Post by qamelian on 2011-07-18
> **nomko said:**
> Normally there's no need for extra plugins/tools. Vlc can play .mwv files perfectly. I never had any issues with such kind of files when using Vlc.
VLC can only play files for which it has a codec. If you look at the original post, the OP has already tried VLC with all codecs installed and VLC does not understand media files created by Go To Meeting. The link I posted contains information on how to play these files back using mplayer, wine, and the Windows dll containing the codec. 

Although VLC is a very capable media player, it does not play everything. There are several codecs like this that for one reason or another it does not or cannot support. Fortunately, the unsupported codecs are very seldom encountered by most users.

You have to realize that WMV, like AVI and several other media types, is only a container format and doesn't define the actual audio or video codec used to encode the contents.

---

