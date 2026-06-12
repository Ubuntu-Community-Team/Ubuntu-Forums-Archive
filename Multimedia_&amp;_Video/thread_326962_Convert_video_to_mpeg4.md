---
title: "Convert video to mpeg4"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by c-m on 2006-12-28
Did i quick search but couldn't find anything.

I have various video files in divx, xvid format etc.. and I need ot convert these to Mpeg4 (as thats what my phone supports) how would i go about doing this in Linux?

---

### Post by dannyboy79 on 2006-12-28
if you don't mind me asking, what type of phone do you have? i use tcpmp on my treo 700P and it can play just about anything! also, i am pretty sure divx and xvid are already a form of mpeg4. mpeg2 are what dvd's are made from. so if you tell what kind of phone you have maybe I can suggest a suitable player.

---

### Post by c-m on 2006-12-28
I have a Samsung D900.

It plays mpeg 4 video files, so i'm looking to convert some files stored on my computer and transfer them to the phone.

---

### Post by dannyboy79 on 2006-12-28
yeah, I beleive you are confussed here. your phone can play mp4 files. I figured that's what you meant to tell me, you want to be able to convert them to a mp4 container not mpeg-4, they are already in mpeg-4 format. So what are the files you have now in (container wise?) they're probably in .avi or maybe .divx. install ffmpeg, mencoder, mplayer and then try this:
ffmpeg -i Video.avi -f psp -r 29.970030 -b 768 -ar 24000 -ab 64 -s 320x240 M4V00001.MP4

where video.avi is your input filename and 
M4V00001.MP4 is your output name. also as you can see, this will be a 320x240 so if your screen is a little smaller try something smaller. a great program for this in winbloz is dvd fab platinum. is has preset values for psp, ipod, and then even a generic one for chosing your own container, resolution, sound settings and tons of other stuff but I don't know of a linux app that has a gui for this yet. Oh wait, look into Devede. I think it may be able to output a .mp4! just gogle it. good luck

or maybe transcode? [http://www.transcoding.org/cgi-bin/transcode](http://www.transcoding.org/cgi-bin/transcode)

---

### Post by crane on 2007-01-01
I installed [Avidemux2]("http://fixounet.free.fr/avidemux/"). I compiled myself and included many of the optional packages listed [HERE]("http://www.avidemux.org/wki/index.php?title=Compiling_Avidemux"). Just be sure to get the required files before compiling. I used the following for my configure on my Edgy box.

```
 ./configure --with-jsapi-include=/usr/include/firefox/js/ --with newfaad

```
I had to create a custom launcher because it does not install an item in the menu.
 I use this on my .nuv files from my mythbox.
You can start the program in a terminal by typing avidemux2
Then open the file you wish to change. There is a PSP option but it appears to be currently broken. 
I the video section on the left I selected Mpeg4(lavc) in the first box, left the second box as-is andadded 2 filters in the third box.
One filter was to resize the video to 320x240. This takes a little messing around with aspect ratios(at least it did for me) and to check the 16 round up box. Then click apply and OK.
The second filter is the resample FPS. When the window popped up it was set to 29.969999.
I just clicked apply and OK. Then close the filters screen.

In the audio section I selected FAAC. You can change the bit-rate by clicking the config tab here and changing.
 I did nothing to the filters box.
 Now in the format box below that I selected  MP4 (not PSP - I tried this with horrible results).
Next click save and save the file as XXXX.mp4.
 When it's done you should have a video that will play on the PSP.
It will not be full screen but that can be changed with the aspect ration on the PSP. 

This is not a ment to be a how because I have a limited knowledge of compiling and even mor limited knowledge of converting videos. I am having a heck of a time getting a DVD ripped to the PC in a decent format to change to PSP.

 If anyone messes around with the settings and comes up with some improvements please share them so we all my benefit!

Peace,
 Crane

---

### Post by sarracenia88 on 2007-01-01
you can redo the resolutions when you rip the dvd to your computer in dvd:rip

---

