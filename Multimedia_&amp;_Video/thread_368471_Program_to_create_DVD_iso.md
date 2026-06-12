---
title: "Program to create DVD iso?"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-02-23
I'm trying to burn some mpeg videos onto a dvd, but the problem is, the only DVD burner that I have is on my laptop which is running Windows XP MCE.  Whenever I try to create the DVD on the Windows machine using both DVDShrink and WinDVD, it can't create the audio because of some problem with the audio codec.  I have no faith in Windows software, since the two programs that I tried both created the disk without audio and didn't give any errors at all, so I would like to create a DVD iso on my Ubuntu machine and transfer it over to my laptop to burn.  Is there a program which will do this?  Also, is there a way to test the iso BEFORE I burn it to verify that it worked without wasting another blank DVD?

I should mention that the mpeg videos play fine (with sound) on both Linux and Windows.

---

### Post by billdotson on 2007-02-23
well K3B for the KDE desktop and gnomebaker for the gnome desktop will burn cd and dvd isos.  good luck

---

### Post by meng on 2007-02-23
Nautilus CD burner can create ISOs, after you press Write to Disc, you can select to burn to a file image rather than a drive.

---

### Post by audax321 on 2007-02-23
Correct me if I'm wrong, but I think his question is referring to encoding the mpegs into DVD format and then burning to disc, not just making the iso. Not that I know how to do this heh... good luck :) (I tried a long time ago and it was complicated back then)

Google should be helpful though.

Try this: [http://flavor8.com/index.php/2006/05/29/how-to-make-a-dvd-in-linux/](http://flavor8.com/index.php/2006/05/29/how-to-make-a-dvd-in-linux/)

It involves something called tovid

As far as testing goes, loading the iso directly into totem "should" load the DVD so you can test it before you burn.

---

### Post by uuwatti on 2007-02-23
also, dvdauthor will do that (encoding video to dvd-friendly format, creating menus and making the actual image file). If you want to use a frontend, devede and qdvdauthor are in the repos. You can test the iso file with vlc player. If you are ripping a dvd then k9copy is your friend.

---

### Post by josesanders on 2007-02-23
Thanks for the suggestions

Tovid is what I originally used to create the mpeg files in the first place (they used to be in mkv format that wouldn't play right anywhere), but I don't see how to use it to create an ISO.  I just tried k3b and gnomebaker, but they all refer to creating a DVD data disk.  Will such a disk play in a DVD player?

What I have decided to try is devede.  It seems very easy to use, and it says that it will create a DVD iso.  It's encoding right now, so we'll see in a few hours if that works.

This is certainly not the right place to ask this, but can anyone recommend a good free Windows program to burn the ISO?  I like ISO Recorder, but it doesn't work for DVDs.

---

### Post by taurus on 2007-02-23
> **josesanders said:**
> 
This is certainly not the right place to ask this, but can anyone recommend a good free Windows program to burn the ISO?  I like ISO Recorder, but it doesn't work for DVDs.

[http://www.cdburnerxp.se/download.php](http://www.cdburnerxp.se/download.php)

---

### Post by josesanders on 2007-02-24
Thank you for all of the suggestions.  What finally worked was devede to create the iso, and cdburnerxp to burn it.

Thanks

---

### Post by forkart on 2007-03-05
You can use magiciso to create dvd iso file, then burn iso file to dvd.
[http://www.magiciso.com/](http://www.magiciso.com/)

---

