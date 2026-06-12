---
title: "utility to combine .vob files?"
date: 2009-03-09
forum: Multimedia Software
---

### Post by n3gative12 on 2009-03-09
I am trying to store my dvds on my hard drive, and I have ended up with several .vob files that make up the movie. Does anyone know of a simple program that will stitch the files together end to end without compressing them?

---

### Post by mc4man on 2009-03-09
Depending on what you had in mind for "storing" then separate .VOB's are normal. Did you rip to a VIDEO_TS folder? (with .ifo's and .bub's
.VOB's on a dvd are limited to a max. size of .99GB, that's why there are several. (Each titleset gets a different number.

---

### Post by n3gative12 on 2009-03-09
I didn't rip to a VIDEO_TS file, I just have several 1 gig .vobs from the dvd. They all play separately, but I want to combine them into one so I can watch it all at once in vlc (I'm not planning on burning them to a dvd, just keeping/watching them on my computer).

---

### Post by mc4man on 2009-03-09
Actually i never rip that way, prefer either dump to .iso or rip to video_ts and then reauthor

Any way you could cd to the folder holding the .vobs you want to join ( only those ones

Then in the terminal
```
cat *.VOB > whatever.VOB
```
or 
```
cat *.vob > whatever.vob
```

You could also change the extension to .mpeg when done

Many rippers will allow you to rip to a single .vob

---

### Post by n3gative12 on 2009-03-09
When I try that, the video won't play in vlc and in the default player the progress bar is all messed up (the bar fills up too early, etc.) Any idea on why this is/ how to fix it?

---

### Post by shirilover on 2009-03-10
Have you tried using 'Open Folder' instead of 'Open File'?

---

### Post by EZEN on 2009-03-10
I've had great luck with these options.

[LIST=1]
[*]Play the .vob files in order in movie player - a slight "bump" occurs when changing files but I don't mind.
[*]Also you can run them through DeVeDe. Make sure "delete"temp files in advanced options is NOT checked. The program will keep the resulting mpeg file for you to enjoy  ;)
[/LIST]

---

### Post by EZEN on 2009-03-12
> **EZEN said:**
> I've had great luck with these options.

[LIST=1]
[*]Play the .vob files in order in movie player - a slight "bump" occurs when changing files but I don't mind.
[*]Also you can run them through DeVeDe. Make sure "delete"temp files in advanced options is NOT checked. The program will keep the resulting mpeg file for you to enjoy  ;)
[/LIST]

Hold off on option 2.
It's possible that I confused programs...there are so many :(
I'll find out for sure.

---

### Post by EZEN on 2009-03-12
Sorry I messed up the previous replies.
I literally had to go through my notes.

[B]TO STITCH TOGETHER .VOB FILES:
Use Avidemux.[/B]

Drag the first .vob into the project area.
Say yes to index and "append" the other .vobs
In the AUTO menu select DVD.
Leave the default at 1:1
Select SAVE from file menu.
Take a short nap.
Voila....done :) You have a high quality .mpeg

---

### Post by prabath_fun on 2010-09-20
Hi Ezen,
  I end up with audio sync problem in Avidemux.... 

And Hi all,
  Whether cat 1.vob 2.vob > result.vob 
  will just joins the vob files without changing any details like audio track, sample, bit rate, video bit rate, resolution etc.,

---

### Post by hsoulen on 2010-09-20
Hi there!

I think it might be best to understand the concept of "ripping" a DVD to start with, I am not trying to be a jerk but working with just the "vob" files is a bit of a pain in the butt as opposed to working with the entire DVD structure.

If you still have the DVD then my advice is download and install handbrake and use this program to rip/transcode your video to either mp4 or mkv.

If you don't have the DVD (I won't ask why I promise :) ) then just using "cat" to combine vob files can simply create a big mess and can lead to audio sync issues, timecode issues etc. (I think you already discovered this).

So at this point I think you are best using ffmpeg or Avidemux, I know the command line can seem a bit daunting at first but if you dig around in these forums you are sure to find some help. Alternatively I think VLC may have an option for this as well (combining video during transcode).

Hope this helps.

Hank

---

### Post by larytet on 2010-10-30
If you want to play the video just use "Open folder" option in the VideoLan (vlc) or right click the folder where the VOB files are and choose "Open with VLC". 

VLC plays DVD rips nicely and supports menus.
MPLayer should do the trick too.

---

### Post by sembagdod on 2012-04-05
Hi, i faced the same issue and it was very easy to solve it through 
tsMuxer 
Download it from [http://linux.softpedia.com/get/Multimedia/Video/tsMuxeR-44716.shtml](http://linux.softpedia.com/get/Multimedia/Video/tsMuxeR-44716.shtml)

then right click and extract, and run the file named "tsMuxerGUI" 
Then you know what to do , so easy. 

Regards

---

### Post by VRathor on 2013-03-12
Hello,
I started with the task to combine movies spanning over multiple .VOB files into one MPEG file.
I'm trying my luck with Avidemux... will update here with results.

---

### Post by wildmanne39 on 2013-03-14
Old thread closed!

---

