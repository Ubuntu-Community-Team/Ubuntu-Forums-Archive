---
title: "How to add a single channel?"
date: 2009-02-28
forum: Mythbuntu
---

### Post by AKADAP on 2009-02-28
How does one add a single channel in the MythTV Channel Editor?.
I can add a channel and specify a frequency, but I can't specify the stream to use.
On cable each frequency can have 3 or more channels on it. Unfortunately, while deleting encrypted channels, I accidentally deleted a non-encrypted channel. I don't know how to add it back without adding back all of the encrypted channels.

---

### Post by blackoper on 2009-03-02
it would be faster to add them all back and just delete them more carefully. I manually add channels through a mysql database administration tool and direct access to the channels area of the mythtv database.

---

### Post by AKADAP on 2009-03-02
> **blackoper said:**
> it would be faster to add them all back and just delete them more carefully. I manually add channels through a mysql database administration tool and direct access to the channels area of the mythtv database.

I did that, and it took about an hour. The channel editor is not very efficient, and there were more than 100 channels to mark as "hidden". (I marked them a hidden rather than deleting them this time).

---

### Post by utar on 2009-03-03
You can make channels hidden through mythweb in a flash.  You can also tell myth not to add encrypted channels in the first place.

---

### Post by AKADAP on 2009-03-04
> **utar said:**
> You can make channels hidden through mythweb in a flash.  You can also tell myth not to add encrypted channels in the first place.

You can make channels hidden through mythweb easily, but installing mythweb was not particularly easy (I did succeed though). I'm glad I installed it, it makes the channel setup much easier.

You can also tell myth not to add encrypted channels, but when you do, it also does not add about 1/3 of the unencrypted channels. Until this is fixed, I'll stick with adding all the channels and hiding the bad ones.

I had a data base error yesterday that prevented myth from recording, or shutting down when idle. Threads I found on line suggested that deleting all cards & video sources and re-creating them. This is what prompted me to install mythweb.

When attempting to rescan the channels, myth backend setup crashed every time It completed the scan of the ATI HD Blunder card I have. I finally gave up on a clean scan (after 3 attempts) and re-scanned without deleting the video source after a crash while scanning. This got me past the problem and appears not to have re-created the data base problem.

Anyway, after this experience I can tell you how many channels I needed to edit. There are 814 channels, of which 517 are encrypted.

Keep in mind that I had to have two copies of the video source for cable as I have two different types of tuners, and I have read that this requires a separate video source for each (bloody nuisance). I also have a separate video source for each of my antennas since they are pointed in different directions. So I have 3 unique inputs going to 5 tuners using 4 "video source"s.

---

