---
title: "dvdstyler problem"
date: 2008-01-13
forum: Multimedia Production
---

### Post by cotcot on 2008-01-13
I am using dvdstyler 1.6 (from the akirad-gutsy repo). 
Burning to a dvd gives a dvd that i can play normally on the pc but that is not OK on the dvd-player (Liteon)  near my TV. 
On the liteon the menu pops up for a fraction of a second and than i get the liteon intro screen again. The pop up image is of a bad quality (checkerboard like pattern) and the color of the letters of the menu items are wrong (highlighted selection color instead of normal color).
I buned it to dvd-r and dvd+-rw. Same result. I tried lower bitrates. Same result. I tried to generate only the iso and do the burning with k3b : same result.
I made dvd-s with the same footage using qdvdauthor and that was ok.
Any ideas ?

---

### Post by Creative2 on 2008-01-13
mm have you tried dvdwizard?
i have made a simple gui for that :)

---

### Post by cotcot on 2008-01-13
Where is your gui for dvdwizard ?

---

### Post by disturbed1 on 2008-01-14
> **cotcot said:**
> I am using dvdstyler 1.6 (from the akirad-gutsy repo). 
Burning to a dvd gives a dvd that i can play normally on the pc but that is not OK on the dvd-player (Liteon)  near my TV. 
On the liteon the menu pops up for a fraction of a second and than i get the liteon intro screen again. The pop up image is of a bad quality (checkerboard like pattern) and the color of the letters of the menu items are wrong (highlighted selection color instead of normal color).
I buned it to dvd-r and dvd+-rw. Same result. I tried lower bitrates. Same result. I tried to generate only the iso and do the burning with k3b : same result.
I made **dvd-s** with the same footage using qdvdauthor and that was ok.
Any ideas ?

What is DVD-S? DVD's ;)

1.6 is bugged out. It's either the akirad compile, Ubuntu's ffmpeg, or 1.6 itself. It has issues with stills, slide shows and menus. Considering 1.6 changed to using ffmpeg without calling a dependency for libavcodec and others in the install nor configure.in, this could be the issue. Previous versions used jpeg2yuv and mpeg2enc rather than ffmpeg.

I've used 1.5.1 since it came out. Never an issue with any player.


-------------------edit-----------------
There is a new DVDStyler 1.6.0.2 I'm compiling it now. Akirad's version is 1.6.0-1 which was put up yeterday. One thing I did notice, in this new version the configure does look for avcodec. So we'll see.

---

### Post by Creative2 on 2008-01-14
ok it's here 

[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

---

### Post by cotcot on 2008-01-16
Thanks creative2. I have it installed. It starts and looks nice. I have to find how to make the menu for a dvd.

---

### Post by Creative2 on 2008-01-16
go in extra and option---->create a dvd

if you want customize better menu you can go in dvdwizard website....and so modify the command line..as you want

---

### Post by Creative2 on 2008-01-19
note if you put too much file with "orgainize like title " turned on maybe it will have problem 
if you have much more 15 files use orgainize "like Chapter" in encoding option windows

---

