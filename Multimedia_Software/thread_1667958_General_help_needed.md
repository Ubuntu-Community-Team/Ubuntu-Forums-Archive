---
title: "General help needed"
date: 2011-01-15
forum: Multimedia Software
---

### Post by dkolars on 2011-01-15
Been using Ubuntu for close to 2 yrs. now after 25+ using DOS/Windoze...  Still having major problems with DVD burning...  Situation is:

Have 2 video clips from my camera, converted to .avi files.  So, open DeVeDe, create .iso file with menu titles, etc.  Directory structure of finished product is /media/drive/movie/movie.iso/ISO9660/AUDIO_TS & VIDEO_TS.  AUDIO_TS is empty, as usual, VIDEO_TS has the usual .bup, .ifo, & .vob files.  

So, open K3b to burn .iso to DVD... drag the .iso file to the bottom panel and get dialog box:
"The file you are about to add to the project is an ISO9660 image. As such it can be burned to a medium directly since it already contains a file system.  Are you sure you want to add this file to the project?" 
[_A_dd the file to the project]   [_B_urn the file directly]

I choose Burn, and it burns a DVD.  However, inserting the DVD does not activate any program, and chosing "Open with" from the desktop icon does not show the menu that I created to allow the viewer to chose which video to view.  

If I chose Add, it attempts to burn, but I get a Brasero error message and the program stops without burning anything to disc.

IF I use Brasero, I can add the .avi files directly, but am not given the chance to create a user menu.

Using both ways of burning means that the user must use the commands in the selection bar of whatever program they are viewing with...

Isn't there a good program for Linux for burning DVD's, or am I just using the existing programs improperly?  I DO miss the programs for Windoze that did this, as it was a simple process...  Probably the only thing I miss about W...

Any suggestions, links, etc. greatly appreciated!  Thanks...

---

### Post by cotcot on 2011-01-15
K3b is an excellent burning application.

To burn your iso you have to go to --> Tools --> Burn DVD ISO image. A new window will ask you where your iso is. Browse to your iso and select it. 

This is different from what you have done. You just copied the iso as an iso on the dvd. 

Another way is to drag the VIDEO_TS and AUDIO_TS to the bottom panel and burn.

---

### Post by dkolars on 2011-01-16
Well, thanks...  did as you suggested, but inserting the DVD into the player did nothing... looking at the file structure, K3b simply copied the AUDIO_TS & VIDEO_TS sub-dirs to the DVD.  The file VTS_01_0.VOB contains the menu that I created, & when I open that file in VLC, clicking the titles does NOT open the corresponding video.

I'm going to try re-creating the .iso with DeVeDe and then burn that with K3b and see if there was a problem with the original .iso file.  Maybe I missed a setting in the original make???

If that doesn't work, I'm gonna be hunting for a better way to burn DVD's... I've got a LOT of videos of a couple of the bands I play in that I want to burn, and this is taking waaay to much time...

---

