---
title: "MPlayer cannot open files with spaces"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by ZOMGxuan on 2007-11-02
Recently when I tried to open video files with spaces in them with mplayer, mplayer gives me an error, saying it is unable to open the file. I am not opening the file through command line, I know perfectly well how to open files with spaces in them using gmplayer in command line. In fact that is the only way i can open video files with spaces with mplayer now. 

The problem here is when i set mplayer as the default program to open video files in nautilus, and then double click on a video file with spaces in the filename or directory path, mplayer gives a error, saying it failed to open the file. Below is picture showing what I mean:
[[IMG]http://img232.imageshack.us/img232/5078/screenshoterrorjw1.th.png[/IMG]](http://img232.imageshack.us/my.php?image=screenshoterrorjw1.png)

As you can see it is particularly a problem when I'm trying to open files still in my windows HD (because I'm too lazy to move them :p). All the white space has been replaced by %20 and makes mplayer unable to open the file. This is strange because i could open files with directory paths with spaces in them previously. 

I do not think this is a problem with the system version or GNOME because this problem occurred even before I upgraded to Gutsy, and I did not install mplayer from the repos, I compiled it myself from source to enable JACK compatibility and other codecs to work. Originally i installed Mplayer from the repos, and it worked properly then, then i compiled it from source once and it still worked. I think this only started happening after I compiled it from source a 2nd time. So could anybody tell me what is the cause of this problem and how to solve it?

---

### Post by Ripichip on 2007-11-07
[http://ubuntuforums.org/showthread.php?t=591923&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=591923&highlight=mplayer)

---

### Post by Lostincyberspace on 2007-11-07
I have never tried with the gui but i can do it in the command line.

---

### Post by ZOMGxuan on 2007-11-11
Thanks the link works great! (Post no.3)
But i had to copy the mplayer.desktop file to "your username"/.local/share/applications for it to work.
And for anyone else who reads this thread and the linked thread wonders what "Exec=" is, just open the .desktop file using the text editor and see for yourself.

Problem Solved. :)

---

