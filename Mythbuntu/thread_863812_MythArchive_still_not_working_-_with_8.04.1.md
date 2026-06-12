---
title: "MythArchive still not working - with 8.04.1"
date: 2008-07-18
forum: Mythbuntu
---

### Post by agamotto on 2008-07-18
I have been trolling the posts in this forum and tried a fix for the infamous "MythArchive won't burn discs" issue based upon removing the .ICEauthority file.

After upgrading my system from 7.10 to 8.04.1, things work quite well, save for the fact that I now can't burn anything to disc, due to the script/program not being able to find 'dev/dvd,' despite the fact that VLC, Mplayer, and K3b can all find it, with no trouble.  I am not completely sure, but I think that is has something to do with the Python script that tells it when/how to burn the disc, as everything runs fine until the actual burn process.

Anyone have clues as to why this is still a problem with 8.04.1?

:confused:

---

### Post by laga on 2008-07-19
Can you post log files?

---

### Post by agamotto on 2008-07-20
> **laga said:**
> Can you post log files?


Sure, what precise names/locations am I looking for?  I get to choose all of the options, but the whole thing clogs at the actual time to burn the DVD, so I am not sure what files would be of help.

---

### Post by db260179 on 2008-07-21
Specify the drive as /dev/scd0 not /dev/dvd - should work then.

> **agamotto said:**
> 
After upgrading my system from 7.10 to 8.04.1, things work quite well, save for the fact that I now can't burn anything to disc, due to the script/program not being able to find 'dev/dvd,' despite the fact that VLC, Mplayer, and K3b can all find it, with no trouble.  I am not completely sure, but I think that is has something to do with the Python script that tells it when/how to burn the disc, as everything runs fine until the actual burn process.

Anyone have clues as to why this is still a problem with 8.04.1?

:confused:

---

### Post by nickrout on 2008-07-22
log files are somewhere under /var/lib/mytharchive - pretty easy to find after you navigate to that point (sorry don't have my mythbox in front of me at present).

---

### Post by agamotto on 2008-07-29
> **nickrout said:**
> log files are somewhere under /var/lib/mytharchive - pretty easy to find after you navigate to that point (sorry don't have my mythbox in front of me at present).

Nope.  I tried finding the files there, and I have nothing mytharchive in var/lib/   I tried looking in MythDVD, nothing I recognized.  I also tried the 'dev/scd0' from above with no change other than it not being able to find 'dev/scd0.'


I really don't want to go back to 7.10 again.... sheesh.

---

### Post by laga on 2008-07-29
Logs can be found in your temporary directory for Mytharchive. You must have set that yourself as it's broken in 8.04, unfortunately :)

---

### Post by nickrout on 2008-07-29
> **laga said:**
> Logs can be found in your temporary directory for Mytharchive. You must have set that yourself as it's broken in 8.04, unfortunately :)

I had to make the directories for mytharchive, it is stuffed otherwise in mythbuntu 8.04.

---

### Post by agamotto on 2008-08-02
Ok, all of my Mytharcive stuff is in /tmp/, and there is a dir for gconfd-agamotto, orbit-agamotto, keyring-******, and mythtv_ddp_*****.  I looked in those and nothing with a name that I recognise.  Oh well, I will just move the few episodes of the Doctor over to my main system and burn them to DVD from that, and just reinstall 7.10 sometime alter this week.

Thanks to everyone for all the help, but I am sufficiently pissed to go back to what worked before.  Ta

---

### Post by agamotto on 2008-08-09
Well, I went back to 7.10 now that Doctor Who is done for the season.  Everything works just fine, save for the fact that Miro doesn't want to behave, but I can deal with that.  I just run Miro on my main box, put the videos on a stick, and play them on the telly from VLC.  Very flexible program!

---

