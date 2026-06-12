---
title: "Copying a DVD"
date: 2011-07-15
forum: Multimedia Software
---

### Post by Dr. KillPatient on 2011-07-15
I've got a movie on DVD that I want to convert to a regular video format (avi/mp4 etc). I've been attempting to use AcidRip but the video that comes out is always much smaller and lower quality than playing it from the DVD originally. Is there any way to *exactly* copy a DVD's content to a video file?

---

### Post by Carborundum on 2011-07-15
MakeMKV. It does not transcode either video or audio, and thus there is no quality loss.

Obviously it only outputs MKV though, not MP4 or AVI.

---

### Post by andrew.46 on 2011-07-15
It is definitely not for those who like semi-automated software but you may be interested to have at least a quick look at a method that I have written up on my personal website:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

Many find this sort of method a little too painful to use but I have been ripping dvds like this for a while and results are almost always very, very good.

---

### Post by handy on 2011-07-15
I would think that you could use HandBrakeCLI & set the output size to roughly the same size as the input.

I use the following command (I keep as a ~/.bashrc alias so I don't have to reinvent the wheel :)) to rip to approx' 1GB size .mp4 files:

alias hb="echo HandBrakeCLI -t --main-feature -i /media/dvd -o NAME.HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn"
 
I made a quick & dirty how-to over here if you are interested:

[http://spiralinear.org/forum/viewtopic.php?f=17&t=21](http://spiralinear.org/forum/viewtopic.php?f=17&t=21)

---

### Post by axel206 on 2011-07-18
These should help you.

[How to rip a DVD to DivX/XviD/H264 using DVD::Rip](http://www.my-guides.net/en/content/view/136/38/)
[How to convert a video to Xvid/x264 using Avidemux](http://www.my-guides.net/en/content/view/180/26)

---

### Post by inobe on 2011-07-18
you can set the quality in most apps manually, acid tends to use lowest quality by default, you may want to mess with the settings till you get the desired quality.

you can try handbrake, or my personal fav, OGMrip [http://ogmrip.sourceforge.net/en/index.html](http://ogmrip.sourceforge.net/en/index.html)

you should consider reading here before proceeding [https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

---

