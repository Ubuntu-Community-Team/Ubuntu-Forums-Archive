---
title: "mythfilldatabase issue"
date: 2009-02-11
forum: Mythbuntu
---

### Post by ForgivenByJC on 2009-02-11
I have Mythbuntu 8.10.  I have two tuner cards.
sourceid 1: Hauppauge PVR-150
sourceid 2: Hauppauge WinTV-Go
Both work and record.  Unfortunately, channel 70 (National Geographic Channel) comes in poorly on sourceid 2: Hauppauge WinTV-Go tuner.  Most other channels record well.  So, I went to Mythweb and deleted sourceid 2 channel 70 from the channel lineup.  The next time mythfilldatabase ran, it re-added sourceid 2 channel 70 to the channel lineup.

I am using SchedulesDirect and can only create one lineup for this account.  Ergo, cannot create another SD lineup without channel 70 and link sourceid 2: Hauppauge WinTV-Go to it.

How should this be set up so mythfilldatabase does not re-add channel 70 to sourceid 2: Hauppauge WinTV-Go, but does update the listings for channel 70 on sourceid 1: Hauppauge PVR-150?  

Have tried
```
mythfilldatabase --update
``` but channel 70 was re-added to the sourceid 2: Hauppauge WinTV-Go channel lineup.
I have searched the web in vain, so if there is a means to isolate this situation via a web search which you have found, please share this also.

---

### Post by dannyboy79 on 2009-02-11
I am still using 20.02 and Feisty but isn't there a way that when you schedule a recording on channel 70 that it will only use sourceid 1? I thought I remember reading something about that when Mythtv 21 came out.

---

### Post by crez79 on 2009-02-11
Delete the channel on the source you don't want it on then try ```
mythfilldatabase --remove-new-channels
```

If that works add --remove-new-channels to mythfilldatabase arguments under general settings, and it will be used everytime myth automatically runs mythfilldatabase.

If you add --help to most commands you can get some arguments or modifiers. Some commands are more helpful than others. Also check the man page by typing man *command* (where *command* is the command you want info about) and that will show you a help file of sorts. Again, some are more helpful than others.

---

### Post by ForgivenByJC on 2009-02-13
**DannyBoy**, I have not heard of blocking a channel from a sourceid.  You can specify "Preferred Input" on MythWeb or select between "Use any available input/Prefer Input Hauppauge PVR-150/Prefer Input Hauppauge WinTV-Go" on MythTV Frontend.  This would only give the authority to specify per recording basis instead of per tuner/sourceid basis.  Is this possibly what you were thinking about?

**Crez**, thank you for your reply.  This seems to have done the trick.  I had seen "--remove-new-channels" when using "--help" and it says:
```
--remove-new-channels
   When using DataDirect, ask mythfilldatabase to
   remove new channels (those not in the database)
   from the DataDirect lineup.  These channels are
   removed from the lineup as if you had done so
   via the DataDirect website's Lineup Wizard, but
   may be re-added manually and incorporated into
   MythTV by running mythfilldatabase without this
   option.  New channels are automatically removed
   for DVB and HDTV sources that use DataDirect.

```
This gave me the impression it would disable the channel from the SD source and subsequently stop populating listings for sourceid 1 channel 70 as well.  My impression seems to have been wrong.  After checking the SD website, channel 70 is still available.  There is still two weeks of listings for channel 70 in mythweb, so am uncertain if the listings are current or residual from before running "mythfilldatabase --remove-new-channels" and adding "--remove-new-channels" to mythfilldatabase arguments under general settings.  Until I see evidence of this, I am going to consider this issue resolved.  I will know in a few days if other channels receive listings two weeks out and channel 70 does as well.  Thank you, Crez! ):P

---

### Post by ForgivenByJC on 2009-02-20
The
```
--remove-new-channels
```
option is still working beautifully!  Thank you!

---

