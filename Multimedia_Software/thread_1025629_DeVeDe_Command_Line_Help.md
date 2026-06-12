---
title: "DeVeDe Command Line Help"
date: 2008-12-30
forum: Multimedia Software
---

### Post by DieselSnorter on 2008-12-30
I use DeVeDe to convert AVIs into a DVD format ISO so I can burn them to disc, and the App works like a champ. I've noticed it pretty much uses all the system resources to do it's thing, but it never really gives me any trouble.  

I wanted to find the correct way to do this via command line so I could script converting mulitple files over night while I'm not using my PC, and possibly do more than one at a time if nice will let more than one run at a time without the two proceses bogging each other down. 

I did some searching and found this site that had step by step command line instructions:

[http://www.cyberciti.biz/tips/howto-linux-create-video-dvds.html]("http://www.cyberciti.biz/tips/howto-linux-create-video-dvds.html")

This seems to work really well until I get to the ISO creation where the following occurs:

> $ mkisofs -dvd-video -o MOVIENAME.iso /media/WD1600BEVE/Movies/MOVIENAME/
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents


Both the AUDIO_TS and VIDEO_TS directories are present.  
I'm pretty new to all this movie conversion whatnot, so I'm probably making a rookie mistake.  

Any ideas or suggestions are hugely appreciated.

---

### Post by DieselSnorter on 2008-12-30
Disregard, I think I figured it out.

---

### Post by dggoldst on 2009-09-26
Please post the solution so that others may benefit.

Thanks!

---

