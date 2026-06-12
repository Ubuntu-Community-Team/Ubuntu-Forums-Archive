---
title: "Converting AVI files to MPEG2 to make a DVD"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by zachthejones on 2007-12-19
Here's the deal. I have two hour long AVI files I edited in Windows on Adobe Premiere, and about five short AVI files edited in Windows Movie Maker.  I need to create  DVD, but when I try and do it through QDVDAuthor, it says its gonna take like 4-5 hours to encode. When I tried to use ManDVD, it was having some codec problems. and DeVeDe was also going to take forever.

I wondered if there was a program I could use to convert these AVI files to MPEG or whatever is easily compatible with any of these DVD creation programs, and then the creating of the DVD wouldn't take so long.

My goal is to get these videos on a DVD (hopefully with a menu) without a 5-hour encoding process.

Any suggestions?

---

### Post by Beaucephus on 2007-12-19
I have had really good luck with **avidemux**.  It can handle any conversion I have thrown at it so far.  The interface is slightly clunky and you have to do your homework about setting framerates, bitrates and such.  I believe it is still the best converter out there.  It's in the standard repositories.

---

### Post by zachthejones on 2007-12-19
Yeah, I had snagged Avidemux to play around editing video in. Thanks for the suggestion - it seems to be encoding the videos as mpegs pretty quickly. will this shorten my DVD creation time?

Oh, and is there any specific video editing program you would suggest (in Linux)? I'm used to Adobe Premiere, but I have an older version and am sick and tired of having to use Windows for anything.  I would like to use an editor which can export my editing timeline in a file that's compatible with DVD authoring programs like QDVDAuthor and manDVD.

---

### Post by Beaucephus on 2007-12-28
Answers
Anything that shortens mpeg transcoding time reduces the time it takes to make DVDs.  Thats a required step

As for editing software, I have not found much.  I do simple stuff so if I need to cut down scenes I just do it in avidemux using the cut tool.  I use a program called **dvdstyler** to actually create the menus and stuff. 

There is no single tool in linux for DVD creation like Adobe Premiere for windows.  Every step in the process that happens behind the scenes in Premiere is a manual step in Linux that requires a different program.  All you need for QDVDAuthor is a MPEG file with the correct sound encoding.   There is no real "timeline" involved after that point.

---

### Post by disturbedite on 2007-12-28
i always use avidemux to transcode/convert video to dvd compatible format & then use qdvdauthor to make the dvd file structure & then k3b to burn.

converting movies & long stuff takes a long time, generally speaking, unless you want crappy quality.  then you can use crappy quality settings & it should encode quicker.  or upgrade your hardware.  :D

---

### Post by konungursvia on 2007-12-30
As for the audio / video sync problem, I am not totally sure, but I solved that at one point by choosing an option for allowing frame dropping during playback to allow an older video card to keep up with the real time audio. It may be a playback issue, rather than a muxing problem.

---

### Post by aonegodman on 2008-01-03
Here's a link for an excellent tutorial on using avidemux to convert avi to mpeg DVD:


[http://avidemux.org/admForum/viewtopic.php?id=3469](http://avidemux.org/admForum/viewtopic.php?id=3469)


Must have Flash Player installed to view.    :popcorn:

---

### Post by zachthejones on 2008-01-03
Thanks so much for the help guys! Using some of the different tutorials ya'll recommended I encoded the AVI files for DVD through Avidemux (I'm starting to think that's one pretty powerful little program). I think after as I start to get the hang of it, I actually like being able to control so many different parameters on the encoding.

After doing that, I just added the videos as-is in QDVDauthor and created my menus and DVD - everything seems to be working pretty well. It definitely creates the DVD files much more quickly.

Then I just use K3B to burn the files to the DVD (as a data disc), and it seems to work fine in my DVD player!

Thanks again for the help!

---

### Post by buntu_hugenewbie11 on 2008-02-19
Does anybody know of a good tutorial for Qdvd author? Also how do you make sure you have the mpeg converted to NTSC?
Ideas??

---

