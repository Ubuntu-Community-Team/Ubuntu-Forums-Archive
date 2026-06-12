---
title: "Video Thumbnails"
date: 2010-10-17
forum: Multimedia Software
---

### Post by ntesla123 on 2010-10-17
I need a way to create wmv video thumbnails with file information (name, size, resolution, duration) using Ubuntu.

---

### Post by Kanedagr on 2010-10-19
The same problem here. I want to be able to create thumbnails from video sources, especially avi files. 
Until now i have to boot to Windows 7, i am trying to find a program that does that but unfortunately nothing comes up. Any help?

---

### Post by ntesla123 on 2010-10-22
I've started using smplayer, to create screenshots. You just go to video -> preview and choose f ex. 4 x 4 and maximum width 1000

---

### Post by Kanedagr on 2010-10-22
It doesn't work on my machine Kubuntu 10.10 and mplayer version 2:1.0~rc4. It says that the mplayer process did't run. Any suggestions?

---

### Post by ntesla123 on 2010-10-26
SlickSlice will do the job. You can for example use the command 

slickslice -x myfile.wmv -S 4x4 -w 400

for a 4x4 image sheet with width 1216.

I've tried this script and it works.
[http://slickslice.sourceforge.net/](http://slickslice.sourceforge.net/)
[http://sourceforge.net/projects/slickslice/](http://sourceforge.net/projects/slickslice/)
[http://www.uluga.ubuntuforums.org/showthread.php?t=251237](http://www.uluga.ubuntuforums.org/showthread.php?t=251237)

There is also a Perl script called Dhyana that is supposed to do the same thing. I tried it, but it only created two thumbs though. But I'm sure it's possible to fix it, so maybe you can make it work.

[http://tobyinkster.co.uk/blog/2007/08/19/dhyana/](http://tobyinkster.co.uk/blog/2007/08/19/dhyana/)

---

### Post by ntesla123 on 2010-10-26
Another perl script

[http://minhtech.com/linux/fedora-linux-create-video-thumbnail-montage-perl-](http://minhtech.com/linux/fedora-linux-create-video-thumbnail-montage-perl-)
script/

---

### Post by ntesla123 on 2010-10-26
I actually wrote this Slickslice script to create 4x4 thumbnails for all the files in the working directory. Image width 1216. I personally have hundreds of video files I'm going to upload to different forums. Then I don't even have to open the files. I can just run the script.

for i in `ls`
do
slickslice -x $i -S 4x4 -e -w 400
done

Then you add filters and fonts and so on in the third line of the script.

You just make it executable and then run it by ./scriptname

I'm actually not using smplayer anymore. I think this is a lot better.

---

