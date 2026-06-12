---
title: "Rip DVD to a single VOB"
date: 2010-08-04
forum: Multimedia Software
---

### Post by summersab on 2010-08-04
So, I'm trying to rip a bunch of DVDs to my HTPC. I'm a bit of a quality fiend, and since I have 2TB of hard drive space, I want to rip straight to raw VOB files (that, and it's WAY faster than transcoding). So far, I've tried several methods:

vobcopy -l -t movie

This DOES create a single file. However, when it is played, the seek is limited to the length of the first VOB file. For instance, one of my movies starts with an 8 second VOB followed by 4 other larger files. When playing, I can only seek within that 8 seconds.

dvdcopy and cat/mpgcat/vobcat

Same issues. Using cat gives seeking issues - limited to the first VOB's length. mpgcat complains that the audio tracks of each VOBs on the disc are of different bitrates, and I have to force the rip. The completed file once again has seek issues.

Any ideas? I'd LIKE to do this from the command line. Also, I am actually ripping ISOs. I originally ripped my DVDs to my drive as complete images, but now I just want the main feature. So, if you have any better ideas with dealing with the raw files, that would be better.

Thanks!

---

### Post by summersab on 2010-08-08
Is it poor taste to bump your own thread? Bump.

---

### Post by dv3500ea on 2010-08-08
You could use [acidrip]("apt:acidrip") with an audio codec of pcm and a video codec of raw (both meaning uncompressed).

---

### Post by summersab on 2010-08-08
I thought about that and other programs like Handbrake and DVD::RIP, but if I use those, aren't I still transcoding? Wouldn't ripping to PCM yield a bigger file rip (sorta like going from mp3 to wav)? I know doing raw wouldn't.

---

### Post by dv3500ea on 2010-08-08
[PCM]("http://en.wikipedia.org/wiki/Pulse-code_modulation") is the standard audio format used for DVDs and is uncompressed. I don't think it should create a bigger file.

---

### Post by rubylaser on 2010-08-08
I'd just use K9Copy ([http://k9copy.sourceforge.net/]("http://k9copy.sourceforge.net/")) and rip to an iso.  That will give you everything in 1 file and not require transcoding.  Just an FYI, I started out by making isos, but now I transcode all my files.  Saving raw ISOs eats up alot of hard drive space in a hurry, and an encoded file with good x264 settings will not look any different to your eyes, and be much smaller.

Hope that helps.

---

### Post by summersab on 2010-08-08
> **rubylaser said:**
> I'd just use K9Copy ([http://k9copy.sourceforge.net/]("http://k9copy.sourceforge.net/")) and rip to an iso.  That will give you everything in 1 file and not require transcoding.  Just an FYI, I started out by making isos, but now I transcode all my files.  Saving raw ISOs eats up alot of hard drive space in a hurry, and an encoded file with good x264 settings will not look any different to your eyes, and be much smaller.

Hope that helps.

Well, the easiest way to rip to ISO is to just right click on the desktop icon and select Copy Disc. That's what I did for my entire DVD library. But, I realized that I seldom watch special features, and menus are annoying, so I wanted to make them straight VOBs (best possible quality) of the main feature. x264 is great, but I'd prefer VOB. I'll give AcidRip a shot, but I wish there were a simple command line way to do this that didn't throw the seek track to pot. Then, I could just script the process and not have to do tedious point-and-click.

Thanks for all your help!

---

