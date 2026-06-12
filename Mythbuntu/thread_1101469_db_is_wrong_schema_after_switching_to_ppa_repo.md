---
title: "db is wrong schema after switching to ppa repo"
date: 2009-03-20
forum: Mythbuntu
---

### Post by aalh on 2009-03-20
Long story,
My personal Hades started when I swapped to the trunk builds. 
I lost the use of mytharchive (the only plugin I use other than mythweb).
Every time I selected mytharchive I was told that the plugin was not compiled with the same lib as mythtv and I needed to recompile it. Mytharchive, front/backend were all trunk and matched the version I saw on the repo when I browsed to it in firefox.
After over a month of patient digging for an error in my setup I found nothing and waiting for the trunk to get updated gave no joy either.

This week I finally got "help".
 It was suggested that I switch to the ppa repo. 
I did so, but now I cant even get mythbackend to start because, according to the log, the ppa version uses a different schema for the db than the trunk version. Now I have no myth at all.  please help me fix this

mythbackend.log
[http://rafb.net/p/dCxu0710.html](http://rafb.net/p/dCxu0710.html)

mythfrontend.log
[http://rafb.net/p/JKuv0A11.html](http://rafb.net/p/JKuv0A11.html)

---

### Post by aalh on 2009-03-22
UPDATE

deleted the ppa repos
re-added the trunk repo (no source repo???)

uninstalled mythtv* that came from the ppa
installed mythtv (using trunk repo)

now mythtv runs and records, but mytharchive is still telling me I compiled it with the wrong libraries
in other words, back where I started

why are there incompatible plugins posted on trunk?

I hope it takes less than 3 months to compile one, but I have been waiting almost that long

I see the version change on the trunk pkgs, but they are still incompatible. Why are the broken pkgs getting updated with other broken pkgs?
I know that trunk is bleeding edge, but I am used to devs not intentionally maintaining broken stuff. the point is to fix it, I want to help but this is very discouraging

what is going on here??????????

---

### Post by aalh on 2009-03-22
if I ever figure out how to fix this I promise to post details here, but I aint holding my breath

---

### Post by aalh on 2009-03-22
ok a helpful soul (not a dev) suggested I use mythrename.pl to fix the gibberish in the recordings dirs, now it is possible to move all my recordings to a drive and wipe the os-drive of any trunk-junk.

far from ideal as I will have a bunch of nuv's with commercials still in them. but I wont lose any recordings and hopefully there is or will be a way to clean the recordings later

so I didnt actually solve it
I found a way to work with it broken in spite of the trunk repo

---

### Post by aalh on 2009-03-29
I posted cautionary threads about the plugins in trunk 
[http://ubuntuforums.org/showthread.php?t=1103111](http://ubuntuforums.org/showthread.php?t=1103111)
and db schemas
(which is related to the former, so I link it above).
This most recent update of trunk:
mytharchive 0.21.0+trunk20282
has solved the issues, no more schema mismatches


thanks for your continued efforts on trunk, devs
especially tgm4883 and superm1 



PS
after the mythrename.pl I had to remember to clear any files I had selected in mytharchive. Although mythtv was happy with the new names, the records mytharchive used pointed to the pre-humanized files. after deleting and re-adding them all was well. I guess there is an actual table for MA instead of a query

---

