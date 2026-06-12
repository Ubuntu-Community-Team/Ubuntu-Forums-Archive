---
title: "I cannot use mp4 files or .exe files"
date: 2020-02-19
forum: Multimedia Software
---

### Post by derpychez-151 on 2020-02-19
Hello,
I am new to Linux Ubuntu, and so far it's great. My only problem is that I can't play mp4 files, or access .exe files. I haven't tried much for fear of my computer, but could someone more experienced with this OS help?

For further information, I used a bootable USB to change my Windows 10 HP laptop to 18.04 Linux Ubuntu. If it helps, it's a 2016 HP Pavilion Notebook.

Please let me know if you have any ideas about what can fix this, I need my Shrek to work.

Thank you!
Chez

---

### Post by CelticWarrior on 2020-02-19
EXE files are Windows executable files. They don't work in Linux. Some Windows software can run acceptably with Wine but not all.

For playing media files it needs codecs. Likje in Windows or Mac not all required codecs are natively available or installed by default. In Ubuntu you can have almost everything you will ever need by installing ubuntu-restricted-extras:

```
sudo apt install ubuntu-restricted-extras
```

---

### Post by hk42 on 2020-02-19
Hi and welcome to Linux world.
For a newcomer there are a few software's that are common to Windows,Android ,Apple and Linux.
Shame that some of them are not included in the basic Ubuntu distribution.
For *.mp4 files and lots of others VLC is the good choice.
Even play list can be shared on different OS
Beware that in Ubuntu you must stop playing a file/stream before closing VLC.
Otherwise a part of it stays in memory and sometimes prevent any other use.

---

### Post by yancek on 2020-02-20
I'm not sure where you would have .exe files if you have overwritten your windows install with Ubuntu.  I would suggest you begin by reading the Ubuntu documentation at the link below.  And how exactly did you try to play mp4 files and fail, what software?

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by TheFu on 2020-02-20
Even today, I usually send people new to Linux here: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
so they can get the most important knowledge ASAP. Don't worry too much about the 2014 article date.

That knowledge from the article limits the inevitable frustration that changing operating systems will cause.  Linux has a completely different philosophy than either Windows or OSX.  It takes time to transition away from "the way it worked on Windows" to the way things work on Unix platforms.  

You will still get frustrated from time to time, but it won't be from unwanted patches or viruses.

+1 on using VLC.  All the codecs are included in VLC's code. My stance is that if VLC can't play it, then I don't really want to see it.  

There is one caveat with VLC, Ubuntu has been switching from the 25 yr old .deb packages to snap packages the last year or so.  VLC was one of the early converts to a snap package.  Snaps, as we call them, have some niffy security features.  But with those constraints added for security reasons, we also lose the ability for snap programs to access some storage locations outside the userid's HOME.  It isn't a problem until it is, then even 25+ yr Linux users get frustrated with snaps.  I've wishes the snap designers bodily harm, from time to time.  They mean well, but ... part of the reason people use Linux is for flexibility. Snaps take some flexibility away.

---

