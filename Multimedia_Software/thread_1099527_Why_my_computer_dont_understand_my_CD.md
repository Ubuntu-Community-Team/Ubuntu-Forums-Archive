---
title: "Why my computer dont understand my CD?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by daGrevis on 2009-03-18
My computer dont understand my CD... :(

[[IMG]http://img23.imageshack.us/img23/122/disks.th.png[/IMG]](http://img23.imageshack.us/my.php?image=disks.png)
[[IMG]http://img10.imageshack.us/img10/6647/cd2.th.png[/IMG]](http://img10.imageshack.us/my.php?image=cd2.png)

---

### Post by Sarai the Geek on 2009-03-18
Sorry, could you be a little more specific?
Are you saying that it's not showing you have a cd in the drive?

Type this in your terminal:
```
sudo mount /media/cdrom
```

---

### Post by 123456789123456789123456 on 2009-03-18
a couple of possibilities.  I am unable to see the picture of the program you were using.  If Ubuntu reconizes that a disk is in the drive.  a disk other than audio cd.  Audio cd's will not appear on the desktop.

The format of the disk may not be compatable with the player you are using.
test this
download the following program, and try to read the disk through it.

in terminal type
sudo apt-get install vlc

vlc is a free media player, plays mp3, audio cd, 99.9% of all sound formats except the new wma.  and plays dvd, and all video formats.  If VLC can't play the disk, it is unreadable most likely.  If it says that there is no disk in the drive, then ubuntu is for some reason not mounting the device.  in that case try the mount command listed above this message.

---

### Post by Sarai the Geek on 2009-03-18
> **123456789123456789123456 said:**
> I am unable to see the picture of the program you were using.

The first picture is brasero, with a popup window that says "there is no available medium, please insert one" under cd rom drive.

The second is a shot of nautilus showing the available drives under "computer". CD rom is not one of them.

It might also bear mentioning that it looks like a very fresh install- all the gui settings are on default. Also, it's a toshiba.

That wasn't a thousand words, was it? ;)

---

