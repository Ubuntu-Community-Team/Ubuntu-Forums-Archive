---
title: "DVD Ripping"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by gogreenpower on 2007-07-04
can anyone suggest a dvd ripper and some settings to get a good quality rip?? ive tried dvd::rip and thoggen but just cant get the quality i was getting with windows dvdfab, help!!!!

---

### Post by hellmet on 2007-07-04
I'd suggest Avidemux. I cannot guide you to use it because, I myself am learning the functions of it.

---

### Post by gogreenpower on 2007-07-05
ok thanks i will give it a go,

---

### Post by Alex Fernandez on 2007-07-05
Depends what you want to do: 
- if you want a 1:1 copy, use vobcopy/dvdbackup
- if you want to just rip to seperate files use mplayer with -streamdump, ffmpeg/txextract to demux, ffmpeg/mencoder to transcode and then mplex.

This is how I rip a lossless mpg from a DVD:

```

mplayer -dvd-device <DVD-DEVICE> dvd://<TITLE> -dvdangle <ANGLE> -chapter <START CHAPTER>-<END CHAPTER> -dumpstream -dumpfile dump.vob
ffmpeg -i dump.vob -vn -acodec copy -y split.ac3
ffmpeg -i dump.vob -an -vcodec copy -y split.m2v
(if you want a different stream then use -map in:out - if you want all the streams then dont demux with ffmpeg at all - if you want to transcode then change the vcodec/acodec settings)
mplex -f 8 -o final.mpg split.m2v split.ac3

```

---

### Post by Tlon on 2007-10-28
What are my options if I want to do a 1:1 copy of the actual video, but not the extras?  I run into this problem when trying to backup DVD's that are loaded with stuff: they're bigger than your standard one-sided DVD.  But a lot of the content I really don't care to have anyway, e.g., I'd really like a lossless copy of Godfather the actual film, but I don't necessarily need the myriad interviews that come with it.  At the same time, there are some things that I *do* want to preserve, like subtitles, chapter breaks, etc.  Has anyone dealt with this problem successfully?

---

### Post by wild77 on 2007-10-28
The latest beta version of DVDFab 4.0.0.0 works well on Gutsy with Wine

check out this thread for more info 
[http://club.cdfreaks.com/f116/dvdfab-hddecrypter-linux-220283/](http://club.cdfreaks.com/f116/dvdfab-hddecrypter-linux-220283/)

---

### Post by mc4man on 2007-10-28
```
I'd really like a lossless copy of Godfather
```
In terms of that title(no structure protection or none that presents issues) I'd say K9copy would give you a reauthored - movie only quite fine.  If you don't want it to reencode adjust the target size first.
It wants to create an iso, a video_ts is stored in tmp
With some recent stuff you'll need win progs. in wine to fix and or customize

---

### Post by 50words on 2007-10-31
Is there a program in the repositories that will rip a DVD to an ISO file like DVDShrink for Windows? Or is it a two-step process, and I have to rip to a video_ts file, then create the ISO with something like DeVeDe?

---

### Post by michaelzap on 2007-11-02
> **50words said:**
> Is there a program in the repositories that will rip a DVD to an ISO file like DVDShrink for Windows? Or is it a two-step process, and I have to rip to a video_ts file, then create the ISO with something like DeVeDe?

AcidRip and K9Copy both do this, and you can also just use Nautilus to make an ISO image.

---

### Post by RTrev on 2008-02-08
> **michaelzap said:**
> AcidRip and K9Copy both do this, and you can also just use Nautilus to make an ISO image.

I've had sporadic luck with all the methods I've used.. Nautilus, dd, Brasero, etc.  9 out of 10 of my normal DVDs rip just fine to a .iso file which can be played from the hard drive using VLC.  But on the 10th ones, I can't do it with anything.  The DVD will play just fine, but the copy will get about 1.8 Megs and then die with an I/O error.

So, all but 1/10th of the DVD's I've purchased are backed up just fine, but the others can't be.. for some reason that eludes me.

What normally works fine is Brasero, or a command like this:

dd if=/dev/hda of=something.iso bs=2048

Can anyone shed any light? Thanks..

---

