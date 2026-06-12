---
title: "Unable to burn working DVD from ripped DVD"
date: 2009-01-31
forum: Multimedia Software
---

### Post by sofasurfer on 2009-01-31
I copied a DVD to my hard drive in the forms of an ISO and video files (audio_ts and video_ts) by using DVD Shrink under Wine.

When I burn them to DVD using Brassero, the result is that:

1) the ISO plays the menu and then shows "unable to connect stream:ok".
2) the video file palys nothing.
3) if I just click on the vts_01_0.VDB it plays the menu and then shows "cannot connect strean:ok". vts_02_1.VDB plays movie but does not give me a menu.

I think the files are saved ok but I must be doing something wrong in burning and playing files. 

Is there a particular video_ts file to click on to play from the hard drive?

Why are my DVDs not functioning properly?

---

### Post by inobe on 2009-01-31
looks like you have over 400+ posts, i will assume that you know about restricted extra's ?

looks like a codec problem

---

### Post by sofasurfer on 2009-01-31
Lots of posts does not mean I am smart ;)

I know very little about codecs, but I think that they make me able to play stuff thats coded for differant countries.

Are you saying I need codecs to burn the dvds properly? Or do I need them to view them? I am able to view the original dvds so I think this means I have the proper codecs. I have tried all the installed players...
Gnome Mplayer, Totem Mplayer, Movie player.

---

### Post by sofasurfer on 2009-01-31
bump?

---

### Post by mc4man on 2009-01-31
Well if your already using wine why don't you install ImgBurn and once you get the idea how to use you'll never worry about getting proper burns again. (of any type, for use on any Os or standalone, ect. ect.

The main thing to do after installing is open it (when installing have it make a desktop icon, decline the quicklaunch.) and go tools -> settings -> I/O and set the interface to the first choice - ASPI-WNASPI32.DLL.
That will take drive detection out of wine's control and into ImgBurn's.

I also like to change the start up mode from 'easy picker' to 'last used' (easy picker can be confusing

The set build mode is for a VIDEO_TS folder, If you set to 'image' it will build an iso, then you'd switch to 'write' mode and burn it.
'Device' means it will burn directly 'on the fly' from the VIDEO_TS (no iso is created. (I prefer to build an .iso then burn.


For your dvd shrink .iso just put ImgBurn in 'write' mode, locate the file and click the burn icon. I'd set the burn speed to 1/2 of the blank media's max speed. (look in the info box


[http://www.imgburn.com/](http://www.imgburn.com/)

guides
[http://forum.imgburn.com/index.php?showforum=4](http://forum.imgburn.com/index.php?showforum=4)

---

### Post by sofasurfer on 2009-01-31
Thanks mc4man. I'll give it a try.

---

### Post by sofasurfer on 2009-01-31
Well, I was able to create a dvd from an ISO which plays in my regular DVD player. But in my PC DVD burner it gave a message that said something like "this disk contains software that must be run. Do you want to run it"? I think I clicked 'no' but I am not sure. Anyway, the menu comes up and is non-functional. I tried to get it to should the 'software' message again but I have not been able to reproduce it. This message does not come up on the original dvd. I think this was on Gnome Mplayer or Movie Player.

I then ran it on Totem Mplayer and it played one chapter (never showing a menu) that was about 2 minutes long and that was all it would do. When I open totem mplayer and try to get it to open "titles" or "menues" it shows no titles or menues available to open

---

### Post by somking95 on 2009-02-16
This seems to be a common question. I have backed up a DVD with DVD Shrink running in Wine. I now have the video_ts and audio_ts files to work with. Normally, this is where Nero would come in but I am looking for an application native to Gnome to burn the files into a workable DVD.

Is there a Gnome application that can do this?

---

### Post by mc4man on 2009-02-17
Even though I use Imgburn I'd think brasero could work ok (maybe get an updated version from getdeb.

K3b would also work ok, just don't burn as data dvd, click on "further actions.." and choose "New Video DVD Project" (to take a VIDEO_TS and make an iso and then burn

What kind of job either do as far as burning an .iso is a coinflip (I've actually had no problems with either, just don't like them

edit: trying brasero again to refresh memory  (worst app I've ever seen for DVD Video iso creation 
On hardy it's no good for creating an .iso from a VIDEO_TS, it uses the wrong filesystem ext.'s,(ISO9660, JOLIET),  might burn a properly done .iso ok.
On intrepid (with repo ver.) not sure. (don't want to waste the time, why it wants to create a checksum *before* creating .iso is beyond me 

If you use it to create an .iso I'd suggest getting the latest version, then opening the .iso in a player first before burning.
If you have disc navigation, then it should be ok , if not then the .iso is worthless

K3b (while not gnome native),at least shows some degree of design effort.

---

