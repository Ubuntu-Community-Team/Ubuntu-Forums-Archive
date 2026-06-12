---
title: "I need help with burning a dvd from an .avi"
date: 2009-06-09
forum: Multimedia Software
---

### Post by jcm1107 on 2009-06-09
Hi I need help with burning dvd from a .avi I used acid rip to backup the dvd to my drive now I want to burn it to a blank dvd that will play in an old home dvd player (not just my computer). I have tried Devede and it seemed to convert it, but when I burned to disk the disk wold not play in my home player. Mabe I need to change settings in Devede? or mabe I need to burn the image created with devede with a differnent burner? I have tried the option to make iso and then I tried create disk structure after that didn't work. I didn't change any other settings though. I am up for any ideas or suggestions like a different program, but I have read on here that a lot of people recomend devede. I haven't seen much about if you should use a certain program to burn with though.

---

### Post by binbash on 2009-06-09
I convert with Devede and burn the image with nero linux or any other image burning softwares.I tested over 100 video files  on 6 different players, devede works great.You should check your Devede version + burn the image with another software (max 4x speed! ) and re-check your settings especially PAL/NTSC

---

### Post by jcm1107 on 2009-06-09
> **binbash said:**
> I convert with Devede and burn the image with nero linux or any other image burning softwares.I tested over 100 video files  on 6 different players, devede works great.You should check your Devede version + burn the image with another software (max 4x speed! ) and re-check your settings especially PAL/NTSC

should I set devede to use pal/ntsc? What version of Devede should I use? Can I use brasero to burn the dvd? If so should I use the make data dvd or make video dvd? the video dvd will not let me put my movie in the area to burn (says movie does not have valid type for video projects) I would like if someone could walk me through burning a playable dvd step by step because its just not working for me. THANKS!

---

### Post by hurtstotalktoyou on 2009-06-09
> **jcm1107 said:**
> should I set devede to use pal/ntsc? I would like if someone could walk me through burning a playable dvd step by step because its just not working for me. THANKS!

1.  In Devede, you get an initial window asking you what kind of disc to make.  Choose "Video DVD".
2.  In the main window, choose "NTSC".
3.  Click "+ Add" under the "Files" window to add a video to your first title.
4.  In the new file window, choose your video file and select "NTSC".  Leave the advanced options alone.  Click "OK" when done.
5.  After you're done adding video files, click "Adjust disc usage" in the main window.
6.  That should do it.  Click "Forward" and choose a save location to have Devede create your *.iso file.  Then use K3B or some other disc burning application to burn it.

---

### Post by jcm1107 on 2009-06-10
> **hurtstotalktoyou said:**
> 1.  In Devede, you get an initial window asking you what kind of disc to make.  Choose "Video DVD".
2.  In the main window, choose "NTSC".
3.  Click "+ Add" under the "Files" window to add a video to your first title.
4.  In the new file window, choose your video file and select "NTSC".  Leave the advanced options alone.  Click "OK" when done.
5.  After you're done adding video files, click "Adjust disc usage" in the main window.
6.  That should do it.  Click "Forward" and choose a save location to have Devede create your *.iso file.  Then use K3B or some other disc burning application to burn it.

thanks I am trying this now. Just one thing, the movie I want to convert said 103% on the disk usage will that fit on a disk? and when I burn do I burn as a movie dvd, an iso, or a data dvd after using devede. Also should I use the create iso or BIN/CUE image or should I use convert to MPEG, or should I use Creat disk struckture option?

---

### Post by jcm1107 on 2009-06-10
this worked (sort of, the sound is about a min. behind the movie. So try playing it on your computer before you burn it!)

cd Desktop/Videos

 tovid -in NAMEOFMOVIE.AVI -out movie

do you want to keep temp files that were created ? n

makexml movie.mpg -out movie


 makedvd -burn movie.xml


This used tovid to convert an avi movie to a dvd that played. Tovid was awsome and simple!!  I found this very simple, just cd to your movie location and then use the comands I listed. But I still want to figure out devede it seems so simple to use I know I would love it if I can get a dvd to burn from it.

---

### Post by jcm1107 on 2009-06-10
1

---

### Post by jcm1107 on 2009-06-12
> **hurtstotalktoyou said:**
> 1.  In Devede, you get an initial window asking you what kind of disc to make.  Choose "Video DVD".
2.  In the main window, choose "NTSC".
3.  Click "+ Add" under the "Files" window to add a video to your first title.
4.  In the new file window, choose your video file and select "NTSC".  Leave the advanced options alone.  Click "OK" when done.
5.  After you're done adding video files, click "Adjust disc usage" in the main window.
6.  That should do it.  Click "Forward" and choose a save location to have Devede create your *.iso file.  Then use K3B or some other disc burning application to burn it.

SOLVED!!! THIS WORKED!!!! THANKS!! I was using pal instead of NTSC I don't know what those mean, probably diferent regions or formats but changing that worked, I then burned to blank DVD-R and it played in an OLD dvd player that dosn't play divx or any special format only dvd's

---

### Post by Browser_ice on 2009-06-17
I followed your instructions and doing it now. As far as I can tell, it is creating an *.mpg file. 

I thought it would directly create an ISO file ?

---

