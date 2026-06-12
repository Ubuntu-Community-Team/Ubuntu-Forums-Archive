---
title: "mkisofs won't convert video files to .iso"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by Jellyffs on 2007-05-22
Hi,

I got a few dvd9 movies presented with .vob .bup and .ifo files. I'm trying to convert them to .iso as usual with mkisofs, but I get a error message that Google cannot explain:

```
jelly@superdupont:~$ mkisofs -dvd-video -o /BigMama/Movies/Movie/MyMovie.iso -J -r /BigMama/Movies/Movie
Warning: Disabling Joliet support for DVD-Video.
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Either VIDEO_TS.IFO or VIDEO_TS.VOB is not of correct size.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
jelly@superdupont:~$ 
```I made sure to add a "AUDIO_TS" folder next to the "VIDEO_TS", and also tried without "-J" and "-r", but that didn't show any difference.

The thing is, I remember getting iso from dvd9 in the past on Edgy and Dapper too... I "think" it's since I'm on Feisty that I can't anymore.

I also have: libdvdread ; libdvdplay ; libdvdnav ; and libdvdcss installed.

Ideas?

Thanks,

Alex.

---

### Post by wesswei on 2008-01-01
i'm having the EXACT same problem.

I've been trying to use k9copy on gutsy for some time now with no luck. my guess is there is a corrupt file somewhere. I don't understand dvd structures. they sure are confusing. one would think it would be as simple as an xml file and then video files, but there looks like there is no simple way of editing the chains. i'm so confused at this point, i'm trying everything to try to understand better.

any luck? or did you give up?

---

### Post by Jellyffs on 2008-01-01
No luck, so I gave up :/

---

### Post by nokie on 2008-02-10
Maybe a dumb question, but are you sure that all files have names that are capitals only? I remember having something similar before, and solved it by renaming everything to capital characters:

video_ts to VIDEO_TS
audio_ts to AUDIO_TS

and the same with the files within those directories. I think the DVD-format requires this.

just a wild guess...

---

### Post by cagljevic on 2008-02-10
I've recently been changing my ripped dvds from video_ts format to iso and found a small tutorial online mentioning how to do this, if i find it again i will link it.

anyways, this is what i did:

mkisofs -dvd-video -o /media/disk/movie/movie.iso /media/disk/movie      #movie has the video_ts and audio_ts folders

the audio_ts folders aren't required.  just make sure you run the command pointing to the parent folder where the video_ts is housed and it should work.  i didn't use any other options other than what i listed above and it worked.

one thing i did notice is if you happened edit the dvd rip with a program like dvdshrink where it can chop up the disc structure mkisofs will not cooperate, perhaps that might be what is going on here?  

mark

edit:  one thing i should note...  make sure you are using a filesystem that supports file sizes larger than 4GB, meaning, do not use fat16/fat32 because it has size limitations and depending on the dvd the resulting iso file can be larger than 4GB especially if the disc is a dual-layer (DVD9).

---

