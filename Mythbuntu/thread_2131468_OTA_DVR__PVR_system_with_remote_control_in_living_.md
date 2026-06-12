---
title: "OTA DVR / PVR system with remote control in living room"
date: 2013-04-01
forum: Mythbuntu
---

### Post by albertkao on 2013-04-01
My HDTV has an ATSC OTA tuner which receives TV signals from an OTA antenna.
I like to build a PVR system in my living room which will record the OTA TV programs from a TV program guide with remote control.
The PVR system should be quiet and use little power.
Do I need an additional ATSC OTA tuner so that I can watch one channel while recording another channel?
Which hardwares should I get?
I google and wonder whether ZOTAC Mini-PC and HDHomeRun Digital Tuners are good choices for me.
Do anyone use them with the latest Mythbuntu 12.04 Precise Pangolin (with MythTV .25) ?

---

### Post by jlp_engineer on 2013-04-05
I have been using a Zotac MAG as a front-end for a while and it works well for me.  I don't know how well it would work as a combined front-end, back-end, however, since the processors on those little PC's are limited.  I would think that if you got one that had a dual core CPU, with hyper-threading, and you connected an external drive to store programs, DVD's, etc., that you may be able to make it work.  Particularly since the tuner will be networked to the mini-PC and digital recordings would not have to be processed when they are recorded.  Only when they are watched...but the VDPAU decoder (assuming you get a Zotac with Nvidia graphics) should be able to handle most anything you can through at it.  The only issues I have seen are when I try fancy graphics with the program guide with live TV.  I think that is a little too much for it (get skips with audio when thumbing through the giude).

Good luck - let us know how it goes.

---

### Post by albertkao on 2013-04-06
> **jlp_engineer said:**
> I have been using a Zotac MAG as a front-end for a while and it works well for me.  I don't know how well it would work as a combined front-end, back-end, however, since the processors on those little PC's are limited.  I would think that if you got one that had a dual core CPU, with hyper-threading, and you connected an external drive to store programs, DVD's, etc., that you may be able to make it work.  Particularly since the tuner will be networked to the mini-PC and digital recordings would not have to be processed when they are recorded.  Only when they are watched...but the VDPAU decoder (assuming you get a Zotac with Nvidia graphics) should be able to handle most anything you can through at it.  The only issues I have seen are when I try fancy graphics with the program guide with live TV.  I think that is a little too much for it (get skips with audio when thumbing through the giude).

Good luck - let us know how it goes.

I have an additional requirement:
Watching internet video such as Youtube.
How does it affect me (besides getting a powerful dual core CPU, with hyper-threading)?

---

### Post by jlp_engineer on 2013-04-08
> **albertkao said:**
> I have an additional requirement:
Watching internet video such as Youtube.
How does it affect me (besides getting a powerful dual core CPU, with hyper-threading)?

I don't believe that this would be a problem.  Even the lower performance Atom processors can play YouTube videos.  As long as there is support for the video acceleration, such as on the ION or ION2 equipped units, then you should have no issues.  There may be a few HD videos encoded that may show some issues when playing, but then most of the content is not HD 1080p, so no worries.

---

