---
title: "dvd::rip fails with ISO"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by anjilslaire on 2006-11-05
Hi all,

I'm looking to rip a dvd iso to avi.

Trying dvd::rip, I can select the ISO, in the create project section, but it errors out on the "rip title" tab because it's trying to read the dvd contects, looking for the TOC.

If the program lets me load an iso, why does it force trying to read from the dvd drive?

When I try using k9copy, it works fine, but it won't encode to the size I specify in the settings, ie. 1400 (just personal preference. This size lets me burn a 3 movie trilogy to 1 dvd for my divx/xvid standalone player). The original 4.7gb movie ends up at about 793mb. ](*,) 

I usually do this with autogk in Windows, but I'm looking for more ways to do this from my Kubuntu partion.

What do others use to re-encode DVDs/ISOs to .avi?

Thanks

---

### Post by kinkdxm on 2007-06-03
looking for the same answer a year later that is....

---

### Post by ahaslam on 2007-06-03
> What do others use to re-encode DVDs/ISOs to .avi?
I use mplayer (mencoder) with lame. I find the following to produce a very high quality output:
```
# remove conflicting files
rm -f divx2pass.log frameno.avi

# rip audio track (bitrate: 160)
mencoder dvd://***TITLE*** -oac mp3lame \
-lameopts abr:br=160 -ovc frameno -o frameno.avi

# video track (pass: 1, bitrate: 1440)
mencoder dvd://***TITLE*** -oac copy -ovc xvid \
-xvidencopts pass=1:chroma_opt:vhq=4:max_overflow_improvement=15:turbo \
-vop scale -zoom -xy 720 -o /dev/null

# video track (pass: 2, bitrate: 1440)
mencoder dvd://***TITLE*** -oac copy -ovc xvid \
-xvidencopts pass=2:bitrate=1440:chroma_opt:vhq=4:max_overflow_improvement=15:turbo \
-vop scale -zoom -xy 720 -o ***FILENAME***.avi

# clean up
rm -f divx2pass.log frameno.avi

# done
```

An average 90min film usually weighs in at just over a gig, though this varies widely due to overflow improvement & the films aspect ratio). You'll certainly get a trilogy on one dvd at this level & the quality loss will be negligible, the only cost is time ;)

This got me started: [http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

> looking for the same answer a year later that is....

Mount the iso, open mplayer & go to preferences > misc > dvd device & change the line to represent your mount point.

Hope it's of some use ;)

---

### Post by teloschistes on 2007-09-13
I had the same problem -- dvd::rip failed reading the toc from a dvd image on the hard drive.  On a whim, I decided to rename the directory containing the image so that there were no spaces in its name and....   drumroll....  it works!

---

### Post by bryncoles on 2008-01-11
please forgive me for jumping in half cocked.... i'm still a bit green around the gills, but would k3b not handle dvd iso files? it has an option on its startup screen....

---

