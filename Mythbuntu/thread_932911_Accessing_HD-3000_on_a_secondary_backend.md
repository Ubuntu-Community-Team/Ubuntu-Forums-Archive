---
title: "Accessing HD-3000 on a secondary backend"
date: 2008-09-28
forum: Mythbuntu
---

### Post by dvanbrunt on 2008-09-28
I have a main/primary mythbuntu HTPC in my living room, with 2 tuners... PVR-250 adn PVR-350, working great.

I had an HD-3000 card laying around, and wanted to use it, too.. but didn't want the rabbit ears in my living room. So I installed it in my other Linux/Ubuntu box (Hardy) and then installed MythBuntu and declared that box a "secondary backend"

In the configuration, it detects the card and does a channel scan. Seems to find the stations. Then I assigned the listings source and connected them up, just as I have done successfully for the PVR-x50's on cable. Mythfilldatbase ran, and appears to be connecting to the primary backend.

Now the program guides show the addition of the Digital stations, but they are greyed out! 

If I hit "Record", I see a message saying that the tuner is "off line"..

... Huh?

How do I make it "on line" then?

---

### Post by novellahub on 2008-09-29
Cycle the backend on the slave box:

```
sudo /etc/init.d/mythtv-backend restart
```

Then the tuner will be active.

---

### Post by dvanbrunt on 2008-10-02
> **novellahub said:**
> Cycle the backend on the slave box:

```
sudo /etc/init.d/mythtv-backend restart
```

Then the tuner will be active.

Unfortunately, that didn't do it. Still appears off line. Not sure how to even test the tuner card.

Should I have installed something from the makers of the HD3000? I thought MythTV and Ubuntu handled everything, but maybe I'm mistaken.

---

### Post by newlinux on 2008-10-02
how did you set it up in myth (DVB?) Is this a pchdtv HD-3000? If so I know it used to require firmware to properly tune digital stations, not sure if still does. From your post I think you are trying ot tune OTA ATSC channels? 

the concerning part is that it isn't even showing up as online. It would help to see the backend logs of the machine that has the tuner it right after a restart of the backend.

So you can see the tuner in your system status, but it shows up as offline?

---

### Post by dvanbrunt on 2008-10-04
> **newlinux said:**
> how did you set it up in myth (DVB?) Is this a pchdtv HD-3000? If so I know it used to require firmware to properly tune digital stations, not sure if still does. From your post I think you are trying ot tune OTA ATSC channels? 

the concerning part is that it isn't even showing up as online. It would help to see the backend logs of the machine that has the tuner it right after a restart of the backend.

So you can see the tuner in your system status, but it shows up as offline?

Ok, it's fixed.  No idea what the magic bullet was, but I deleted all the lineups (on BOTH backends) when I saw that there appeared to be 2 additional tuners when looking at the Info screen on the primary backend/frontend. So on the secondary, I deleted all the cards and lineups (and OOPS this removed them on the primary too... who knew?) then re-added the HD3000 from the secondary, and re-added the PVR-x50's from teh primary. Restarted both. Working fine now. 

With apologies to the moderators for the original cross post, I'll link to this comment from the other thread.

---

