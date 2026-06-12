---
title: "More QAM help"
date: 2011-11-02
forum: Mythbuntu
---

### Post by bcg30506 on 2011-11-02
Every time our cable company moves our digital QAM stations around, I panic and get lost in confusion over how to easily rescan/map them in MythTV.  I renumber all of them to make it easier for us to remember them with the remote (higher WAF).

I have 2 text files I've generated with hdhomerun_config and VLC.  One shows the scan results with frequencies and the default program numbers.  The other is a result of me using the hdhomerun_config GUI to view each found channel with VLC and typing in what station it is.

What all does myth need to tune in and align the listings?  Is there an automated way to get from what I have in these files to a working mythtv configuration?

---

### Post by GaryP2 on 2011-11-02
I just recently learned how to edit the database with phpMyAdmin, editing both the dtv_multiplex and channels tables. You do need to install and learn how to carefully use phpMyAdmin, but I think this may the easiest way to make incremental changes (channel adds, moves, or deletes) once you&#8217;re up and running. Just go at it slow, making a small change at first and seeing the results, etc. Wrong changes in the database can render things useless.
[INDENT][http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada)#Manually_adding_channels](http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada)#Manually_adding_channels)
[/INDENT]Getting all the channels aligned was one of the more frustrating parts of setting up Myth .23 for me 14 months ago. I think I read somewhere along the way that things were broke with that version of Myth in regards to auto channel scanning, etc.. Things may or may not be better with the most recent release.

---

### Post by nickrout on 2011-11-02
> **bcg30506 said:**
> Every time our cable company moves our digital QAM stations around, I panic and get lost in confusion over how to easily rescan/map them in MythTV.  I renumber all of them to make it easier for us to remember them with the remote (higher WAF).

I have 2 text files I've generated with hdhomerun_config and VLC.  One shows the scan results with frequencies and the default program numbers.  The other is a result of me using the hdhomerun_config GUI to view each found channel with VLC and typing in what station it is.

What all does myth need to tune in and align the listings?  Is there an automated way to get from what I have in these files to a working mythtv configuration?

Are you in the US? I though schedules direc tdid all this automatically?

---

### Post by GaryP2 on 2011-11-02
> **nickrout said:**
> Are you in the US? I though schedules direc tdid all this automatically?
Analog channel lineups flow into Myth from SchedulesDirect through the mythfilldatabase process pretty well. But for me the digital lineups took a lot of finagling to get everything correct the first time. If I remember right I had to have Myth scan for digital channels first, and then *manually* edit some or most of the channel attributes (like the callsign, xmltvid, etc.) for each of the channels. Then when mythfilldatabase ran, it populated things from there if you had your SchedulesDirect digital channel lineup setup correctly. 
 
I don’t think SchedulesDirect knows what RF channel (referred to as the multiplexid in the database from the dtv_multiplex table) and subchannel (referred to as the serviceid) is used for each channel for the cable TV system without either scanning for channels or manually editing the database for minor changes.

---

### Post by bcg30506 on 2011-11-04
> **GaryP2 said:**
> Analog channel lineups flow into Myth from SchedulesDirect through the mythfilldatabase process pretty well. But for me the digital lineups took a lot of finagling to get everything correct the first time. If I remember right I had to have Myth scan for digital channels first, and then *manually* edit some or most of the channel attributes (like the callsign, xmltvid, etc.) for each of the channels. Then when mythfilldatabase ran, it populated things from there if you had your SchedulesDirect digital channel lineup setup correctly. 
 
I don’t think SchedulesDirect knows what RF channel (referred to as the multiplexid in the database from the dtv_multiplex table) and subchannel (referred to as the serviceid) is used for each channel for the cable TV system without either scanning for channels or manually editing the database for minor changes.

This is my experience as well.

As for this particular lineup change, I was able to modify things fairly quickly simply by manually editing the channel table's mplexid, freqid, serviceid, and channum fields in mysql to match the new positions from Charter.

---

