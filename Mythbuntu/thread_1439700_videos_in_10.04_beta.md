---
title: "videos in 10.04 beta"
date: 2010-03-26
forum: Mythbuntu
---

### Post by kdx7214 on 2010-03-26
Okay, so I am able to rip dvd's now to an ISO file and they still don't show up under Watch Videos.   I decided to try an avi file and an mpg video file.  These don't show up either.

Where do I put this stuff and how do I watch them?   There is some piece missing on my setup for 10.04 right now.   I can use mplayer to view the ISO files just fine from the alternate locations and also to view both the avi and the mpg files.

Any ideas?   If nothing else, is there an mplayer command I can use that will play the ISO and also output to the Hauppage 350 card I have?

I think the real problem is that the list of videos to play never, ever shows anything - no matter what I put or where.

Thanks!

---

### Post by larsolav on 2010-03-26
For the ISOs I would follow this advice:
[http://baablogic.net/drupal/node/7](http://baablogic.net/drupal/node/7)

Myth DOES work with ISOs, just not in storage groups, and JAMU tends to undo the art-work. But if you don't put the ISOs in a storage group they play (for the most part, may have to scrub away the FBI warnings...)

Make sure you press m, and scan for changes after setting the system up as described in the link as described here: [http://www.mythtv.org/wiki/MythVideo#Scanning_for_Videos](http://www.mythtv.org/wiki/MythVideo#Scanning_for_Videos)

 _ Scanning for Videos_

When you add new videos to your storage directories, you can trigger a scan from any MythVideo view by choosing MENU->Scan For Changes.

In versions of MythTV prior to .22, it was necessary to enter the Video Manager screen to initiate a scan. This is no longer the case.

---

### Post by kdx7214 on 2010-03-26
LOL... I've been pulling my hair out for a day now because I didn't remember to scan for changes.   Oh well, my own fault :)

Thanks for the help!  Now my ISO files are playing and everything.

Thanks again!
Mike

---

### Post by larsolav on 2010-03-26
Awesome!

---

### Post by kdx7214 on 2010-03-26
One more thing... how do I put in metadata for the movies?  I used ot do this in video manager but that's gone now.

Thanks again :)
Mike

---

### Post by larsolav on 2010-03-26
> **kdx7214 said:**
> One more thing... how do I put in metadata for the movies?  I used ot do this in video manager but that's gone now.

Thanks again :)
Mike

Instead of m, you press i, that should bring up a pop-up menu with metadata option in it. Be prepared that the downloaded art-work may first show up, but then after JAMU has run it may not show up...

---

### Post by iamlindoro on 2010-03-26
> **larsolav said:**
> Instead of m, you press i, that should bring up a pop-up menu with metadata option in it. Be prepared that the downloaded art-work may first show up, but then after JAMU has run it may not show up...

Only if you are using Ubuntu 9.10, which didn't contain .22 at all, but a prerelease.  All *released* versions of Jamu/Myth work great and won't break your metadata.  Suggest you install the autobuild repository and get to a version of myth that's meant to be public.  ;)

---

### Post by larsolav on 2010-03-26
> **iamlindoro said:**
> Only if you are using Ubuntu 9.10, which didn't contain .22 at all, but a prerelease.  All *released* versions of Jamu/Myth work great and won't break your metadata.  Suggest you install the autobuild repository and get to a version of myth that's meant to be public.  ;)

Sweet, I actually have activated the autobuild (if this is what you mean: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)), but have not clicked on the update button for a few weeks. So if I do click on the update now, JAMU won't mess with ISO art? Awesome! and thanks iamlindoro!

---

### Post by larsolav on 2010-05-16
> **iamlindoro said:**
> Only if you are using Ubuntu 9.10, which didn't contain .22 at all, but a prerelease.  All *released* versions of Jamu/Myth work great and won't break your metadata.  Suggest you install the autobuild repository and get to a version of myth that's meant to be public.  ;)

Okay, now I have fresh install of 10.04 with autobuilds activated, so now I have 0.23 installed, and still after JAMU runs the artwork for the ISOs no longer show up...

---

### Post by Senkoboy on 2010-05-16
> **kdx7214 said:**
> LOL... I've been pulling my hair out for a day now because I didn't remember to scan for changes.  


Me too!

---

