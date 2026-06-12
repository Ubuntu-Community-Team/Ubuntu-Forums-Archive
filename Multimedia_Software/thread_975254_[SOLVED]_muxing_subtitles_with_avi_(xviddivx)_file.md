---
title: "[SOLVED] muxing subtitles with avi (xvid/divx) files"
date: 2008-11-08
forum: Multimedia Software
---

### Post by girishven on 2008-11-08
There is this process of muxing subtitles within AVI files. This is a process where you dont play around ( re-encode)  with the video or the audio within the container, but simply embed the .SRT file within the AVI container. This method helps some of the media streaming devices like Playstation 3 render the subtitles while using tools like mediatomb [http://mediatomb.cc/](http://mediatomb.cc/).

In the Windows world there is a tool called AVISUB
[http://www.trustfm.net/divx/SoftwareAviSub.php](http://www.trustfm.net/divx/SoftwareAviSub.php)
that does this. It allows you select the AVI file ( XVID/DIVX) and then select the corresponding SRT file. Allows you to select a font of your choice and then the positioning of the subtitles.

My questions is , is there a similar tool for Ubuntu ?.

I can very well do this within Windows, but would prefer to get it done using Ubuntu.

---

### Post by ledenjes on 2008-11-08
This, I'd like to know, as well.

---

### Post by ledenjes on 2008-11-09
Hi, I've done some searching. Apparantly, MEncoder is the only suitable programma, available. However, it is a very difficult programme to use, since there are no GUI's which make it easier to bake an .srt file into an avi file.

This is what I found: [http://wiki.showmedo.com/index.php/Video_editing_Ubuntu#merge_video_with_subtitles]("http://wiki.showmedo.com/index.php/Video_editing_Ubuntu#merge_video_with_subtitles")

Follow the instructions and all should go well. By the way, make sure you have plenty of free hard disk space (about 40-50 Gb).

Regards.

---

### Post by MonGol on 2008-11-09
hey

if you don't want to render the subtitles into the video, you can use mkvmerge. just drag & drop the avi/divx and srt/sub etc. file into the mkvmerge gui and click merge (maybe you should add some information about the source (e.g. FPS, aspect ratio etc). but keep in mind: you'll get mkv containers and not avi containers. i don't know whether the ps3 is able to play this container.

greez,
marcel

---

### Post by McPoophead on 2008-11-10
I had this problem myself. Now I use the free tool[ AVIAddXSub]("http://www.calcitapp.com/AVIAddXSubs.php"). It's a windows app but works very well under wine. It takes 3 minutes or so to mux the subtitle with a movie. 


grtz.


(one of my first posts so I hope it was a helpfull one :))

---

### Post by girishven on 2008-11-10
> **ledenjes said:**
> Hi, I've done some searching. Apparantly, MEncoder is the only suitable programma, available. However, it is a very difficult programme to use, since there are no GUI's which make it easier to bake an .srt file into an avi file.

This is what I found: [http://wiki.showmedo.com/index.php/Video_editing_Ubuntu#merge_video_with_subtitles]("http://wiki.showmedo.com/index.php/Video_editing_Ubuntu#merge_video_with_subtitles")

Follow the instructions and all should go well. By the way, make sure you have plenty of free hard disk space (about 40-50 Gb).

Regards.

Thanks for your response.

I tried to spend some time with mencoder today. The command that one would use to introduce subtitles would be

mencoder -vf pp=de,scale=696:284 -oac copy -ovc lavc -lavcopts keyint=25:vcodec=mpeg4:vbitrate=904:vpass=1 -sub "Movie.srt" -o "Movie_with_subs.avi" "Movie.avi"

In the above command

oac indicates what we want to do with the audio - we either keep it as it is in the source - in which case "copy" must be used. we could  use some of the mencoder supported codes if audio recompression is required. 

ovc is where the video compression method is specified. in this case mpeg4 ( xvid compatible ) has been specified. ( you could use "copy" if the source frames are to be retained as it is - a direct stream copy )

The interesting point here is that if mencoder ought to be used, the subtitles can not be merged without hardcoding them within the video. In other words the video must be re-encoded. There doesn't seem to be ( atleast obvious to me )  a way to just add(mux) the subtitle within the AVI container as in the case if AVISUB.

The hardcoding of subtitles ( not muxing ) within the video can also be achieved by using a tool ( not CLI but GUI based ) call Avidemux. This turns out to be a much easier way to achieve this.

---

### Post by girishven on 2008-11-10
> **McPoophead said:**
> I had this problem myself. Now I use the free tool[ AVIAddXSub]("http://www.calcitapp.com/AVIAddXSubs.php"). It's a windows app but works very well under wine. It takes 3 minutes or so to mux the subtitle with a movie. 


grtz.


(one of my first posts so I hope it was a helpfull one :))

You did GREAT on your first ever post !.

Your solution works great. Have not enough words to thank you.

It would have been great if there had been a native linux app to do this ( without the need to resort to using Wine ). Nevertheless, the program does the job and this is exactly what was needed.

i can now get my avis muxed and have them streamed from MediaTomb to my PS3! :-)

thanks once again. I guess this thread should me marked as SOLVED. How do we do that ?

---

### Post by clancymf on 2008-11-10
> **girishven said:**
> 

thanks once again. I guess this thread should me marked as SOLVED. How do we do that ?



Its above in the thread tools

---

### Post by girishven on 2008-11-10
> **clancymf said:**
> Its above in the thread tools

Marked as SOLVED.

---

### Post by jlezama on 2009-02-24
I wouldn't say that AviAddXsubs works perfectly with wine. It gives scrambled subtitles that are impossible to read sometimes.

Anyone found any solution to this?

---

### Post by Donalb on 2009-03-26
The problem I have with AviAddXsubs is that I can't select the source files using the browse button within AviAddXsubs. I've tried copying them into the AviAddXsubs direcctory and tying the name in but no luck.
Any ideas?

---

### Post by jastonas on 2011-10-18
also interested in this problem...

maybe contact the developer of aviaddXSubs to develop it for linux?

:0

---

