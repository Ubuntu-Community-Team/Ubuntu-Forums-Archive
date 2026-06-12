---
title: "frame buffer problems with all formats: avi,mpg,wmv"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Drone4four on 2007-10-28
I don't know what causes it, but after a few hours of using Ubuntu Gutsy, wmv, avi and mpeg playback fails.  I hear sound, but I can't see the video.  All i see in my Totem media player or MPLayer is pink and yellow gibberish.  Is this a bug?  Should I submit a bug report? My current work around is to restart x w/ CTRL + ALT + Backspace.  That temporarily fixes the problem, but after a half hour of viewing media files, it's spontaneously all messed up again.

---

### Post by Drone4four on 2007-10-28
WOW: I restarted x.  I started watching some .moeg video files.  I click maximize and compiz fusion locks up.  CTRL + ALT + F1-F6 doesn't work.  Restarting x doesnt work.  I had to reboot my computer.  This is definitely a serious bug.

---

### Post by haphaeu on 2007-11-30
I have the same problem with video player... only the sound and a pink screen. I noticed the problem started when I installed the package with restricted codecs. 

First I installed Ubuntu while offline - so apt didn't install any extra packages. With the fresh installation I could see all my videos but I coudn't play any mp3 or wma files - because they are not installed by default.

After I got internet working, I installed the restricted codecs package - all fine with the mp3 and wma - but my videos stop working, all formats.

So I belive this a problem with some new decoder installed with that package - but as I'm newish with Ubuntu/linux I'm not sure how to proceed to recover the old (working) coded.

---

### Post by powerofslack on 2008-01-04
I am having the exact problem described above.  I'm running Ubuntu 7.10 gutsy AMD64, kernel 2.6.22-14-generic, gnome 2.20.1, ] with w64 codecs installed (everything through automatix), with an Asus nVidia GeForce 7300GT 256MB DVI/HDTV Silent PCI-Express Video Card (AS-73GT256) using "Nvidia accelerated graphics driver (latest cards)".  I have never had any video playback problems with this machine under 7.04 or 7.10 using the automatix supplied codecs, even when it has been up for weeks at a time without reboot.  Now, presumably due to some change or update that I made, something triggers it after a few hours up time to present that mostly pink with a little yellow and greenish boxy static picture with perfect sound, for wmv, avi, etc.  Reboot fixes it temporarily but I have number crunching things running that take a week or so per run so I'm stuck without even that half-assed fix for now.  Please let me now what's up if anyone figures this out!  thanks!

---

### Post by Nirevus on 2008-03-16
Same bug here. Was watching MPEG4's all morning absolutely fine using the default video player. Now in the evening both VLC and the default player show lots of pink pixels with the sound still clear. I've tested this on serveral video files.

---

### Post by StevenRoose3 on 2008-03-24
same problem here.
wmv mpg, avi works with vlc.

doesn't anyone know a solution?

---

### Post by markonhismobile on 2008-04-04
Getting the same here, will try a restart in a mo. I thought it might have been due to activating the "backports" updates the other morning, but I took them off again after an update from there broke Miro.

---

