---
title: "recordings with missing data files"
date: 2009-01-19
forum: Mythbuntu
---

### Post by bareflix on 2009-01-19
I have a strange thing happening on my mythtv installation. Any recording on channel 7 or 11 appears in the DB, but when I go to play it, it says the file cannot be found.

If I manually record from either of those channels, it works fine. I've looked at the logs but don't see anything reported when the recording happens.

Any suggestions as to where to look for clues? Recordings on all other channels work fine, so I think maybe something is wrong in my channel data. I upgraded the data from an older version of mythtv when I installed mythbuntu 8.10.

--
Chris

---

### Post by Vague Craig on 2009-01-20
Hi, I had similar problems with my myth box, turned out to be the DVB-t tuner not actually tuning when trying to record. Not sure why myth doesn't notice that this has happened. 
Does the tuner ever fail when you open live TV? What card are you using, does it happen on all tuners or just one?

---

### Post by UltramaticOrange on 2009-01-20
I'm guessing that Vague Craig is on the right track, here. But seeing as I've had a similar experience...

I had a problem like this when I had a bad SATA cable which prevented a hard drive (the one mounted as /var/lib/mythtv/recordings) from staying mounted. The result was that the recording would be listed in the frontend, but would error if you tried to watch the file (unless the recording happened after the failure to mount) If you're mounting one of your drives like I am (as the directory to store recordings) check to make sure that the drive is getting mounted properly. If it *is* getting mounted properly, make sure you don't get an I/O error when you try to `ls` that directory.

---

