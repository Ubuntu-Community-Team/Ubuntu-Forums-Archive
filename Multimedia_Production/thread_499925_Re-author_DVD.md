---
title: "Re-author DVD"
date: 2007-07-13
forum: Multimedia Production
---

### Post by thebucksstop on 2007-07-13
OK, I've got a bunch of clips on several DVDs - showreels and the like, that I'd like to re-author onto one single DVD. Does anyone know how I can go about doing this, without converting them to avi or mov, and then re-converting and authoring from that?

Thanks!

---

### Post by lisati on 2007-07-13
DVD-shrink can do that. The only catch is that it runs under Windoze, so you'll probably have to get it working with "Wine" or similar.

---

### Post by thebucksstop on 2007-07-13
Cheers, I know DVD-Shrink can do that - I've had trouble getting it working properly under Wine for quite a while. I can run it fine, but as soon as I try and do anything in it, it'll hang and I'll have to Force-Quit. do you know of any fixes for that, or any native programs that'll do what I want?

---

### Post by vanadium on 2007-07-13
If the DVDs are not encrypted, you can open de VOB video files on the DVD using Avidemux. In Avidemux, you select the clip you want, then save it in a DVD compliant mpg container file (Audio: copy, Video: copy, Format: MPEG PS A+V). This does not reprocess your streams: the original wuality is preserved.

This way, you'll end up with your clips in DVD compliant mpeg format. These must be authored to a DVD. As of yet, I have only experience with the command line tool dvdauthor. 

dvdauthor -o <outputdir> -x <xlm-config-file>

The <outputdir> states where your VIDEO_TS and AUDIO_TS will be located. The <xlm-config-file> describes the layout of your disk. On [http://dvdauthor.sourceforge.net/doc/index.html](http://dvdauthor.sourceforge.net/doc/index.html) there are some examples for simple layouts.

Finally you will need to write the authored DVD to disk. First create an iso

mkisofs -dvd-video -o<nameofiso.iso> <dirwhereyourVIDEO_TSresides>

This results in an iso that can be written using your favourite DVD burning app. For example

dvdrecord speed=2 -dao dev=1,0,0 <nameofiso.iso>

---

### Post by thebucksstop on 2007-07-13
Thanks vanadium, seems pretty straightforward.

I've actually got the .vob, .ifo, .bup files sitting on a hard drive at the moment - presumably I can work off this in Avidemux just as easily as if straight from a DVD.
To run through the rest of your suggestion, basically it is:
1) Stick the DVD clips into an MPEG wrapper using Avidemux
2) Use these clips to create a "DVD" on the hard disk using relevant authoring software (e.g. dvdauthor)
3) Turn this "DVD" into an image using mkisofs

Presumably I can use any DVD authoring software, e.g. DeVeDe or QDVDAuthor, and take it from there?

There's no way you're aware of to skip the MPEG wrapper step, and just work straight from the original DVD files?

Cheers
C

---

### Post by vanadium on 2007-07-13
You have got it right. My Linux video experience is still limited, but indeed, it should be possible to author your DVD from appropriate mpegs using DeVeDe or QDVDAuthor. One feature of DeVeDe would be that it can converts video streams to DVD compliant mpegs, but you do not need that feature (should not do that) as you are already working with DVD video. If you use DeVeDe, make sure it does not transcode.

Working straight with the original DVD video would imply that you could cut the VOB files and use these directly to author the new DVD. No, I am not aware of this possibility.

---

### Post by thebucksstop on 2007-07-13
Shame I can't work directly from the VOBs, but I guess that's DVD structure for you. At least there's one way to do it.

Thanks for your help, I'll post back if I can't get it working.

---

### Post by rovernaut on 2007-07-13
> **lisati said:**
> DVD-shrink can do that. The only catch is that it runs under Windoze, so you'll probably have to get it working with "Wine" or similar.

There is xDVDSHRINK in Automatix.

---

