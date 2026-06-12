---
title: "Watching DivX in DVD Player"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by milad on 2007-04-13
My DVD player supports Divx format but sometimes it can't play them. So is there any point I have to know before I burn a CD or DVD containing divx files so that they be playable in DVD Players? Or maybe we have differrent kind of divx files and my dvd player is only able to play some of them?

---

### Post by Archmage on 2007-04-13
You are right. Although most of the files are just named xxx.AVI they are not all the same. Most propably your DVD-Player can't play the newest DIVX (6.0?) or you are trying playing XVID with qpeg setting one. (Most of the XVID-files can be played in a DVIX-Player, but not all.)

---

### Post by milad on 2007-04-13
So is there any way to convert , for instance, XVid to DivX5 in Linux?

---

### Post by milad on 2007-04-13
Problem Solved!
I downloaded a small software for windows called [AVI FourCC Code Changer]("http://www.videohelp.com/tools?tool=AVI_FourCC_Code_Changer") and run it using wine. Then changed xvid to divx and XVID to DX50

That's it! This change in FourCC thing makes your standalone player think your video is DivX5

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29636&stc=1&d=1176484387[/IMG]

---

