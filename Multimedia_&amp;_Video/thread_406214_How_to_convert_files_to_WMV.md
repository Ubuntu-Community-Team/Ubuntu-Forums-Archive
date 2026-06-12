---
title: "How to convert files to WMV"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by Error47 on 2007-04-10
I need to convert movies to wmv so they can play on my xbox 360. If there is another way to stream videos other then vmware, how can I do it. 

Thanks.

---

### Post by Error47 on 2007-04-11
Any programs for that?

---

### Post by Shampyon on 2007-04-11
I have no idea if this will work. I know nothing about video converting beyond the fact that I wish there was a Linux version of Super. I got the command line code from [this thread]("http://ubuntuforums.org/showpost.php?p=2047554&postcount=6").

> ffmpeg -i movie.flv -vcodec wmv1 -acodec adpcm_ima_wav movie.wmv

Where *movie.flv* is the name and file extensionof the video you wish to convert, and *movie.wmv* is what you want the finished product to be called. This assumes you have the video in your Home directory.

It looks like that'll give you output in an [X-Box 360 supported codec]("http://blogs.msdn.com/xboxteam/archive/2006/10/31/fall-06-supported-video-formats.aspx").

Hope it works!

edit: This also assumed you've installed the Win32 codecs. If you haven't, the easiest way I know of is [Automatix.]("http://www.getautomatix.com/") I can't recall if that also installs ffmpeg. To test it, open up a terminal window and type in *sudo apt-get ffmpeg*, or open up Synaptic and search for *ffmpeg*.

---

### Post by Error47 on 2007-04-15
Will that convert ANY video? .avi?

I tried converting a .mpg , I thought it worked for a sec, then I put it on my USB drive, along with 2 other .wmv files. The other two files worked, the one I converted didn't work. Any software for this?

---

### Post by Error47 on 2007-04-21
It didn't work, Please Help!

---

### Post by ticopelp on 2007-05-04
I just converted an .avi file to .wmv using this method and it worked without incident. Thanks for the tip.

---

