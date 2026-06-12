---
title: "problem with riping dvd's"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by jacob01 on 2008-03-30
im trying to back up my dvd's onto my hard drive and i have tried a couple times using both acidrip dvd ripper, and dvd::rip but it seem that both i am having a little of a quality problem and the sound is a few seconds off the actual video.

what i am asking is does any one know how to fix this or another program that will work better.

---

### Post by mc4man on 2008-03-30
are you looking to just rip the entire disk 'as is' ?

---

### Post by pseudo-random on 2008-03-30
When I rip I use: ```
mencoder dvd://$title -o Videos/$name.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4 -alang en

```
This format is good quality given the much reduced size.
As for your lag, whats your hardware specs?

---

### Post by jacob01 on 2008-03-31
well i am looking to rip the video and convert it to as high of quality that is still practical size (8 gig at the most) to a format like mp4 or mpeg mpeg2... and so that the sound is right on with the video

---

### Post by Prefix100 on 2008-03-31
to rip my DVDs I use

```
sudo cat /your/devicepath > /home/username/dvdname.iso
```

Finding your device path is easy, use system monitor, then click the 'file systems' tab to find the right device name.

This will make an iso of the disc which can be used to burn more DVDs or can be played through VLC.

---

### Post by benerivo on 2008-03-31
I know k9copy is meant to be very handy. It works in a similar way to DVDShrink for Windows. The audio syncing is fine and it can shrink the DVD to a .iso file of 4.7GB so that it will fit on to a regular DVD, and you can still play the file on the computer.

---

### Post by jacob01 on 2008-03-31
yea i tried k9copy but i still noticed a quality issue and teh sound was still of the vid my a little

---

### Post by benerivo on 2008-03-31
Do you have the disk space to just keep them as unconverted iso's?

---

### Post by jacob01 on 2008-03-31
yea i have plenty of space (180 gig) but i want to be able to watch them too. I riped it and i get little likes that leave a little trail on the image around moving objects in the picture like elongated pixels, and i encoded it at at 30 fps and with over 6000 kb/s so i don't know whats causing the problem. could it be my screen? i really don't think so but it is rather old and i was thinking about trying out my s-video on a small hdtv i have. ill tell you what happens.

---

### Post by benerivo on 2008-03-31
Have you tried just making a copy of the disc image (not ripping) and using that for your backup/playback. The playback result will be identical to playing the original disc itself. Any graphical problems that you notice from playback from disc, will be due to the limitations of the pc and/or os. I'm sure any computer monitor will have specs that exceed those of a DVD.

---

### Post by Prefix100 on 2008-03-31
Try the method i posted above then play it with vlc, it should work perfectly - at least it does for me.

---

### Post by jacob01 on 2008-03-31
yea ill try it cool thanx

---

### Post by OZFive on 2008-04-17
> **Prefix100 said:**
> Try the method i posted above then play it with vlc, it should work perfectly - at least it does for me.

That is another very cool thing I did not know I could do, but now I do!  Thanks!

---

