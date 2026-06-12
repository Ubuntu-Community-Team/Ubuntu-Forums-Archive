---
title: "Creating SVCD with Kino and Brasero"
date: 2009-10-28
forum: Multimedia Software
---

### Post by cscj01 on 2009-10-28
I am rather new to Ubuntu and Linux, and I am trying to create an SVCD on a CD-R using Kino and Brasero as follows:

[LIST=1]
[*] Import the video from my camcorder via firewire using Kino;
[*] Edit and trim using Kino;
[*] Export using Kino with the following options on the MPEG tab:
    [INDENT](a) 8 - DVD;
    (b) Deinterlace - None;
    (c) Aspect Ratio - Autodetect;
    (d) Output dvdauthor XML - Create DVD-Video (dvdauthor);[/INDENT]
[*] Create a new video project using Brasero.
[/LIST]

The process through Step 3 seems to be fine with Kino creating a folder with the usual AUDIO_TS and VIDEO_TS folders with AUDIO_TS empty and VIDEO_TS containg the BUP, IFO, and VOB files, and I can view the VOB files created by KINO.

At this point I am confused.  As I am coming from an XP environment, I would burn these two folders to the CD.  However, Brasero won't let me select folders; only files.  Am I using Brasero incorrectly?  Will Brasero create an SVCD for me by only specifying the VOB files?

---

### Post by vinutux on 2009-10-28
yes....... select any video file from folder and hit burn button 
You will get an window for selecting appropriate media like svcd,vcd etc

And feel free to experiment with that means select **[COLOR="Red"]Image file[/COLOR]** from select disk to right menu it creat an iso image in your hard disk

---

### Post by cscj01 on 2009-10-28
Okay, I tried that.

I added the 3 VOB files.  When I select Burn, I get a message which says "It is not possible to write with the current set of plugins."

Under Edit/Plugins I show 4 plugins.  They are File Checksum, File Downloader, Image Checksum, and Normalize.

What do I need to add?

BTW, I am running Ubuntu 9.04 and Brasero 2.26.1, which came with Ubuntu 9.04.

---

### Post by vinutux on 2009-10-28
Try k3b ```
sudo apt-get install k3b
```


Anyway when u export fom kino try other options like avi.mpg,ogm etc

---

### Post by cscj01 on 2009-10-29
I decided to try to burn a data CD using Brasero and the AUDIO_TS and VIDEO_TS folders as my source.  It worked.

However, there is one strange outcome.  If I open with Movie Player (Totem) and select Open Location, the video plays with no sound.  If I use Nautilus and double-click on the first VOB, it plays with sound in Movie Player.

Can anyone tell me what is happening?.

---

