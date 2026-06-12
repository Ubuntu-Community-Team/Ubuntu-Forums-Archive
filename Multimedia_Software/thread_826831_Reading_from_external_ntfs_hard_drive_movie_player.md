---
title: "Reading from external ntfs hard drive movie player works, vlc doesn't?"
date: 2008-06-12
forum: Multimedia Software
---

### Post by cinohpa on 2008-06-12
So, basically topic. 

I'm completely new to ubuntu so I might just need to install something, but as is the movie player that came with ubuntu will play .avi files from the hd, but when I try to open the same video files with vlc I get an error and nothing will play.

Also playing with the ubuntu movie player, the video is pretty bad relative to what it usually is. 

I also tried copying the file to my desktop which worked save an error. From the desktop it stilled played in the ubuntu movie player, but not in vlc. I have had vlc work with other .mov files that I had previously on the ubuntu partition.

Any suggestions/explanations?

Thanks.

---

### Post by cinohpa on 2008-06-12
hmmm strangely enough. This problem is only caused with one anime that I have on my hd. All of the other files appear to be working in vlc with normal quality video. 

I tried using the ntfs configuration utility to mount an external hd this time but I didn't try the other files (the ones that are working now) until after that configuration. 

I hope I didn't corrupt those other files now because they still won't play. . .

---

### Post by eye208 on 2008-06-12
VLC has a stream info window and a message log window. The stream info window will tell you what's inside the AVI. The message log will tell you why VLC can't play the file.

Open the message log window, then try to play the file and watch out for error messages.

---

### Post by zero777zero on 2008-06-22
i'm trying to play mpeg/avi/mp4 on an external harddrive which is NTFS. my drives are working fine and i'm playing music off them, when i copy the video file onto my laptop drive it plays fine, but when i play them i get something like this:

Unable to open 'file:///media/931NTFS/2%20movies%20+%20tv/Blue.Velvet%5B1986%5DDVDrip%5BEng%5D-Kole.avi'


it plays fine in Totem. unistalled and reinstalled VLC, didnt help.

on hardy heron

---

### Post by fermulator on 2008-10-13
> **zero777zero said:**
> i'm trying to play mpeg/avi/mp4 on an external harddrive which is NTFS. my drives are working fine and i'm playing music off them, when i copy the video file onto my laptop drive it plays fine, but when i play them i get something like this:

Unable to open 'file:///media/931NTFS/2%20movies%20+%20tv/Blue.Velvet%5B1986%5DDVDrip%5BEng%5D-Kole.avi'


it plays fine in Totem. unistalled and reinstalled VLC, didnt help.

on hardy heron

same problem here trying to play a movie from a locally mounted ntfs-3g drive.  If the file is copied over to an ext3 partition, it works.

---

