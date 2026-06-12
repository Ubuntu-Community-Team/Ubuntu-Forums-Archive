---
title: "Handbrake: Ripping DVD issue"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by BrandonObrien on 2007-02-04
I wanted to rip Kill Bill Volume 2 to an MP4 file on my Ubuntu box.

I typed in the following command:
handbrake -e x264 -E ac3 -2 -S 1400 -i /media/cdrom1/video_ts/ -o /media/sdb1/KillBillVol2.mp4

It started to work and I was happy, but the thing is, it encoded 2 parts. It spent about 4 hours encoding the first part and didn't even write a file anywhere. As soon as it started encoding the second part, it instantly started writing a file to the appropriate spot.

The second encoding also took about 4 hours. Is there some reason it took so long to encode the first part and it didn't even write a file?

Is there something in my settings that caused this?

Any help would be great. thanks!

---

### Post by BrandonObrien on 2007-02-05
crap, no one? :(

---

### Post by Borbus on 2008-01-23
The first pass creates a stats file which it will use to allocate bitrate during the second pass. I think handbrake puts the stats file in some temporary location which is why you can't see it. The second pass uses the source and this stats file to make the actual encode.

---

### Post by Major_Kong on 2008-02-09
There's a new gui avaliable:

[http://rippedwire.sourceforge.net/](http://rippedwire.sourceforge.net/)

[IMG]http://rippedwire.sourceforge.net/images/hbgtk-video.jpg[/IMG]

Looks promising...

Scratch that... it's outdated.

---

