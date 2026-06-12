---
title: "can't make cropdetect work alright for mencoder"
date: 2009-10-16
forum: Multimedia Software
---

### Post by plh on 2009-10-16
Hello,

I'm in trouble with mencoder: exceptionaly, it did not detect the correct scale/crop for a movie I ripped., and I get enormous up/down/left/right black borders, especially when I put the video in full screen :-(. Moreover the video appears to be in 5/4 format:

-------
Video
ID                               : 0
Format                           : MPEG-4 Visual
Format profile                   : AdvancedSimple@L5
Format settings, BVOP            : Yes
Format settings, QPel            : No
Format settings, GMC             : No warppoints
Format settings, Matrix          : Default (H.263)
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 2h 1mn
Bit rate                         : 869 Kbps
Width                            : 720 pixels
Height                           : 576 pixels
Display aspect ratio             : 5:4
Frame rate                       : 25.000 fps
Standard                         : PAL
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.084
Stream size                      : 758 MiB (87%)
Writing library                  : XviD 1.1.2 (UTC 2006-11-01)

-------

Of course when I look at it, it is clearly not the good scale, closer to a classical 16/9.


using cropdetect option I get " -vf crop=704:304:8:136", but re-running mencoder with -ovc copy, -oac copy and this crop option does not change anything.

ANy idea to help me get the correct final video aspect?

Thanks in advance!

---

### Post by andrew.46 on 2009-10-18
Hi plh,

> **plh said:**
> using cropdetect option I get " -vf crop=704:304:8:136", but re-running mencoder with -ovc copy, -oac copy and this crop option does not change anything.

Does your *original* movie display correctly when you run it with the cropping parameters? For example this:
```

mplayer -vf rectangle=704:304:8:136 ***[COLOR="Red"]my_original_file.avi[/COLOR]***
``` 

would normally give a good idea of what the cropping *should* do to the original movie file.

All the best,

Andrew

---

### Post by plh on 2009-10-31
Hi Andrew,

Thanks for replying, and sorry for being late to answer, I've been away for a while...
The answer is yes, the original movie displays correctly with these values...

Does it give you  a hint?

Thanks again anyway!

---

### Post by andrew.46 on 2009-11-01
Hi plh,

Could you then simply re-encode the *original* movie using the cropping parameters that worked successfully with MPlayer? I suspect I am missing your actual sequence of encoding here, for which my apologies :(.

Andrew

---

### Post by plh on 2009-11-02
Hi,

That's what I did, but it did not change anything in the final video.

Maybe the "-ovc copy" option prevents any changing of the video part, whatever the other encoding options? 
What's your opinion?

---

### Post by benow on 2010-12-11
Yeah, this is an old thread but just in case... you can't crop to a file without rencoding.  This is due to the alteration of the video bits.  When cropping live video with -vf the rest is not displayed (but still in the stream), when cropping to a file, the cropped portion must be removed from the output.  This is not possible without re-encoding.  Play back with the saved crop settings, or re-encode and loose fidelity.

---

### Post by plh on 2011-03-07
ok thanks benow,
that's what I thought... I switched to another encoder meanwhile, but thx again anyway !

---

