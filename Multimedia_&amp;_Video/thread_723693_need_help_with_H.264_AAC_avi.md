---
title: "need help with H.264 AAC avi"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by Ubermouser on 2008-03-13
I've been using a program called MCEBuddy - which takes the 4gb monstrosities that windows media center records, puts them on a diet, and transforms them into pretty little 600mb videos - to shrink down half a terrabyte of bloated television shows my HTPC has recorded. I dual boot to Vista 64 and had no problems playing these new files, but I've been having trouble doing the same in Ubuntu. According to Gspot in Wine, the audio is encoded in the "FAAD AAC" format, and the video in the "H.264" format. Ubuntu's default video player was able to play the video perfectly, but was unable to play the audio that went with the video. After looking around these forums for help, I finally downloaded the VLC media player after being unable to get the audio to work in Totem. I'm able to play other videos with the H.264 video format along with .m4a files which I thought were basically AAC files, but can't seem to play them both at the same time.

Has anyone had any success in playing a file of this type? If so, what did you do in order for it to work? Thanks in advance for your response!

Totem gave me this message when trying to play the file:
```
** Message: don't know how to handle audio/x-avi-unknown, codec_id=(int)28781
** Message: Missing plugin: gstreamer|0.10|totem|audio/x-avi-unknown decoder|decoder-audio/x-avi-unknown, codec_id=(int)28781 (audio/x-avi-unknown decoder)
no application found
** Message: No installation candidate for missing plugins found.
```
VLC gave this:
[[IMG]http://img100.imageshack.us/img100/7559/vlckg1.jpg[/IMG]](http://imageshack.us)
GSPOT:
[[IMG]http://img90.imageshack.us/img90/2516/gspot1sc6.jpg[/IMG]](http://imageshack.us)

---

### Post by xc3RnbFO8P on 2008-03-16
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
> sudo apt-get install w32codecs

Here is some video editing apps: [http://www.getdeb.net/category.php?id=12]("http://www.getdeb.net/category.php?id=12")

I record digital TV and Avidemux don't work because of skipped frames 
so I have to use Devede to correct this  and then I use Avidemux to cut and for final size.
There also LiVES witch I have not tried out yet. 
Hope it helps.

---

