---
title: "Help with channel lineups / card setup"
date: 2010-01-22
forum: Mythbuntu
---

### Post by bcg30506 on 2010-01-22
I am having a difficult time understanding the relationship between the channel scan for a tuner, mythfilldatabase, and the Schedules Direct lineups.  Here is my situation:

I have the HDHomeRun dual tuner to pick up my cable company's free HD channels over QAM.  Schedules Direct do not formally support QAM but they have a digital cable lineup that contains all the QAM channels (with different channel numbers) except one.  I know I can edit the channels in mythweb to modify the channel numbers to my liking.  My problem is the one channel that is missing.  It is on off-the-air channel that is broadcast via QAM too.  It shows up on SD's Local Broadcast lineup but I'm not using an OTA antenna.

Right now I include both lineups to get the listings but obviously can only connect my tuners to one lineup and they really need to point to the Digital Cable one to get most of the channels.  How do I get this last channel into my tuner listings?  Will mythfilldatabase download the listings for all lineups even if no tuner is "using" them?  I know I can edit the xmltvid's in mythweb, but don't want the mythfilldatabase runs to blow away the tuning frequencies found when the HDHR did the scan with the ones from the SD lineup.

I'm sorry if my question is hard to understand.  I guess if I don't really get the relationships between these pieces, it's hard to even know what or how to ask.

---

### Post by myth1914 on 2010-01-22
Once you scan for the channels and pull the frequency table associated to those channels, the DB should maintain it.  If you then edit the channels to match the channel number to what your SD lineup pulls, the mythfilldatabase runs should update the listings on those you specify in your SD lineup.

To clarify some, you can have channels in your SD lineup that will show in the guide regardless of if you can tune to them.

I use two channel lineups for this purpose.  One for standard and one for HD.  I've only scanned the HD channels once, from there, the frequency lock is set and while I could change the channel number, SD had them all so it associated the listings content accordingly.

---

### Post by klc5555 on 2010-01-22
> **bcg30506 said:**
> I am having a difficult time understanding the relationship between the channel scan for a tuner, mythfilldatabase, and the Schedules Direct lineups.  Here is my situation:

I have the HDHomeRun dual tuner to pick up my cable company's free HD channels over QAM.  Schedules Direct do not formally support QAM but they have a digital cable lineup that contains all the QAM channels (with different channel numbers) except one.  I know I can edit the channels in mythweb to modify the channel numbers to my liking.  My problem is the one channel that is missing.  It is on off-the-air channel that is broadcast via QAM too.  It shows up on SD's Local Broadcast lineup but I'm not using an OTA antenna.

Right now I include both lineups to get the listings but obviously can only connect my tuners to one lineup and they really need to point to the Digital Cable one to get most of the channels.  How do I get this last channel into my tuner listings?  Will mythfilldatabase download the listings for all lineups even if no tuner is "using" them?  I know I can edit the xmltvid's in mythweb, but don't want the mythfilldatabase runs to blow away the tuning frequencies found when the HDHR did the scan with the ones from the SD lineup.

I'm sorry if my question is hard to understand.  I guess if I don't really get the relationships between these pieces, it's hard to even know what or how to ask.

? Only one lineup per tuner? That's not the case. One _Video Source_ per tuner. Each Video Source could incorporate bits and pieces of any number of Schedules Direct lineups, whatever you need. If you're already getting the Schedules Direct xmltvid information for your channel on any of the lineups you currently subscribe to, just call up the channel on livetv and edit in the appropriate xmltvid number that gives you the full schedule, and you'll get it the next time mythfilldatabase runs. No problems.

The only thing mythtv requires is that if you get two versions of the same channel (analog and SD, say; or SD and HD) then you need to differentiate the two versions by assigning them two differentiated call signs: WWTW and WWTW-DT or WFOO-DT and WFOO-HD. And you're good to go, even if the two versions have the same broadcast schedule and therefore the same xmltvid.

