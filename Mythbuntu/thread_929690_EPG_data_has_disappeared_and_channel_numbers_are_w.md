---
title: "EPG data has disappeared and channel numbers are wrong (xmltv/radiotimes)"
date: 2008-09-25
forum: Mythbuntu
---

### Post by bruk on 2008-09-25
Hauppage Nova-T 500 
Mythtv 8.04 + Latest branch fixes

Tried to use my mythtv box this morning, only to find all the guide data had mysteriously disappeared, something that hasn't happened in a very long time. I tried using mythfilldatabase to get the listings, with no real luck. So I tried deleting my channels and rescanning for them. Channels data seem's to have been grabbed properly from radiotimes, but the channel numbers which come from the channel scan, are now virtually all wrong (BBC One comes out as 4171 and not 1, for example). I've never had this particular problem with mythtv before, and short of manually editing channel numbers (not really acceptable, there's obviously an inherent problem), there seems to be no way for me to fix it.

From checking other posts, this could be another issue with radiotimes/xmltv, or a partially corrupted sql db (there was a suggested mysqlcheck command, but it failed on password entry, neither my sudo passwd or the myth sql db passwrd would work).

Any suggestions?

---

### Post by newlinux on 2008-09-25
You probably just had a corrupted table and didn't need to delete your channels. I'm not very familiar with non-us channel scans but maybe the proper information for channel mapping isn't being sent for some reason (happens with US QAM all th time, and I have the manually edit some channels to get the right info).It might be easiest to check on and repair your tables from mythweb (look in configuration on mythweb - it should give you a status for all your tables as well).

---

### Post by db260179 on 2008-09-25
I'm in the uk, same problem. Read my post about this issue

[http://ubuntuforums.org/showthread.php?t=914136](http://ubuntuforums.org/showthread.php?t=914136)

---

### Post by bruk on 2008-09-25
Info much appreciated db260179, and after adding/changing the script around (channel id's aren't right for radio stations, probably a freeview thing), I've got all the numbers exactly as they should be.

The actual guide data is still proving to be a problem, but I'd imagine that's just one of the many 'eccentricities' with xmltv and radio times.

For anyone else who stumbles across this post, I've added the modified script to this message that should set up all of the freeview channels in the UK as they are reported in most media.

---

### Post by db260179 on 2008-09-26
I can no longer get EPG data either. i assume they have changed the dvbstream again!

Are you getting EPG yet, leave it overnight, then post back here!

Might have to post a bug fix for mythtv

---

### Post by smbm on 2008-10-04
I'm not sure but I think I might be having this problem too.

Is this what causes the channels to be a very weird order?

Any news on any solutions?

Cheers

---

### Post by Andrew U.K. on 2008-10-05
I'm also not getting the epg data. So I'm in on this one. Just displays Unknown. Is there a more reliable way of getting it on the internet?

Cheers
Andrew

---

