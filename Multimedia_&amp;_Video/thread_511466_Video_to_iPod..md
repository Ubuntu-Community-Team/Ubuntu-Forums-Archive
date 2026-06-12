---
title: "Video to iPod."
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by Edan. on 2007-07-27
I've been looking for guides or application that will simply allow me to convert
my .avi files so I can play them on my iPod.
I found those two -

[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)
[http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946)

But as a beginner in Linux I found it pretty much hard. 
Is there any simple software to convert .avi video to iPod, SIMPLY ?

Thanks in advance.

---

### Post by kostkon on 2007-07-28
Yes, I hope you will feel the following I am giving you are easy to follow. First, you need to install ffmpeg. I recommend you to install the version of ffmpeg that is offered from the [medibuntu repository]("http://medibuntu.org/"). Thus, first you have to add this repository to your software sources. [Here in the medibuntu site]("http://medibuntu.org/repository.php") you will find how you can easily add the repository.

After this, go to synaptic, search for *ffmpeg* and then select and install it. 

Then, you'll need a GUI for ffmpeg. A good one is [WinFF]("http://biggmatt.com/winff/"). WiFF has already presets for iPod video so you will be able to convert a video to a format that an iPod can play, right away. Thus, go to the [downloads section]("http://biggmatt.com/winff/downloads/") of the site, download the deb version of the program and then double click the deb file and install WinFF.

Furthermore, if you want a program to transfer the videos to the iPod from Ubuntu, you can use gtkpod-aac or [floola]("http://www.floola.com/"), the last one being a very good program! Floola is the one that I use. You can install gtkpod-aac from Synaptic and to install Floola you have to download the binary from its site.

I hope I helped you somehow :)

---

### Post by thelinux_guy on 2007-08-03
Thanks! WinFF works like a charm! :)

---

