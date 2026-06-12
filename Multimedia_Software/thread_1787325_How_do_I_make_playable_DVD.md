---
title: "How do I make playable DVD?"
date: 2011-06-21
forum: Multimedia Software
---

### Post by j*tech on 2011-06-21
I am trying to make a DVD from video files, that will play in DVD players and specifically my PS2...My video files are mostly avi, wmv, and mp4, and im currently running 11.04...
  
What program should I use?...What process?...I have a new burner and sum DVD's im dieing to use :wink:....

---

### Post by nomko on 2011-06-21
I use K3B and i do it this way:
 
When K3B is srated up, i choose: create video-dvd
The screen then shows at the bottom left a pane where i can drag/drop the video files ( 2 folders are shown: AUDIO_TS and VIDEO_TS). i navigate to the folder which contains the video files and drag the 2 folders the right folder to the right place (you have to drag/drop the files to the root, not in VIDEO_TS). After that it's just a matter of burning!
 
But which burning application you're using?

---

### Post by dFlyer on 2011-06-21
I use Brasero. Just click video project and follow the instruction within the screen to add your data.

---

### Post by j*tech on 2011-06-21
nomko - using .avi, .mp4, and .wmv files :(...DL'd k3b, Brasero, DeVeDe, Bombono, and DVD Styler lol...


dflyer - I will try that later today...

---

### Post by nomko on 2011-06-21
> **j*tech said:**
> nomko - using .avi, .mp4, and .wmv files :(...DL'd k3b, Brasero, DeVeDe, Bombono, and DVD Styler lol...
 
 
dflyer - I will try that later today...
 
IF your DVD player can handle AVI, then you can burn the avi as a normal data CD/DVD. WMV and other formats i uselly convert them into .vob files using a prgram called Devede. Here's a site where you read 1 or 2 things about this program: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html).
 
Best part of Devede is that it converts almost any format into a DVD readable format (.vob) and puts it in a .iso file so you just have to birn the image but having a fully readable DVD (the .iso will be extracted by the bunring tool and then burned on the disc).

---

### Post by j*tech on 2011-06-21
Do I need to transcode video files first?...DeVeDe seems like my best bet, although I have already experienced a few errors today and I heard its quite buggy on 11.04...After I have the .vob files, how should I burn them?...Can I drag-n-drop burn?...Appreciate the help so far man, DVD authoring isn't as easy as I initially thought ](*,) lol...

---

### Post by nomko on 2011-06-22
Devede has the option of creating an iso image file which contains all the video (.vob) files. The only thing remaining for you is burning the iso image file. To let Devede create an iso image file you have to expand the advanced options below and mark: creating ISO or BIN/CUE image file, ready for burning (or something like this, i'm using Devede with the Dutch language).

---

### Post by andrea000 on 2011-06-22
2ManDVD is a full featured dvd authoring application and
the successor of ManDVD you can download the .debs [here]("http://debian-multimedia.org/dists/unstable/main/binary-i386/")
or the source [here]("http://kde-apps.org/content/show.php?content=99450")

---

### Post by j*tech on 2011-06-22
[LEFT]Found an awesome tuturial - [http://www.ghacks.net/2009/03/20/create-dvds-in-linux-with-devede-mkisofs-and-k3b/](http://www.ghacks.net/2009/03/20/create-dvds-in-linux-with-devede-mkisofs-and-k3b/)
[/LEFT]

---

