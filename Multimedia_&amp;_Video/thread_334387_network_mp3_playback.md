---
title: "network mp3 playback"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by twidget on 2007-01-08
[LEFT]hi
  I've got two Linux boxes on a windows network, the fast one runs Kubuntu Dapper and the slower one runs Xubuntu Edgy. I'm trying to get the Xubuntu machine to play mp3 files stored on the Kubuntu machine. I have Samba configured and, from what i can tell, running properly on both machines. The folder containing my music is mounted  startup via fstab.
   Ive installed both Amarok and XMMS but neither seem to work right. 
   Amarok scans the folders for a bit and then fails saying that there were too many errors. it also says i should maybe try re-installing TagLib which I've done.
   XMMS scans for a bit then plays one mp3 and then scans a bunch more before returning to the same mp3. if i manualy go to a different mp3 it scans a bunch and then starts playing the same song.
  does anyone know of a way to fix this?](*,) 
thanks in advance[/LEFT]

---

### Post by deadgobby on 2007-01-09
have you tried to install the restricted formats? 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Gobby

---

### Post by twidget on 2007-01-09
I dont think its lack of codecs. like i said XMMS at least plays mp3s...well one mp3 anyway. 
in the mean time i tried copying over a random mp3 over the network and that failed giving me a message that i had the wrong permisions or something like that. so i think this may be a permissions problem. i still think my samba share is set up right because i can read and write to the shared folder. so could this mean that the permisions on the mp3's are somehow messed up? if so how would i find out what i need to set the file's permisions to? also is there a way i can set the permisions of everything in a directory? I'm hoping i dont have to do each file individualy since that would take forever.

---

### Post by twidget on 2007-01-09
looks like it was at least partialy a permissions thing
on server :
```
sudo chmod -R 777 sound
```
XMMS now seems to be playing fine. Amarok on the other hand still fails to build its collection.
](*,)
the permissions could probably be done better but im tired of messing with it.

---

