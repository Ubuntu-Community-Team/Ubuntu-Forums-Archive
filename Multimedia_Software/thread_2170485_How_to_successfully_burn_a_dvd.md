---
title: "How to successfully burn a dvd"
date: 2013-08-26
forum: Multimedia Software
---

### Post by Lateralus138 on 2013-08-26
Hi all, I have did a search here, but haven't found exactly what I wanted so...

I am trying to burn a movie from dvd folders (audio_ts, video_ts) and have been quite unsuccessful. I have been experimenting. In Windows I will usually take the folders and create an iso image then burn with ImgBurn or other software and 100% of the time it is successful. I created an iso of the the files using:
```
mkisofs -o Downloads/thecomp.iso Downloads/thecompfolder
```
and then used Brasero to burn the iso. Note: it burned and then created a checksum. I took the disk out of the drive and put it in my Xbox and it just came up with the Xbox logo after I tried playing the DVD. I then put it back in my computer and the autoplay thing popped up asking what to do and clicked ok and the movie player popped up but said it could not play the file. I then browsed to the cdrom and tried running the menu vob and could not push and buttons. I then went to the 1st video vob and it actually played, but if I tried fast forwarding it made the movie player freeze. The VOB files from the download folder play just fine. My guess is that it either has something to do with permissions or what settings I have set in Brasero or maybe the way I converted to iso. I also tried playing in a regular dvd player and didn't work. I am not as familiar with burning on Linux yet so can someone please explain to me the best way to burn vob files and make playable in XBox 360?

---

### Post by speartip on 2013-08-26
What type of files are you trying to burn (.avi .mp4 etc)>?
You may need to use a program called devede to convert your files into an iso before burning.
Also make sure you have the ubuntu-restricted-extras package installed.

---

### Post by Lateralus138 on 2013-08-26
They are VOB (DVD) files, not containers, and I do this all the time in Windows; have the AUDIO_TS and VIDEO_TS in a DVD folder and put the DVD folder into an iso and just burn with ImgBurn... I have been reading hard about mkisofs and growisofs and it seems I was doing it wrong. I have attempted do to follow instructions on this [page]("https://wiki.archlinux.org/index.php/Dvdbackup") and now recieved the 2nd error on this [page]("http://askubuntu.com/questions/28052/how-do-i-create-a-video-dvd-from-vob-files"). I screwed up my last disk while attempting to burn with growisofs and I forget the error now since it was 6 hours ago maybe, so I will have to wait until I can buy more disks before I can attempt it again. 

As for the the resticted extras package I had forgotten all about reinstalling it on my last clean install so thanks for the reminder! I just read about that devede so I'll check that out too... I'll get some more disks soon and attempt this again and reply back with results

---

### Post by Jonor on 2013-08-27
Thanks for the tip speartip, i just managed to put some avi onto a DVD after getting frustrated with both Brasero and K3b, DeVeDe is noobproof : )

---

