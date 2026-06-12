---
title: "[SOLVED] Trying to copy DVDs"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by afderrick on 2008-01-27
I am wanting to copy my DVDs to my hard drive so I can start to support networked video playback off my home server.  (read I want the DVD on a PC in my basement and want to watch them on my HTPC in my living room.  I have tried k9copy and it said finished but when I went in to check it the sound was fast and the video looked garbled (probably as the same speed of playing as the sound).  I also tried using dvd::rip and it was going well until about halfway through the project and the program just quit running.  Any suggestions on how I can accomplish this so I can throw all my DVDs in a box somewhere?  They are so ugly sitting out next to the TV.

---

### Post by saheer on 2008-01-27
Try K3B.
Thank you  :D

---

### Post by gareth_005 on 2008-01-27
You may want to try this method, insert the dvd and check that it starts playing. Quit the dvd application.

In a terminal enter the following:
$ dd if=/dev/cdrom of=./mydvd.iso bs=2048
Replace /dev/cdrom with your dvd location.
This will create an iso image of the whole dvd, like a backup.

You can then play it in vlc or xine.
$ xine -pfhq -D --no-splash dvd:./mydvd.iso
or
$ xine -pfhq -D --no-splash dvd:./mydvd.iso/1.2
The first option will play the dvd from the start and show the menu.
The second option will jump to "title 1, chapter 2" (or something like that) but it will skip the menu and start the movie.

I use this method on my home server and spread the images over many drives, then I share one folder which has symlinks to all of the iso images, it works nicely.

---

### Post by afderrick on 2008-01-27
Okay, so I opened up MPlayer and just tried to play the DVD and its not even playing off the CD which might be some of my problem.  I get an error message gnome_screensaver_control() and it doesn't do anything from that point in time, what do I need to do differently?

---

### Post by benerivo on 2008-01-27
You can just copy a DVD to a .iso file on your server, and then use vlc to play it back. I don't know about the screensaver message you are getting.

EDIT: I wouldn't rip a dvd as it lowers the quality and/or takes time. Just copy the dvd to a .iso file.

---

### Post by gareth_005 on 2008-01-27
Is your dvd region code set?
Have you got all of the libdvd css/read stuff installed?
I use xine, it is easy to install using synaptic or automatix, automatix will also install the libdvd stuff.

The iso method using dd works most of the time, I have found that the new Teenage mutant ninja turtles dvd does not play from the iso file.

---

### Post by afderrick on 2008-02-02
So I tried to copy the DVD and all I got was a 3.5MB .iso file and it won't play in VLC at all no matter which way I go about it.  I also tried xine and wasn't able to get anything.  Any suggestions?

I even found a way within GUI to copy the image to a .iso and still am not able to get it to do anything outside of sit there.

---

### Post by gareth_005 on 2008-02-02
Are you able to play the dvd in xine from the dvd drive?

---

### Post by afderrick on 2008-02-02
well I am using vlc, but yes I can watch dvds without problem.

---

### Post by gareth_005 on 2008-02-02
If you used the "**dd**" method to copy the dvd to an iso file and xine or vlc can't play it I can not help you further. I can browse to the iso image with nautilus, select the iso file and choose open with vlc, the dvd plays.

If you are trying to copy a new dvd it may be a new protection scheme, maby test an older dvd.

---

### Post by TeaSwigger on 2008-02-02
> **afderrick said:**
> So I tried to copy the DVD and all I got was a 3.5MB .iso file and it won't play in VLC at all no matter which way I go about it.  I also tried xine and wasn't able to get anything.  Any suggestions?

I even found a way within GUI to copy the image to a .iso and still am not able to get it to do anything outside of sit there.

A 3.5mb file, I guarantee you, is not a copy of a DVD.

k3b makes it very easy to backup a disc onto a hard drive. There are also other apps you can find searching in Synaptic, some command line; they can be harder to learn at first but work very well.

---

### Post by afderrick on 2008-02-03
Is there any reason the file is only 3.5Mb?  Shouldn't it be much bigger than that if I am copying it to iso?

---

### Post by gsmanners on 2008-02-03
> **afderrick said:**
> I have tried k9copy and it said finished but when I went in to check it the sound was fast and the video looked garbled (probably as the same speed of playing as the sound).  I also tried using dvd::rip and it was going well until about halfway through the project and the program just quit running.

Are you able to play *that* DVD normally?

This sounds like some new form of copy protection. If dd only lets you see the production logo, then it's almost certainly protection that you're getting hung up on.

---

### Post by afderrick on 2008-02-03
I can play the DVD off CD without problem.  When I try to play the .iso in VLC is just closes on error to VLC

---

### Post by gsmanners on 2008-02-03
> **afderrick said:**
> I can play the DVD off CD...

Huh?

---

### Post by afderrick on 2008-02-04
If I put the DVD in the drive, I can play it without a problem, I just can't play the copies .iso file.

---

### Post by stooshbunutu on 2008-02-04
The best application I know and use for this purpose is [AcidRip]("http://packages.ubuntu.com/gutsy/graphics/acidrip") which is based on the mplayer and mcoder which you seem to already have. I converts the files to either .mpg or .avi format with no real loss of quality.

Hope this helps :)

---

### Post by afderrick on 2008-02-04
I will try AcidRip when I get home, so far I've not had any luck.  I momentarily tried K3B this morning before work and it wasn't finding my DVD for some reason, not sure why since I could see it anywhere else.

---

### Post by afderrick on 2008-02-04
I got k3b to work, pretty cool stuff, thanks for everyone's help.

---

### Post by stooshbunutu on 2008-02-05
If its all fine now, remember to mark your thread as solved with the thread tools mini menu near the top. I just found out about it today :)

---

### Post by afderrick on 2008-02-05
OH cool, I didn't know how to do that.

---

