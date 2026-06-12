---
title: "Mythbuntu won't refresh file list in videos folder..."
date: 2010-03-06
forum: Mythbuntu
---

### Post by killabee44 on 2010-03-06
Guys,

I am having a problem where mythbuntu will not let me see my video files. It shows a folder with a question mark on it named: "unknown prefix". 

When you click it and navigate it, it takes you to an old folder which has been deleted.

Is there a way to clear the database?

Is there a step I missed? I thought this was supposed to be done automatically? 

Thanks.

---

### Post by tgm4883 on 2010-03-06
What is the old folder? What version of MythTV are you using? What version of Mythbuntu are you using?

It could be picking up the storage group or local frontend settings.

---

### Post by killabee44 on 2010-03-06
> **tgm4883 said:**
> What is the old folder? What version of MythTV are you using? What version of Mythbuntu are you using?

It could be picking up the storage group or local frontend settings.

Thanks for your reply...

I am using mythbuntu 9.10 which comes with myth .22

Music and pictures are on home drive. Recordings, Library and livetv are on the new media drive.

I am using the default folders in myth linked to folders on a separate drive which contains my videos. They are linked via symbolic links.

ls -l /var/lib/mythtv:
 
```
total 44
lrwxrwxrwx 1 root   root     27 2009-12-08 22:54 banners -> /media/mythtv/video/banners
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 banners_old
lrwxrwxrwx 1 root   root     28 2009-12-08 22:54 coverart -> /media/mythtv/video/coverart
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 coverart_old
lrwxrwxrwx 1 root   root     24 2009-12-08 22:54 db_backups -> /media/mythtv/db_backups
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 db_backups_old
lrwxrwxrwx 1 root   root     26 2009-12-08 22:55 fanart -> /media/mythtv/video/fanart
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 fanart_old
lrwxrwxrwx 1 root   root     26 2009-12-08 22:54 livetv -> /media/mythtv/video/livetv
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 livetv_old
lrwxrwxrwx 1 root   root     17 2009-12-08 22:06 music -> /home/htpc1/music
drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 05:10 music_old
lrwxrwxrwx 1 root   root     20 2009-12-08 22:06 pictures -> /home/htpc1/pictures
drwxrwxr-x 2 mythtv mythtv 4096 2009-10-26 05:10 pictures_old
lrwxrwxrwx 1 root   root     30 2009-12-08 22:06 recordings -> /media/mythtv/video/recordings
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 recordings_old
lrwxrwxrwx 1 root   root     31 2009-12-08 22:55 screenshots -> /media/mythtv/video/screenshots
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 screenshots_old
lrwxrwxrwx 1 root   root     28 2009-12-08 22:57 trailers -> /media/mythtv/video/trailers
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 trailers_old
lrwxrwxrwx 1 root   root     27 2009-12-08 22:06 videos -> /media/mythtv/video/library
drwxrwsr-x 2 mythtv mythtv 4096 2009-12-07 23:27 videos_old
```

Shouldn't it say mythtv mythtv and not root root?

---

### Post by tgm4883 on 2010-03-06
Well that would depend on who owns the other folders. 

Why don't you go into mythtv-setup and change the storage group locations rather than use the symlinks?

---

### Post by killabee44 on 2010-03-06
> **tgm4883 said:**
> Well that would depend on who owns the other folders. 

Why don't you go into mythtv-setup and change the storage group locations rather than use the symlinks?

I only did it this way so that everything would stay at default within Myth. 

I set the folders within mythtv-setup pointing to the media drive directly and it still does not work. 

After setting the folder locations in Mythtv-setup I did not get an error when exiting (I got an error of invalid folder in the past when I mistyped a folder name), so I know it is set correct.

It's just weird that when you browse the media folder it shows a folder there that has been deleted for a while now. 

Is there a cache I can clear to fix this or somehting?

---

### Post by tgm4883 on 2010-03-06
You could try hitting M and then scan for changes. Do you have multiple frontends? What is the path that doesn't exist anymore? Does that path exist on another frontend machine?

---

### Post by killabee44 on 2010-03-06
double post..

---

### Post by killabee44 on 2010-03-06
Ok will try that when I get home. This setup is a simple one with the HTPC front and back end on one machine. My plan is to later on make this into the back end only and set up a quiet front end.

The path that you mentioned is just a movie folder I put there and later deleted.

---

### Post by killabee44 on 2010-03-06
Ok, finally got it thanks for your last suggestion. I was trying pressing M but did not know where I had to press it. While in the menu for the front end, etc. because I am so new at this.

The solution that while in the Myth Frontend Utilities/Setup go to Video Manager and then press M and select scan for changes. 

If you press M at other menus you will not get the option to scan for changes.

 Hopefully this will help someone and they will not have to spend as much time as I have trying to solve something that seems so simple now.

Thanks a lot tgm4883...

---

