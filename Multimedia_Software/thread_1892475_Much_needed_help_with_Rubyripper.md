---
title: "Much needed help with Rubyripper"
date: 2011-12-08
forum: Multimedia Software
---

### Post by minstrelstokg on 2011-12-08
Hi all,

I recently downloaded rubyripper because of its EAC-like features. Over the past couple of weeks I've been trying to noodle around with getting rubyripper to rip a few discs to add to my collection. In the midst of ripping a few CDs in particular, the program analyzes any mismatching chunks and proceeds to trial three at which point the program seems to stall and abruptly exits. 

I have used the offset list provided by rubyripper for my media device with parameters set to match all chunks twice (including erroneous) with a total of six trials for the maximum value. 

I have not set any of the parameters in TOC analysis because when I do the programs spazzes out saying that cdparanoia can not encode wav files. It then goes into some sort of loop deal between the ripping screen and the disc information screen and I end up having to exit the application.

I am growing very frustrated but I'd really like to use the EAC features. 

Here is a copy of the log file from a recent "rip."

This log is created by Rubyripper, version 0.6.1
Website: [http://code.google.com/p/rubyripper](http://code.google.com/p/rubyripper)

Cdrom player used to rip:
TSSTcorp CDDVDW SH-S222L SB01
Cdrom offset used: 6

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-wav

CDDB INFO

Artist	= Neko Case
Album	= Middle Cyclone
Year	= 2009
Genre	= Americana
Tracks	= 15 (15 selected)

01 - This Tornado Loves You
02 - The Next Time You Say Forever
03 - People Got A Lotta Nerve
04 - Polar Nettles
05 - Vengeance Is Sleeping
06 - Never Turn Your Back On Mother Earth
07 - Middle Cyclone
08 - Fever
09 - Magpie To The Morning
10 - I'm An Animal
11 - Prison Girls
12 - Don't Forget Me
13 - The Pharaohs
14 - Red Tide
15 - Neko Case / Marais La Nuit

STATUS

Starting to rip track 1, trial #1 (34 seconds)
Starting to rip track 1, trial #2 (25 seconds)
Analyzing files for mismatching chunks (0 second(s))
Every chunk matched 2 times :)
MD5 sum: 11fd522a888bbcacea24ffe669fb8f23

Starting to rip track 2, trial #1 (13 seconds)
Starting to rip track 2, trial #2 (13 seconds)
Analyzing files for mismatching chunks (0 second(s))
Every chunk matched 2 times :)
MD5 sum: 0e30f0f49887d230e2bf63794a3ab926

Starting to rip track 3, trial #1 (20 seconds)
Starting to rip track 3, trial #2 (18 seconds)
Analyzing files for mismatching chunks (22 second(s))
2 chunk(s) didn't match 2 times.
Starting to rip track 3, trial #3 (17 seconds)


Here's where the abrupt exit occurs. Please help! I've finally found the motivation to work on my music library and for me this is a major setback. My numerous searches have provided no viable solutions and are adding to my confusion. Any and all help would be much appreciated. Thanks in advance!

Also, if it's helpful, I'm running Ubuntu Studio 11.04 Natty...

J.

---

### Post by lukeiamyourfather on 2011-12-08
> **minstrelstokg said:**
> 
2 chunk(s) didn't match 2 times.


I'm not familiar with rubyripper but I've seen errors similar to that with other "secure" rippers. Try a different optical drive if one is available.

---

### Post by shantiq on 2011-12-08
hi there  minstrelstokg


it works way better if started from the command line [ for some reason from gui it often goes t*ts up]


use   ```
rrip_gui
```   and set your choices of codec etc....


then enter ```
rrip_cli
```  and follow the really straightforward instructions



i have a whole lot of info on **[lossless ripping]("http://ubuntuforums.org/showpost.php?p=9630448&postcount=26")** here for RR



ALSO  EAC works perfectly under Wine if you want to take that route.  Personally i use both...

---

### Post by minstrelstokg on 2011-12-21
Thanks for your help and I apologize for the delayed response. I had installed Wine awhile back with intentions of using EAC instead of Ruby. I'm not sure why I'd given up but I installed EAC and configured Wine this evening and had no problems at all ripping the same Cd's that were problematic with Ruby! It's also a familiar interface which makes it nicer as well.

Thanks again very much for your guidance!

---

### Post by cornelis spronk on 2012-01-04
I had problems with Rubyripper on the last tracks on my CD's. I set the offset to +600 as recommended on the offset setting chart for my model of CDROM  It worked better with 0 offset.

I then experimented by changing the offset to -300.  It worked no better.  Setting to -500 made things worse.  I dropped back to -200 and it has been working fine.

Changing the offset by progressive trials may work for you.

When next I come across difficult tracks. I will tweak the offset and hopefully find an optimum value.

---

