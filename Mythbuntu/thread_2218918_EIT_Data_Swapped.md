---
title: "EIT Data Swapped"
date: 2014-04-22
forum: Mythbuntu
---

### Post by nunya01 on 2014-04-22
I've tried using the search features of this forum, but I'm not getting any recent hits on this subject.
My EIT (EPG) program information is wrong about 50% of the time. It seems to get swapped with other programs (mixed up). Google searches tell me this is a common problem, however I have been unable to find a method that works with Mythbuntu.
The "kicker" is this: It seems like the EPG starts out OK after a fresh grab, but somehow gets corrupted as time goes by.

12.04.4 LTS, MythTV .27, HDHomerun w/ OTA antenna

I did find this: [https://code.mythtv.org/trac/ticket/11739](https://code.mythtv.org/trac/ticket/11739) and this [http://www.mythtv.org/wiki/EIT](http://www.mythtv.org/wiki/EIT)
but since I use Mythbuntu and did not compile from source, I can't figure out how to fix it. I am NOT a Linux expert or even proficient by any means.

Please do not suggest paid subscription services. I know they work, but I want to use the free OTA guide.
Thanks

---

### Post by blm-ubunet on 2014-04-22
DVB or ASTC ?

EIT & EPG (data streams in DVB) are not the same thing.

In some parts of the world EIT data is just "now + 2 hrs" &/or notoriously bad.
 
MythTV does not support smart integration of EIT over the top of EPG (from internal or external source).
MythTV does not directly support extraction of EPG data from DVB.

You say "EPG starts out OK after a fresh grab..." which suggests running grabber script (xmltv) for EPG source.
That source could be OTA EPG.

Your symptoms sounds as if good EPG is being slowly overwritten by bad EIT data.
Try disabling EIT scanning.

---

