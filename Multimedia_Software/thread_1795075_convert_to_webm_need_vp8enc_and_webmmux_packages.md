---
title: "convert to webm??? need: vp8enc and webmmux packages??"
date: 2011-07-02
forum: Multimedia Software
---

### Post by jonny.milano on 2011-07-02
Hi,

I am trying to convert some videos to webm for use with HTML5. I need to use the webm codec. After a little searching around, I found that Arista is a good program for this. I installed it from the repositories. I try to use it to convert to webm and get a promt to install more software: 

GStreamer element webmmux

and

GStreamer element vp8enc

I can't find the packages anywhere for Ubuntu 10.04. Can someone please please help me out??? I like to avoid ffmpeg and the command line but if someone pointed me to a reliable tutorial, I'd be ok with using it to convert these videos. 

Thanks in advance!

---

### Post by andrew.46 on 2011-07-02
> **jonny.milano said:**
>  I like to avoid ffmpeg and the command line but if someone pointed me to a reliable tutorial, I'd be ok with using it to convert these videos. 

I have been using FFmpeg to create pretty good quality webm files and there is a great guide on these Forums that will help you do this:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

The main focus of this guide is x264 encoding but if you follow the optional libvpx section you should be right to go. Good news to is that there are now some presets available for encoding to webm :).

---

### Post by jonny.milano on 2011-07-02
WOW! Fast replies on the UbuntuForums!! Kudos! Thanks very much for the reply! :) That guide does look good but furthur googling has lead me to this: [http://www.youtube.com/watch?v=0pQCBng1vJs](http://www.youtube.com/watch?v=0pQCBng1vJs) Basically, one can simply add this: ppa:gstreamer-developers/ppa via PPA! :) and then all of the scripted programs that I was trying to use via the GUI, work! (including Arista) :) 

Very happy now. Again, thank you for you help. I hope others find this useful.

---

