---
title: "Cannot get VLC and Acetoneiso to work together. Any help please"
date: 2009-03-21
forum: Multimedia Software
---

### Post by Alethenorio on 2009-03-21
Hi guys. I am no expert on linux but I usually hold my own however after spending about a day trying to get Acetoneiso and vlc to work together I decided to come crawling to the forums :)

I can mount images just fine on acetoneiso, as soon as I mount nautilus comes up with the mounted folder open and everything seems fine however if I right click on the disc icon on the desktop and teel it to open with vlc or if I tell vlc to open a disc and point it to the mount directory, it just throws me an error message and it wont play.

If I just open the vob files instead with vlc that works too.

The interesting part is that after I try to open the disc with vlc (As a disc) the mounted folder is no longer accessible from nautilus or anywhere. Trying to do a 'ls' within the mounted folder throws this message back

ls: cannot open directory .: Transport endpoint is not connected

Thats about the extent of my problems, I have tried 2 different versions of acetoneiso (2.0.2 and 2.0.3 RC1) and I am using the latest vlc version, I have nautilus and vlc on acetone config.

Could anybody shed some more light on the situation?

---

### Post by mc4man on 2009-03-21
Is there any particular reason you're mounting the .iso for use with vlc?

Vlc can play an .iso without it being mounted, just r.click on the .iso -> open with vlc or open the .iso from vlc (open file

All of the 0.9.x versions have some issues, opening dir.'s from vlc can work, not work or work poorly (particularly if the dir. is or contains a video_ts)

---

### Post by Alethenorio on 2009-03-22
I did not know you could open isos wth vlc as I found out yesterday upon searching the net and trying it out.

Thanks for the info, it is a pitty though that you can't mount the images and open with vlc afterwards.

---

