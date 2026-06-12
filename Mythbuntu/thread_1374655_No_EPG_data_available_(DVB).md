---
title: "No EPG data available (DVB)"
date: 2010-01-07
forum: Mythbuntu
---

### Post by mmarre on 2010-01-07
Hi all,

I have an issue with the latest Mythbuntu release and the DVB-C card TechniSat Skymaster HD2. There is no program data available (EPG) in the recording list. All other seems to work fine (live TV, recording).

Under Mythdora the problems doesn't exist.

Just one related information:

I created a channellist.conf manually and read it in. All channels was found and after that i updated the database manually with "mysql -u root -p" and "USE mythconverg; UPDATE channel SET useonairguide=1;" to enable EPG for all channels.

I have no further ideas.

Please let me know if you need further informations / logs.

Regards
Michael

---

### Post by stevanbt on 2010-01-07
Hi Michael,
It sound's like you had a similar problem to me (see [http://ubuntuforums.org/showthread.php?t=1371507]("http://ubuntuforums.org/showthread.php?t=1371507")).  I had to do a full scan (importing channel.conf or using existing transports didn't work).

Thanks, Steve.

---

### Post by mmarre on 2010-01-07
Uhm... The reason why I created a channels.conf is because of the fulls can did not work by any unknown reason. "bad parameter" ore somewhat like this is then responded. 

Seems that the problem is cheasing his own tail :-|

But I'll give a try again in 3-4 hours when I'm back home.

Thanx a lot for the hint!

Regards

Michael

---

### Post by SiHa on 2010-01-07
FWIW, I got the 'Bad Parameter' error because I was using a character that it didn't like in one of the scan options dialog.

This was for a DVB-S scan, I used a decimal point in the 'frequency' box (because the prompt was for KHz, but it **actually** wants Hz!).

---

### Post by mmarre on 2010-01-07
Yes, I was right. Every option I tried for channel scans fails, except providing a channel.conf list.

I configured the video source using EIT, and then tried to get the system scanning for channels without success. Every possible option reults in a fail.

Seems that I have to go back to mythdoa if no one have further hints -.-

Regards
Michael

---

