---
title: "Convert OGG video to anything else"
date: 2007-06-25
forum: Multimedia Production
---

### Post by LIJI on 2007-06-25
Hey,
I used a desktop recording program to make a demonstration video of Ubuntu, Gnome and Beryl in Hebrew.
The video file was saved as an OGG video.
The video file is 17 minutes long and of course needs shortening and editing.
The problem is - Kino doesn't support OGG video and PiTiVi hardly work.
Any attempt to find a converter by Google resulted in useless audio converters.
Is there any easy to use program that can convert OGG to something else?

Thanking in advance,
LIJI

---

### Post by rattking on 2007-06-25
Hi
have you tried ffmpeg from the command line?
ffmpeg -i file.ogg file.avi
should basically work.. but there are many options available.. then you can input that to kino
you will probably need ffmpeg libtheora0 installed
good luck

---

### Post by LIJI on 2007-06-25
> **rattking said:**
> Hi
have you tried ffmpeg from the command line?
ffmpeg -i file.ogg file.avi
should basically work.. but there are many options available.. then you can input that to kino
you will probably need ffmpeg libtheora0 installed
good luck

Thanks for your answer.
I tried mencoder and it worked fine. :)
Thanks anyway.

---

### Post by reckless2k2 on 2007-06-29
How did you use mencoder to convert ogg to avi? I tried using the suggested ffmpeg command but the avi output would produce errors in every player i used and was unable to make it work. how were you able to achieve this with mencoder? or how can i use ffmpeg to make a playable avi file. 

i'm using istanbul to make training tutorials that output in ogg only. i'm trying to convert to avi. thanks.

---

### Post by LIJI on 2007-06-29
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)
Follow this guide, that what I used.

---

### Post by reckless2k2 on 2007-06-29
I've got an ogg file created in istanbul. i used the following command to convert it to avi:

mencoder file.ogg -o file.avi -ovc lavc -oac lavc

it created an avi file but i'm getting the same error trying to open it with anything. i'm trying to convert it to a file to be viewed in windows media player for office workers. i'm creating instructional tutorials. i don't have the option to install the ogg codec on each co-workers machine to view it in the original format. 

so i tried converting it with ffmpeg and mencoder to an avi but it doesn't seem to be working. i'm not sure what the issue is.

---

### Post by luisbg on 2007-06-29
I just wish there was a user interface for ffmpeg like mac os x has ffmpegX.

luis

---

### Post by fluoblack on 2007-07-01
For the lazy ones: there is a transcoding wizard in VLC media player, you can convert audio, video or both in most of the formats you need.
Et voila :)

---

### Post by weblordpepe on 2007-07-01
Hey guys I made a different post about this but  I think I solved my own problem.
Go apt-get install ffmpeg
and then apt-get install iriverter
its a GUI front end to ffmpeg

---

### Post by GMU_DodgyHodgy on 2007-07-03
Can we get some screenshots of the front-end GUI.  This would actually be a very helpful tool.

---

### Post by weblordpepe on 2007-07-04
Your wish is my command
[IMG]http://homepages.slingshot.co.nz/~davoman6/iriverter.png[/IMG]

---

### Post by mahiyar on 2007-10-28
If I am not mistaken is the front end for mencoder.

---

### Post by Creative2 on 2007-10-29
see here... multimedia converter make many many many things 

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by SupraBlur on 2007-11-30
> **weblordpepe said:**
> Hey guys I made a different post about this but  I think I solved my own problem.
Go apt-get install ffmpeg
and then apt-get install iriverter
its a GUI front end to ffmpeg

I know this is resurrecting an old thread, but I was actually never able to ge iriverter to run.  I dowloaded it as well as ffmpeg and mencoder, but when I click on iriverter, nothing happens.

-Ray

---

