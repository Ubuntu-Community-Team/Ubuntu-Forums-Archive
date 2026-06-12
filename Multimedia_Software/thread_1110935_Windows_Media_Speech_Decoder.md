---
title: "Windows Media Speech Decoder ??????"
date: 2009-03-30
forum: Multimedia Software
---

### Post by jeffus_il on 2009-03-30
Video from the site bloomberg.com requires the "Windows Media Speech Decoder", any ideas?

---

### Post by henrymoritz on 2009-05-24
i had the same problem. only video no audio. then i installed mplayer from the command line.

1. Open Terminal
2. write : sudo apt-get install mplayer  
3. enter your password

That was all. Now i can see the video and her the tone in 

[http://www.bloomberg.com/?b=0&Intro=intro3](http://www.bloomberg.com/?b=0&Intro=intro3)

:p

---

### Post by vmidhun09@gmail.com on 2009-11-13
Dude .. even i was trying to solve the same prob.. 
Go to Synaptic Package manager --> and type asf ...

You ll find something like this-----------> libavformat-unstripped-52_0 install it.. you also need gnome player or mplayer.

or type this in your terminal : 

sudo wget -c [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/f/ffmpeg/libavformat-unstripped-52_0.svn20090303-1ubuntu2+unstripped1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/f/ffmpeg/libavformat-unstripped-52_0.svn20090303-1ubuntu2+unstripped1_i386.deb) 

Hope this ll help you guys.. :D

---

### Post by 88300D on 2010-07-20
Hi i have and issue i think is the same, i have done the suggestions on this page and lots of others but still no luck the url i am trying to play from is [http://unitab.com/unitab_help/radiotab/radiotab_http.asx ]("http://unitab.com/unitab_help/radiotab/radiotab_http.asx")

This is one of my three issues that are holding me back for being happy with linux

peace and blessings Howie
[]("http://unitab.com/unitab_help/radiotab/radiotab_http.asx")

---

### Post by mc4man on 2010-07-20
> i am trying to play from is [http://unitab.com/unitab_help/radiotab/radiotab_http.asx](http://unitab.com/unitab_help/radiotab/radiotab_http.asx) 

Not to hard if you have the right player(s) and or codecs.

If you are on karmic or lucid then I'd add this ppa, and update your gtreamer plugins (thru the update manager would be fine

Then you could listen in firefox (with the default totem-mozilla plugin) or in totem itself (probably also rhythmbox 

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Just about any current mplayer will work, most ppa's will be ok.
From the command line you need to adjust the url for mplayer

```
mplayer mms://streaming.tabonline.com.au/radiotab?MSWMExt=.asf
```
Sometimes totem can also benefit from expaned url also, (though not needed here) either in the player  - Movie -> open location and use 
```
mms://streaming.tabonline.com.au/radiotab?MSWMExt=.asf
```

or from terminal ```
totem mms://streaming.tabonline.com.au/radiotab?MSWMExt=.asf


```

There are other ways for other players to get wmas support..

Note that in maverick !10.10 - releases in oct. ) wmas and wmap will be supported by default for most players

---

### Post by amzium on 2010-11-13
I tried updating the gstreamer thingy and it work't perfect, Just wanted to write it cause I got so happy not needing to boot in to Windows any more to watch some of my videos.

---

