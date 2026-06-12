---
title: "swap IDE for SATA DVD, now no rip"
date: 2008-04-02
forum: Mythbuntu
---

### Post by knathraak on 2008-04-02
HI,  I just swapped my IDE DVD drive for a SATA DVD-RW, and now I can no longer rip DVDs.  The drive seems to work fine.  When I put in a disc, it gets mounted automatically, and I can even play DVDs in MythTV.  Of course, I had to set the dvd device to /dev/scd0 in the setup.   When I chose rip/transcode, it just sits there waiting for a DVD.  Is there anything else I need to do to make it work?

Thanks

---

### Post by foxbuntu on 2008-04-03
> **knathraak said:**
> HI,  I just swapped my IDE DVD drive for a SATA DVD-RW, and now I can no longer rip DVDs.  The drive seems to work fine.  When I put in a disc, it gets mounted automatically, and I can even play DVDs in MythTV.  Of course, I had to set the dvd device to /dev/scd0 in the setup.   When I chose rip/transcode, it just sits there waiting for a DVD.  Is there anything else I need to do to make it work?

Thanks
Did you make sure you changed the drive settings for ripping?

---

### Post by knathraak on 2008-04-03
> **foxbuntu said:**
> Did you make sure you changed the drive settings for ripping?

I looked at that.  The Rip command is mplayer with a --dvd-device option, and the macro "%d," which, I assume, is supposed expand to the dvd device obtained from the database.  

I ran mythfrontend with verbose output and saw that when I choose the Rip/Transcode option, it performs the following query:
```
 SELECT data FROM settings WHERE value = 'DVDDeviceLocation' AND hostname = 'bespin' ;

```
I logged into mysql and performed the query, and it comes back /dev/scd0, so I think that part's right.

---

