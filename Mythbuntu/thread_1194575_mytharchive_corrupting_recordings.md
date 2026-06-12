---
title: "mytharchive corrupting recordings"
date: 2009-06-22
forum: Mythbuntu
---

### Post by bcg30506 on 2009-06-22
I was trying to burn some recorded shows onto DVD using mytharchive, which I've done many times before in the past, but the generated files in VIDEO_TS end up corrupt.  They will play, but they have random colored "digital" blocks appearing and some DVD players freak out at some points.  This is a new problem since I installed mythbuntu 9.04.  Every DVD I made on my previous setup, (Ubuntu 8.04 + my own compile of mythtv) worked fine.  The recording files are fine and play perfectly in mythfrontend.  I've tried playing the VIDEO_TS "image" from the myth menu, from mythvideo as an ISO, burned onto a disc and played on 3 different machines, and transferring the folder structure to my Mac and playing it there.  All cases play with the same blockiness issue and severe stuttering  in some titles.  It seems mythtranscode is producing bad files?  The recordings are already mpeg-2 from a PVR150 and no commercial cuts were performed.

Anyone got any ideas?  I'm a tad frustrated that an "upgrade" loses previously working functionality.  Plus I'm filling my disk and need to archive and remove some shows.

---

### Post by bcg30506 on 2009-06-23
Ok, I have more information and think I have it narrowed down to tcrequant.  The DVD I was making was 5.1 GB so tcrequant had to scale it down to fit a standard DVD-R.  This used to work and I've even burned discs in the past with greater multipliers than that with no issues.  When I removed some shows and got the size down to 3.2GB it plays fine with no digitized colored blocks randomly appearing all over the screen.

Before removing the tcrequant step I tried with projectx instead of mythtranscode/mythreplex but got the same results.  So both of these items point squarely at tcrequant.  Again, I never had this problem in ubuntu 8.04 so it appears the newer version of tcrequant or a dependency of it has broken something.

Anyone know anything about it or how to get an older version without breaking my setup?

---

### Post by bcg30506 on 2009-06-23
Bit more info - appears it is a known issue with tcrequant and it is being deprecated.  Vamps seems like the replacement for it but may not appear to work for mytharchive jobs.  Does anyone know about this?

[http://www.gossamer-threads.com/lists/mythtv/dev/381882]("http://www.gossamer-threads.com/lists/mythtv/dev/381882")

---

### Post by bcg30506 on 2009-06-24
Did some trials and came up with a hacked solution.

First, I tried using vamps instead of tcrequant.  While manually I could run this and ended up getting decent results, trying to incorporate it into the flow of mythburn.py was beyond the scope of my efforts.  This may prove to be a good long-term solution though.

What I ended up doing was downloading the transcode deb file from the ubuntu 8.04 repository and manually extracting just the tcrequant binary from it and copying it to /usr/local/bin so it takes precedent over the installed one in /usr/bin for mythbuntu 9.04.  When I reran the archive job, it worked and the video looked great with no blocks!  So the newer release of tcrequant inside the transcode package is definitely the culprit.

---

