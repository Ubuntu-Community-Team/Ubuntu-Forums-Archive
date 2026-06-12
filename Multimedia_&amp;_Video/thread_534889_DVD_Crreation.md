---
title: "DVD Crreation"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by xhero0 on 2007-08-25
Can anyone reccomend a decent dvd creation app.

My goal is to convert mpg/avi to a dvd format and then burn it to a dvd

I am using 7.o4 and Gnome

Thanx!


joe...

---

### Post by kyphi on 2007-08-25
Try GnomeBaker.  Look for it in the Synaptic Package Manager.  It burns CDs and DVDs.

---

### Post by xhero0 on 2007-08-25
Ok Gnomebacker seems to like to do ISO's great now I know.. but how creating a dvd with video_ts and audio_ts?

---

### Post by kyphi on 2007-08-25
I think what you are after is some sort of converter and I cannot help you with that.

---

### Post by xhero0 on 2007-08-25
Ok thanx for your time!

Ok... anyone else can help!??! :(

I just learned about nerolinux.. considering that.....

---

### Post by nalmeth on 2007-08-25
Forget about NeroLinux

If you just want a simple/stupid DVD that will work in a DVD player, install DEVEDE.

If you want to make a really nice DVD with animated menus, check out Tovid. Included when you install are tovid, and todisc.

Tovid is for converting, todisc is for making the menu and directories (VIDEO_TS)
I like to use Tovid via command-line first to get the video to MPEG2, then use the todisc GUI to make my menu. 

Don't be put off by the command-line tovid, simply go to the directory your files are in, and run the simple command:
```
cd Videos/
tovid -quality 10 -in movie.avi -dvd -ntsc -out Movie
```

This will give you a Movie.mpg file, at full possible quality. If the file is too big, simply go -quality 9, or -quality 6, etc. The -dvd and -ntsc are essential if you live in North America. Otherwise it will encode in PAL format

Then run the todisc GUI (Applications -> Sound & Video -> todisc GUI)
Add your mpg files, edit the title that will appear, change the menu title, add a background image/video, background audio clip, hit Run -> run todisc

Then you're in business! You can burn the DVD via command line or K3B

---

