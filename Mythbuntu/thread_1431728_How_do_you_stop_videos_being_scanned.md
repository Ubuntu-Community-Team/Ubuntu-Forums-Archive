---
title: "How do you stop videos being scanned?"
date: 2010-03-17
forum: Mythbuntu
---

### Post by TheCook on 2010-03-17
I have a number of videos in my collection that have their titles overwritten on a regular basis for example 'Akira' and 'Spirited Away' gets changed to some Asian symbols and or empty squares.  'The Name of the Rose' gets turned into 'Der Name Der Rose'.

I suspect there is an automatic "scan for changes" of the video files going on but I can't find where to stop it.

Any hints?

---

### Post by tgm4883 on 2010-03-17
This is a mythvideo cron job. Check in MCC and see if you have a jamu section. You should be able to disable it from there.

---

### Post by TheCook on 2010-03-17
I don't have a Jamu section in MCC.  I have checked crontab for mythtv.

I have a separate BE/FE system.  Is the mythvideo scan done by the BE or is it done by one/all of the FEs?

---

### Post by kja999 on 2010-03-17
TheCook .. I am so glad you asked this question. I keep forgetting to post it.
I have exactly the same issue.

I removed the mythvideo script from /etc/cron.hourly /etc/cron.daily folders, but each time there is an update they are re-added (I use the daily builds repo), so watch out.

In terms of solution, I would like to add that blocking/disabling jamu for certain content types would be great too .. I.e. I hate seeing fanart on tv shows, plus it spins up my NAS just to browse the recorded list now, as my videos and video fanart folder are on the NAS.

---

### Post by TheCook on 2010-03-18
Ahhhh!

I was looking up crontab to find cron jobs.  No wonder I couldn't find it.  I'll clean up my server tonight.  Thanks for the hint about updates too.

---

