---
title: "Retrieving Lineup from Schedules Direct, not showing newly added lineup"
date: 2015-06-29
forum: Mythbuntu
---

### Post by stevenc413 on 2015-06-29
&#8206;Just got a HD home run connect and trying to add it to mythtv. 

I added it as a Capture Device, it shows up fine. I added the antenna as a source in Schedules Direct from their website. But when I go to Video Sources and click 'Retrieve Lineup', it only shows the lineup I use for my other tuner (old PVR cable tuner). Am I doing this wrong, or is there another way to force it to update?

Tried restarting, running mythfildatabase, still just that one lineup.

---

### Post by aelfric55 on 2015-06-30
Independent of what you've done with Schedules Direct, in the backend setup you'd normally add a new video source (say, "Antenna") for your antenna in Video Sources. This new video source "Antenna" would then be bound to your new tuner's /dev/... node in Input Connections.  You would then scan for available channels on this new tuner in Input Connections, so that mythconverg database entries for the channels visible to the antenna tuner will be created for the bound video source "Antenna". You'd check these newly added channels entries in Channel Editor: with luck the xmltvid numbers and the names for the visible "Antenna" channels will have filled in during the scan. If they haven't, you fill them in manually, obtaining the xmltvid numbers for the affected channels from the Schedules Direct web site.

 When all this is done, you'd run mythfilldatabase. It retrieves all the data basically in undifferentiated daily lumps from all your Schedules Direct lineups, and sorts it and plugs it in to mythconverg by xmltvid numbers (and pretty much nothing else) upon arrival.  

And then you should be ready to go.

---

### Post by stevenc413 on 2015-06-30
I guess the question I have is, should I have two lineups one Cable, and one Antenna like you have it setup in Schedules Direct. I was expecting two to show up in the drop down when I go to Backend Setup -> Video Sources -> click 'Retrieve Lineup' after entering my Schedules Direct information.  It is connecting to schedules direct, because the list is populating, but it only has the one option, which says cable.

---

### Post by aelfric55 on 2015-06-30
You need two defined video sources in your Video Sources: one for your cable tuner and one for your OTA Antenna tuner. It doesn't matter if you have one, two, or four lineups set up in Schedules Direct, as long as each channel you see on whatever tuner has an xmltvid number to describe its unique lineup in the undifferentiated xmltv schedule stew that mythfilldatabase downloads. For example, the local ABC over-the-air channel will probably use the same xmltvid number as the cable local ABC channel, same with the OTA NBC channel and its cable NBC version, etc.

For years, Schedules Direct failed to include one channel that I received on Comcast in the so-called "Comcast lineup" for my area code. I found this channel on a "FIOS lineup" for two towns over from mine, and so I added that town's "FIOS lineup" (or one channel from it) so I could get the channel's xmltvid number and schedule dumped into my mythconverg for my unsupported Comcast channel. In short, Schedule Direct's "lineups" are nearly meaningless --they are an aid to subscribers to organize xmltvid's and the associated data in a more convenient roughly geographical way, but they don't actually correspond physically to anything going on in mythtv or with the number or type of tuners in your installation.

---

