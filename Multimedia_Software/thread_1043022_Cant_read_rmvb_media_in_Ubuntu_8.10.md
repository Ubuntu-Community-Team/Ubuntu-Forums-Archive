---
title: "Cant read rmvb media in Ubuntu 8.10"
date: 2009-01-18
forum: Multimedia Software
---

### Post by vincent chin on 2009-01-18
[COLOR="Blue"]I am the beginner of Ubuntu just having a problem of reading rmvb media with Mplayer.I have followed the steps below to configure the neccessary codecs.However, the player still display error messenge **"Cannot find codec matching selected -vo and video format 0x30345652"**.


```

tar -jxvf essential-20071007.tar.bz2
cd Desktop
cd essential-20071007
sudo mkdir /usr/lib/codecs
sudo cp * /usr/lib/codecs


```

Change setting in Mplayer, Preferences->Video to x11,Video codecs family to RealVideo decoder, Audio codec family to FFmpeg/libavcodec audio decoder

Could anyone help me to solve it?
Thank you.[/COLOR]

---

### Post by x33a on 2009-01-18
Try vlc media player. it works pretty good with real media files.

latest version is 0.9.8a. you can get it here

[http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/)

---

### Post by vincent chin on 2009-01-18
Thank you.It work pretty well.

---

### Post by fruit003 on 2009-12-23
Installation was a breeze and you folks are smart, so I’ll just skip talking about that part. There are a few issues here and there depending on your hardware and software setup and for that a bit of poking around the Boxee forum should help out. 
 After installation, I just added a few folders as media sources (supports Samba network and UPnP shares too) and Boxee had no trouble listing my content, even downloading album/media artwork when it automatically recognized some of it. I’m not certain if Boxee looks at metadata/ID3 tags only or if it also tries to infer titles based on filenames, but it only recognized a few TV shows and movies out of a terabyte of my media. That’s not a big deal though, playback is fine, you just can’t tap into Boxee’s special sauce – sharing things like recent plays with friends, rating media and viewing media information such as movie summaries. 
 In addition to Boxee helping your friends make media recommendations for you, many users flock to Boxee for it’s native support for many online video streaming services (unfortunately Hulu was recently pulled). However, **that’s not why I’m using Boxee**. I’m using it to painlessly manage the stockpile of media I already have on my HTPC. That being said, this post comes from my usage of Boxee and as such I won’t be mentioning much of Boxee’s Internet video streaming, built-in BitTorrent client, Python plugin system and [other such features]("http://en.wikipedia.org/wiki/Boxee"). 

==========
[gmc envoy wheel bearing](http://www.carpartswarehouse.com/gmc-envoy-wheel-bearing.html)
[importing car to canada](http://www.vehicleexporting.com/)

---

