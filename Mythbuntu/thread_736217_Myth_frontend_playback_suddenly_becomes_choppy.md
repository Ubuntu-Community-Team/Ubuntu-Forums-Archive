---
title: "Myth frontend playback suddenly becomes choppy"
date: 2008-03-26
forum: Mythbuntu
---

### Post by Dogbone on 2008-03-26
Am not sure if this is a Mythbuntu issue or a general hardware problem

I have a Mythfrontend on my laptop which works fine for about 30 minutes. Suddenly while watching a recording the playback becomes extremely choppy and plays only a second of video at a time. Extremely irritating

On closer inspection I notice that when I ping the backend the response time has increased from less than 1 ms  to about 600 ms.

If I disconnect the wireless connection and reconnect then the response time is back to less than 1 ms and I can watch TV again for about 30 minutes

Has anybody come across this before ?

My Backend is wired to a Wireless router and my Frontend is on a Dell d620 laptop using a 3945ABG wifi connector

Frontend and Backend are Myth 0.21

Using the same laptop but with a Windows partition I can use Mythplayer 0.5 for hours without any problem

---

### Post by funkydan2 on 2008-03-27
I think I get the same problem - though I've never checked the pings (I'll do it later tonight).

Have you tried either using a wired connection or trying the new mythtv plugin for Totem-gstreamer?  (Need to upgrade to Hardy for the second option).  Unfortunately on my laptop going wired seemed to fix the problem - until 0.21 :confused:

---

### Post by Dogbone on 2008-03-27
Thanks for the feedback.

Have tried Wired and it's fine

Am using Mythbuntu 7.10 so is that a Gutsy release ? I don't really want to go to 8.04 yet until it's GA

I was watching TV last night through the frontend and it was fine for 2 hours. Then, after watching a recording for 15-20 minutes I get the same problem

So the issue is definitely caused by watching recordings through a wireless connection

---

### Post by funkydan2 on 2008-03-27
That's interesting.  I'll try some live tv on the weekend (not that I watch live stuff normally) but it'll be intersting to test.

Tonight I tried both MythTV and Totem with the MythTV plugin on my wired network and had lots of trouble, but it seems to be quite unpredictable when the problem might start to occur.

---

