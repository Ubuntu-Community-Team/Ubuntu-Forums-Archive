---
title: "First Mythtv attempt and struggling"
date: 2013-01-16
forum: Mythbuntu
---

### Post by bensr20det on 2013-01-16
Hello,

I am trying to switch from WMC to mythbuntu and having a tough time. On WMC when I would scan for my channels it would bring them all up. On Mythtv it is only getting some. I am also trying to use Schedules Direct. I was kind of hoping that I could just download the channel list from there with out having to scan. And then the ones that I do pick up with the scan are not all showing the correct name from SD. So any channels in the 36 range like 36-2 or 36-6 all show up as the same channel name even though they are not. I know I am not giving enough info but I don't even know where to start. I have checked every site I could find. Please let me know what I can give you to help solve this issue.

Thanks,
Ben

---

### Post by bensr20det on 2013-01-17
Any Ideas? Is there any information I can give to help?

---

### Post by klc5555 on 2013-01-17
1) Depending on what tuner(s), what format of TV you're scanning for (cable, satellite, OTA digital, even maybe analog) and which Linux driver(s) your tuner(s) use, then it is possible that your Linux scans are in fact getting fewer locks than your Windows scans. Most tuner manufacturers don't write Linux drivers at all; these are supplied over time by the open source community. A lot of these are beta code. Some aren't stable. Only pc-hdtv (so far as I know) targets the Linux community in preference to the Windows community.

2) But more likely you're getting about the same number of unencrypted channels with a myth scan as with a Windows scan, just that they're mostly named "UNKNOWN" or the equivalent. And listed as subchannels under main channel numbers, where the numbering is peculiar, like "37_059" or some such. This is actually normal.

3) The UNKNOWN channels you may have to identify yourself, by watching them in livetv. Keep a list. Since nobody wants to deal for long with channel number "37_059", you assign each viewable channel whatever (virtual) channel numbers you wish --one, two, three, four, or five digits in length. You can do this in bulk, from the Channel Editor in the backend setup, or per individual channel, by hitting the "e" edit key while the channel is on your screen in live TV from the Mythtv frontend. You might also wish to name the channel something more appropriate than UNKNOWN and give it a callsign (it doesn't have to be the actual real-life callsign, just something unique) like WKKW-HD3. These things also are done from the Channel Editor or using the "e" edit key in livetv.

4) When you have identified some (or all) your viewable channels, either automatically or by inspection, you'll want to hook up each identified channel with appropriate program schedule information from SchedulesDirect. Each SchedulesDirect listed channel has a 5-digit XMLTVID number. You can log into SchedulesDirect and print out your list of channels and XMLTVID numbers, if you wish. In Mythtv, for each viewable channel, plug in the 5-digit XMLTVID number corresponding to the SchedulesDirect channel you intend to use for it. Again, from the Channel Editor, or "e" edit key while watching livetv. Some of the channels that got automatically identified in the scan may already have their XMLTVID numbers entered, but often not. The XMLTVID number is the only glue that connects SchedulesDirect listings with the channels in your Mythtv installation.

5) The next time mythfilldatabase runs, it will pull in the program data for your channels that have had the XMLTVID numbers entered. By default, this data begins to fill into the database for the midnight _after_ mythfilldatabase has run, so you might have to scroll forward a bit in your schedules listing to see it begin, after mythfilldatabase has finished.

6) For general myth configuration questions, check the wiki and its installation guide: [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) For more concrete questions about a) your specific hardware, including specific tuners; b) your specific version of Mythtv/Mythbuntu; c) the specific type of TV (etc.) service you're trying to hook up to and d) specific software or configuration glitches, for which you may be asked to supply specific information from various logs to help troubleshoot, please check back. If someone can't help, then usually you'll be able to find out where deeper technical assistance may be found.

---

### Post by kcog on 2013-01-18
Copy and paste that post into the wiki!  ASAP.  Thank you very much! :guitar:

What I always wonder is how did people like you learn this if it's not documented somewhere?

I'm not positive, but I think your post has the information I need to answer my question
[http://www.silicondust.com/forum/viewtopic.php?t=14242](http://www.silicondust.com/forum/viewtopic.php?t=14242)
...which I was about to re-post here.

KC

---

