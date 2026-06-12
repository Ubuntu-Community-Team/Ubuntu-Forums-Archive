---
title: "Network access to myth recorded files"
date: 2015-12-20
forum: Mythbuntu
---

### Post by gga96 on 2015-12-20
My myth recordings get saved to directory /media/hdd2/mythtv/recordings. I  own the directory but the video files themselves are owned by user mythtv.  
  
 The permissions for both directory and video files follow:
  
 ```
glen@backend1:~$ ls -l  /media/hdd2/mythtv
 total 12
 drwxrwxrwx 2 glen glen 4096 May 12  2014  db_backups
 drwxrwxrwx 2 glen glen 4096 Dec 19 11:32  livetv
 drwxrwxrwx 2 glen glen 4096 Dec 21 06:01  recordings
 glen@backend1:~$ ls -l  /media/hdd2/mythtv/recordings
 total 138088568
 -rw-r--r-- 1 mythtv mythtv 2448419692 Dec 14 05:59  1002_20151213175900.mpg
 -rw-rw-rw- 1 mythtv mythtv      88507 Dec 14 06:01  1002_20151213175900.mpg.png
 -rw-r--r-- 1 mythtv mythtv 2433412216 Dec 14 15:30  1002_20151214032900.mpg
 -rw-rw-rw- 1 mythtv mythtv      79394 Dec 14 15:33  1002_20151214032900.mpg.png
 -rw-r--r-- 1 mythtv mythtv 3221050248 Dec 14 18:44  1002_20151214062400.mpg
 -rw-rw-rw- 1 mythtv mythtv      88608 Dec 14 18:47  1002_20151214062400.mpg.png
```
 ...
  
 The group data for glen and mythtv follow:
  
 ```
glen@backend1:~$ id glen
 uid=1000(glen) gid=124(mythtv)  groups=124(mythtv),0(root),4(adm),24(cdrom),27(sudo),30(dip),44(video),46(plugdev),110(sambashare),1000(glen),125(lpadmin)
 glen@backend1:~$ id mythtv
 uid=115(mythtv) gid=124(mythtv)  groups=124(mythtv),20(dialout),24(cdrom),29(audio),44(video)
```
  
 I can successfully connect from Win7 on the LAN with other directories that  have similar permissions, but will not recognize the  /media/hdd2/mythtv/recordings director or the contained files.

  
 I cant figure out what I have to do with ubuntu to gain access and copy one  of the myth recordings to my Win7 machine.
  
 What is it that I need to do to fix this problem?

  

 Thanks a lot, hope you can help
  
 Regards 
 Glen

---

### Post by ryry46d92 on 2015-12-21
Samba ? 
Myself, I transcode the tvshows to mp4 then host them via Plex. 
So even at work I can watch shows on my android phone.

---

