---
title: "Theora vs Schroedinger"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by Angus77 on 2007-12-24
I've decided to put all my DVDs onto my hard disk (not a lot, less than 20).

I've got several hundred GB free, so I don't mind if the files are big.

So, what is your opinion?  Should I go with Ogg Theora or Schroedinger?  I have no experience with either.  Actually, I've never encoded video before.

---

### Post by hyper_ch on 2007-12-24
why not just putting an image of the dvds on the hard disk? then you'll have no quality loss at all (if you have enough disk space)

---

### Post by Angus77 on 2007-12-24
How easily can you play that?  I want to rip them so I can watch them when I want, rather than just archiving them.

And how would I go about ripping a DVD image?

---

### Post by daengbo on 2007-12-24
Schroedinger is a spec still in transition, with iffy support by GStreamer, which is what you'll be using if you go with Schroedinger.

I love OGG for its freedom, but it has quality issues when compared to other formats, specifically due to B-frames being excluded. I've been using Vorbis for my music and Theora to rip DVDs for a couple of years, but ...

I were doing it again, I'd create mkv with h.264, which are free containers and foramts. The quality of h.264 is extremely high.

---

### Post by hyper_ch on 2007-12-24
Just make an .iso file out of it and then you can mount it... depending on what you use (gnome/kde) there are even scripts that can mount .isos easily and then you just open them in your media player.

---

### Post by kpkeerthi on 2007-12-24
[How to backup a DVD]("http://gentoo-wiki.com/HOWTO_Backup_a_DVD") => Exact 1:1 copy. No quality loss (optional).
[How to rip a DVD]("http://gentoo-wiki.com/HOWTO_DVD-Ripping") => Possible shrinking with a loss in quality.

Install these using synaptic. 

If you backup your DVD as iso, using the first method above, you may [mount the iso file]("http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html") and use mplayer to play from the mounted folder. vlc can play the iso file without a need to mount it (Open url and type the path to iso as in dvd:///home/username/dvdimages/dvdimage.iso).

Hope it helps

---

### Post by Angus77 on 2007-12-24
Aren't there patent issues with h.264?  That's why I was looking into theora and schroedinger in the first place.

I'm going to see what I can do about ripping the .iso s.

Thanks for everybody's help!

---

### Post by hyper_ch on 2007-12-24
angus: those patent issues depend on where you life. In some place there are no issues at all ;)

---

### Post by Angus77 on 2007-12-24
Okay, I've been googling around, trying to find a way to rip to h264, but so far nothing I've tried works (ie x264, ffmpeg).  Any suggestions?

---

### Post by Bachstelze on 2007-12-24
Avidemux is a very intuitive and user-friendly encoder that can encode in x264 (it's similar to VirtualDub in Windows if you know that one). Not very efficient for batch processing but if you just wish to encode one video at a time, it will get the job done, and very well done.

(Moved to Multimedia & Video)

---

