---
title: "Help using composite input manually"
date: 2011-06-06
forum: Mythbuntu
---

### Post by bcg30506 on 2011-06-06
I know there are other ways to do this, but none are as convenient or simple for non-techies as being able to use MythTV, so I'm hoping I can.

I have old VHS tapes I'd like to digitize into MythTV using my HVR-1950's composite inputs.  I've added a fake channel for it in mythtv-setup, but when I try to view Live TV on it I just see black, and when I try and manually schedule a recording to channel 999 and tell it to use my Aux input source, the scheduler says "No Listing".

So then I gave it an xmltvid of another channel so it had fake listings, then tried to program it for one of the shows, all the while playing the VCR tape, but that did not work either.

What am I missing?  Is there a way to do this with mythtv without resorting to command lines and video editors?  It would be great if I could record a manual "show" with mythtv from my VCR then use the Edit Recording function to clean it up with cutlists and archive it.

---

### Post by Senkoboy on 2011-06-08
What you are trying to do will work. I have done the same thing with a PVR150.  Make sure it is set up correctly in the back end.  

[http://ubuntuforums.org/showthread.php?t=718350]("http://ubuntuforums.org/showthread.php?t=718350")   

You should be able to see your VCR when you tune to the fake channel you created.  If that works you can use manual record to record our tapes.

---

### Post by bcg30506 on 2011-06-08
Okay, I think it is working as far as I can tell now without negatively affecting our normal TV watching/recording from the other cable sources.

I have no idea what I did differently except I manually stopped the backend and edited all the necessary tables in mysql instead of using mythtv-setup.  It looks pretty much the same but now works, whereas after doing it with the setup GUI, it would not use the composite inputs.

I'm running a manually scheduled recording overnight to see if all goes well, but live TV on it worked when I just set it up and tried.  If it is okay in the morning, I'll post back how the tables look.

---

### Post by bcg30506 on 2011-06-09
Believe I figured it out.  I had failed to add a 2nd capture card for the HVR-1950's composite input.  Instead, I only added an input connection for the composite on the same card entry (even though it is the same physical device).  For some reason, mythtv requires both a card and connection added for the same hardware unit for this to work.  Does that make sense?

I'm pasting the mysqldumps below of the capturecard & cardinput tables for both what wasn't working and what does.

failed capturecard table:
```
INSERT INTO `capturecard` VALUES
(1,'1017F365-0',NULL,NULL,'HDHOMERUN','MPEG2TS',NULL,'mythbox',0,0,1,0,0,NULL,0,NULL,0,1000,3000,0,0,0,0,0,NULL,1),
(3,'1017F365-1',NULL,NULL,'HDHOMERUN','MPEG2TS',NULL,'mythbox',0,0,1,0,0,NULL,0,NULL,0,1000,3000,0,0,0,0,0,NULL,1),
(5,'/dev/video2','ALSA:default',NULL,'MPEG','television',0,'mythbox',0,0,1,0,0,NULL,0,NULL,0,1000,3000,0,0,0,0,0,NULL,1);

```
working capturecard table:
```
INSERT INTO `capturecard` VALUES 
(1,'1017F365-0',NULL,NULL,'HDHOMERUN','MPEG2TS',NULL,'mythbox',0,0,1,0,0,NULL,0,NULL,0,1000,3000,0,0,0,0,0,NULL,1),
(2,'1017F365-1',NULL,NULL,'HDHOMERUN','MPEG2TS',NULL,'mythbox',0,0,1,0,0,NULL,0,NULL,0,1000,3000,0,0,0,0,0,NULL,1),
(3,'/dev/video2','ALSA:default',NULL,'MPEG','television',0,'mythbox',0,0,1,0,0,NULL,0,NULL,0,1000,3000,0,0,0,0,0,NULL,1),
(4,'/dev/video2','ALSA:default',NULL,'MPEG','composite',0,'mythbox',0,0,1,0,0,NULL,0,NULL,0,1000,3000,0,0,0,0,0,NULL,1);

```
failed cardinput table:
```
INSERT INTO `cardinput` VALUES 
(1,1,3,'MPEG2TS',NULL,NULL,'709','HD QAM 1',0,0,2),
(2,3,3,'MPEG2TS',NULL,NULL,'11.2','HD QAM 2',0,0,2),
(3,5,1,'television',NULL,NULL,'46','Analog Cable',0,0,0),
(4,5,4,'composite','/bin/true',NULL,'999','Aux Inputs',0,0,0);

```
working cardinput table:
```
INSERT INTO `cardinput` VALUES 
(1,1,3,'MPEG2TS',NULL,NULL,'709','HD QAM 1',0,0,2),
(2,2,3,'MPEG2TS',NULL,NULL,'11.2','HD QAM 2',0,0,2),
(4,3,1,'television',NULL,NULL,'46','Analog Cable',0,0,0),
(3,4,4,'composite','/bin/true',NULL,'999','Aux',0,0,0);

```

---