If you need to add a second lineup at Schedules Direct to get your channel's schedule, blank out all the channels on this second lineup at the website ("edit lineup") except the one channel you want. 

Schedules Direct doesn't do tuning frequencies, it does xmltvids, and the broadcast schedules associated with those xmltvids. If the xmltvid number is correct that you've entered in the channel editor or equivalent, you'll get the one and only schedule filled in in mythconverg that is associated with that precise xmltvid, provided you have added some lineup somewhere at Schedules Direct that has that xmltvid.

Example. I'm on Comcast. For about two months last winter they supplied Deutsche Welle on QAM to my area, but had no xmltvid for it. The only xmltvid I could find for DW was on the local FIOS lineup. So I added the FIOS lineup on Schedules Direct to my Comcast lineup, blanked all the FIOS channels from this lineup save the one I needed, edited in the appropriate xmltvid to the scanned channel where DW was appearing, and ran mythfilldatabase. Still all on one Video Source. No problems. 
Well, until Comcast eliminated DW anyway (darn them)...

---

### Post by bcg30506 on 2010-01-22
That is the most detailed, clear, and helpful explanation I've seen on this subject in all the years I've been using MythTV.  Thank you!

In essence, that is what I've done.  I have one channel that does not show up in the Charter Digital lineup that my QAM tuner pulls in, but it is listed in the Local Broadcast lineup.  So I added that lineup and removed everything but that one channel.  The tuner is tied to the Charter Digital lineup in mythtv-setup but I used the mythweb interface to edit the xmltvid with the one on the SchedulesDirect site for the one air station that the QAM tuner receives over cable.

So I guess I accidentally got it right?  I just wasn't sure if no tuners were connected to a lineup source in mythtv, that mythfilldatabase would still download listings for it or not.  But both of your replies seem to say mythfilldatabase downloads listings for ALL lineups in my account, regardless if they are used explicitly by a capture input.  Did I read this right?

---

### Post by klc5555 on 2010-01-23
> **bcg30506 said:**
> That is the most detailed, clear, and helpful explanation I've seen on this subject in all the years I've been using MythTV.  Thank you!

In essence, that is what I've done.  I have one channel that does not show up in the Charter Digital lineup that my QAM tuner pulls in, but it is listed in the Local Broadcast lineup.  So I added that lineup and removed everything but that one channel.  The tuner is tied to the Charter Digital lineup in mythtv-setup but I used the mythweb interface to edit the xmltvid with the one on the SchedulesDirect site for the one air station that the QAM tuner receives over cable.

So I guess I accidentally got it right?  I just wasn't sure if no tuners were connected to a lineup source in mythtv, that mythfilldatabase would still download listings for it or not.  But both of your replies seem to say mythfilldatabase downloads listings for ALL lineups in my account, regardless if they are used explicitly by a capture input.  Did I read this right?

Sounds like it's set up like it should be. If the data shows up after a mythfilldatabase --refresh-today --refresh-all  then it's working. But your conclusion is correct, all non-blanked out channel schedules for all lineups that are subscribed to are downloaded en masse and dumped into one big data pot, which any Video Source on your myth machine may use any or all of.

Cheers!

---

### Post by mythbuntu101 on 2010-01-28
I too have a problem w/ 'mythfilldatabase' (mythbuntu 9.10) Can you supply a 'step-by-step' how to for this? SchedulesDirect info is okay. Here's their direct reply.
- - - - - -
MythTV downloads data in raw format and doesn't have the limitation. Since you can download data using XMLTV there's nothing wrong with yourSD account or PC setup, you must have a MythTV config issue. Unfortunately, we're not really in a position to help with applicationproblems. I don't even use Myth myself. I suggest you post on theMyth-Users mailing list. I'm sure there are folks there who can help.
 - - - - -
Can you provide how fix this MythTV config ? [http://mythbuntu.org/installation_manual](http://mythbuntu.org/installation_manual) is not currently working

---

