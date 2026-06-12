---
title: "Bluray or DVD"
date: 2013-01-25
forum: Mythbuntu
---

### Post by tez1982 on 2013-01-25
I've enabled BluRay playback on my system and it works fine in VLC.

Is there a way of calling a script when I select "Play Optical Disc" that will check if it is a BluRay or DVD in the drive and call VLC with the appropriate command?

Normal command for BluRay: 
vlc bluray:///dev/dvd

Normal command for DVD:
vlc dvd:///dev/dvd

N.B.
I'm guessing there is not a simple way to do this using the internal player?

---

### Post by topcat5 on 2013-01-26
Another suggestion is to use Handbrake (I do this on another machine) to rip the disk then sftp the file to your videos directory.   Once you figure out the naming conventions, the system will automatically download metadata, screenart, etc.  

You can then play the video on any frontend at any time.  All the annoying menus are gone, and you can add subtitles if it is a foriegn disk.

---

### Post by nickrout on 2013-01-26
> **tez1982 said:**
> I've enabled BluRay playback on my system and it works fine in VLC.

Is there a way of calling a script when I select "Play Optical Disc" that will check if it is a BluRay or DVD in the drive and call VLC with the appropriate command?

Normal command for BluRay: 
vlc bluray:///dev/dvd

Normal command for DVD:
vlc dvd:///dev/dvd

N.B.
I'm guessing there is not a simple way to do this using the internal player?Perhaps reading the instructions might help you? [http://www.mythtv.org/wiki/Bluray#Watching_With_the_Internal_Player_.28recommended.29](http://www.mythtv.org/wiki/Bluray#Watching_With_the_Internal_Player_.28recommended.29)

---

