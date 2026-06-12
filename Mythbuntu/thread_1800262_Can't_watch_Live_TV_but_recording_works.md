---
title: "Can't watch Live TV but recording works?"
date: 2011-07-08
forum: Mythbuntu
---

### Post by sidesh0w on 2011-07-08
So my mythbox has been flawless for last couple years, so I havent upgraded or touched any configuration for awhile.
 
Come 5 minutes before the state of origin game 3 (why is life so cruel) I lost the ability to watch live TV...
 
If I try watch live TV I get the 'Please Wait...' then it just kicks back to menu, no error (on the gui side anyway).
 
Now the weird part... recordings are still working (I actually just setup the origin game to record then watched it on delay).
 
So everything is working fine, even recordings... just cant watch live TV ?
Any help where to look for logs, etc? (never botherd to troubleshoot in the past and just did a re-install, but this setup has kept me going for so long...)

---

### Post by heyho on 2011-07-09
I can't be of any specific help regarding your problem, however you should find you logs in /var/log/mythtv.  Post your most recent logs, and hopefully somebody will be able to offer some advice.

---

### Post by nickrout on 2011-07-09
> **sidesh0w said:**
> So my mythbox has been flawless for last couple years, so I havent upgraded or touched any configuration for awhile.
 
Come 5 minutes before the state of origin game 3 (why is life so cruel) I lost the ability to watch live TV...
 
If I try watch live TV I get the 'Please Wait...' then it just kicks back to menu, no error (on the gui side anyway).
 
Now the weird part... recordings are still working (I actually just setup the origin game to record then watched it on delay).
 
So everything is working fine, even recordings... just cant watch live TV ?
Any help where to look for logs, etc? (never botherd to troubleshoot in the past and just did a re-install, but this setup has kept me going for so long...)

Perhaps because the tuner was busy recording it (I don't know how many tuners you have?)

---

### Post by David Grigor on 2011-07-11
I had this problem a year or so ago. I couldn't watch live but it would record just fine. 

Change your playback profile to something lower and see if you can get it to work. 

Utilities -> Setup -> TV Settings -> Playback -> Playback Profiles

If that resolves, then start stepping up the quality to the highest you can get it to work reliably. 

If still doesn't work, you will have to review the logs for any other possible clues.

---

