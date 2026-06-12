---
title: "problems watching an .iso"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by mshale on 2007-05-22
> I need to watch a file called foo.iso . But how do i mound it ??

and where do i mount it too ? /mnt ???

EDIT: NM

sudo mount -t iso9660 -o loop,ro /home/notig/Desktop/foo.iso /mnt

i tried this, and all i get is two folders, one audio_ts and one video_ts.  how do i mount it so that i can watch the video that is inside that .iso?  i need it to perform as though i put the image on a cd and put that cd into the drive.  Thanks so much for all of your help.  I did a search but all i could find was this, and it didn't quite deliver what i needed.  I tried a script too, but that didn't work out too well either.  any suggestions?

oh, here is the script.  maybe what i need is someone to help the script out ;)

```
#!/bin/bash 
# 
for I in "$*" 
do 
foo=`gksudo -u root -k -m "Enter your password for root terminal access" /bin/echo "got r00t?"` 
sudo mkdir /media/"$I" 
sudo mount -o loop -t iso9660 "$I" /media/"$I" && nautilus /media/"$I" --no-desktop 
done 
done 
exit0
```

---

### Post by taurus on 2007-05-22
What if you watch it directly with gmplayer.  Assuming you are in the same directory where the movie, movie.iso, is, run

```
gmplayer movie.iso
```

---

### Post by ronocdh on 2007-05-22
I just use VLC. You can open an ISO up in that and it plays just like you're watching a DVD.

---

### Post by mshale on 2007-05-23
> **taurus said:**
> What if you watch it directly with gmplayer.  Assuming you are in the same directory where the movie, movie.iso, is, run

```
gmplayer movie.iso
```

i tried your solution taurus, and this is what was returned.

```
Playing /media/sharedmedia/Videos/graduation.iso.
MPEG-PS file format detected.

Too many video packets in the buffer: (4096 in 7718621 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)
```

VLC worked!! thanks a ton!

thanks all!

---

### Post by fearevilleet on 2007-05-23
Try VLC it will play everything even iso's without mounting them.

---

### Post by taurus on 2007-05-23
> **mshale said:**
> i tried your solution taurus, and this is what was returned.

```
Playing /media/sharedmedia/Videos/graduation.iso.
MPEG-PS file format detected.

Too many video packets in the buffer: (4096 in 7718621 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)
```

VLC worked!! thanks a ton!

thanks all!

Your problem is MPlayer is using a wrong video driver, video_out.

Start MPlayer and go into Preferences -> Video and change the driver to xv.

---

### Post by stchman on 2007-05-23
> **fearevilleet said:**
> Try VLC it will play everything even iso's without mounting them.

I use VLC for everything.  Only thing is the CDDB does not work with VLC.  Have you been able to get it to work?

Thanks

---

### Post by mshale on 2007-05-23
> **stchman said:**
> I use VLC for everything.  Only thing is the CDDB does not work with VLC.  Have you been able to get it to work?

Thanks

I'm not too handy with acronyms sir, so i don't quite know what you are speaking of.

As for the MPlayer solution, that last post you made, taurus, got it working in mplayer.  for that, i thank you :KS

---

### Post by stchman on 2007-05-24
> **mshale said:**
> I'm not too handy with acronyms sir, so i don't quite know what you are speaking of.

As for the MPlayer solution, that last post you made, taurus, got it working in mplayer.  for that, i thank you :KS

CDDB = CD database

When you insert a CD into a drive a list of th songs come up.

---

### Post by mshale on 2007-05-26
> **stchman said:**
> CDDB = CD database

When you insert a CD into a drive a list of th songs come up.

i never listen to cds on my laptop, so no i haven't gotten it to work. sorry, though.

---

