---
title: "[SOLVED] Burn DVD from VIDEO_TS or .avi"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by altonbr on 2007-01-05
I've read a lot of threads on encoding and ripping DVD's using XviD and A3C (close to the staples of .avi files at the moment) but if I'm using dvd::rip or acidrip or DVDShrink, what I'm curious about is how to actually burn the files back onto DVD. What ever happened to copying DVDs on the fly, or to the hard drive, then back to a blank DVD?

Everyone seems to be obsessed with high-quality .avi files, but I still want them on my DVD player. If I have Anchorman, and I want my sister to have a copy, I use dvd::rip to rip the DVD right? Then I use K3B to burn the .VOB files? The .VOB files always seem to be over 4.4GB. Then what about audio?

And what about an .avi file? How do I get that onto DVD? I think using a program like Adobe Premiere would be overkill would it not? I had a grasp on how to do a lot of this stuff when burning VCD's were all the rage, but now I'm at a loss, especially switching from Nero to a plethora of Linux equivalents.

I'll continue researching VIDEO_TS and AUDIO_TS folders and the files that are supposed to be inside, but any help you can lend would be greatly appreciated. Thanks.

---

### Post by pseudonym on 2007-01-05
> **altonbr said:**
> I've read a lot of threads on encoding and ripping DVD's using XviD and A3C (close to the staples of .avi files at the moment) but if I'm using dvd::rip or acidrip or DVDShrink, what I'm curious about is how to actually burn the files back onto DVD. What ever happened to copying DVDs on the fly, or to the hard drive, then back to a blank DVD?
Hi, I thought that's what these ripping programs do? That is - rip, cache to disk, burn to blank dvd. Unless I misunderstood your question...

> **altonbr said:**
> Everyone seems to be obsessed with high-quality .avi files, but I still want them on my DVD player. If I have Anchorman, and I want my sister to have a copy, I use dvd::rip to rip the DVD right? Then I use K3B to burn the .VOB files? The .VOB files always seem to be over 4.4GB. Then what about audio?
The program I've used for this task is [k9copy]("http://k9copy.sourceforge.net/"), which is in the Ubuntu repositories. You just pick your output media (DVD, DL-DVD, .iso image) and it does the rest. I think you can do the same in all the other programs you mentioned.

> **altonbr said:**
> And what about an .avi file? How do I get that onto DVD? I think using a program like Adobe Premiere would be overkill would it not? I had a grasp on how to do a lot of this stuff when burning VCD's were all the rage, but now I'm at a loss, especially switching from Nero to a plethora of Linux equivalents.
You cannot burn a .avi to DVD, unless you're doing so as a data-DVD. For DVD video, your input source *must* be in compliant .mpeg-type format. Most commonly this is mpeg2, but these days many people also use divx if their player supports it.

If you have .avi files you will need to re-encode them to a DVD compatible format. Mencoder is a good tool for this but it's hard to use. For a good list of other suiatble apps, look [here]("http://forum.doom9.org/forumdisplay.php?f=63"). Many of these are available in the Ubuntu repositories.

> **altonbr said:**
> I'll continue researching VIDEO_TS and AUDIO_TS folders and the files that are supposed to be inside, but any help you can lend would be greatly appreciated. Thanks.
I don't think there's supposed to be anything in an AUDIO_TS folder. It's just a remnant from the early days of DVD. These days, everything is included in the .vobs inside the VIDEO_TS folder.

For questions about the DVD format, try [here]("http://www.dvddemystified.com/"). 

HTH :)

---

### Post by Foxblood on 2007-01-07
Thanks, I wasted an enormous amount of time trying to get this information. Kudos to you!!!

---

### Post by rocknrolf77 on 2007-01-07
You can use devede to create dvd's form avi's. It's in the repos. At least in edgy. Or you can get it from [www.getdeb.net](www.getdeb.net)

---

### Post by altonbr on 2007-01-08
That's perfect. I'm using K9Copy to create an ISO file and GnomeBaker or K3B to burn the ISO. It seems to crash if I try to burn it through K9Copy, so that's why I create ISO's. Thanks for the information.

---

### Post by breaking on 2008-02-24
> **altonbr said:**
> That's perfect. I'm using K9Copy to create an ISO file and GnomeBaker or K3B to burn the ISO. It seems to crash if I try to burn it through K9Copy, so that's why I create ISO's. Thanks for the information.

Yup, that's the way to do it!  Took me a while of searching around to figure this out.

I personally use devede ("dee-vee-dee") to do the encoding.  It's in the repositories, and it has options to specify region, audio and video rates, size, etc.  Very simple to use, and very effective (not to mention a nice GUI).  Just bear in mind transcoding an .avi file can take *quite* a long time, so don't expect to have your movie on the fly!

---

### Post by drvid on 2008-03-06
[DVD Shrink]("http://www.dvdshrink.org/") worked great for me with Wine!

K9Copy seemed retarded to me and besides, who really wants KDE apps in their GNOME.

:P

---

