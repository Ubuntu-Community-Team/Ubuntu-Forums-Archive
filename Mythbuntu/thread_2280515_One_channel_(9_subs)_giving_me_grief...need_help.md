---
title: "One channel (9 subs) giving me grief...need help"
date: 2015-05-31
forum: Mythbuntu
---

### Post by johnodon on 2015-05-31
Hello all...first post here.

I'll try to include all of the relevant info but if more is needed please let me know.

My setup:

Base:  MythBuntu 14.04.2 with latest updates running in a KVM VM on top of unRAID
Tuner #1:  HDHomerun HDTC-2US (firmware 20150406)
Tuner #3:  HDHomerun HDHR3-US (firmware 20150406)
Guide data provider:  Schedules Direct zip code 19380
Channel freq table:  us-bcast

If I scan for channels using the HDHomerun Setup app (from my WIN8 laptop), all channels are captured as expected with correct channel #s, call signs and names.  Same hold true for the HDHomerun Config GUI app provided with mythbuntu.

When I run a channel scan in Myth, all channels look good except for channel 33 (subs 33.1 thru 33.9).  Some of the discrepancies are...

Good channels have numbers such as 29_1, 29_2, etc. but channel 33 shows as 33-1, 33-2, etc.
All channel 33 subs are populated with the same name and xmltvid:  WZPALD2 (WZPAL-D2) and 80751
The callsigns for the 33 subs look abnormal to me:  i.e.  33-1 has a callsign of 1331, 33-2 has a callsign of 1332, etc.
Naturally since all 33 channels have the same xmltvid, they all get the same guide data from SD.

I have tried to manually edit the 33 channels to change the xmltvid as found at the link below but have had very mixed results.  Sometimes new, correct data is pulled in...sometimes not.

[https://www.schedulesdirect.org/lineups/report/PC%3A19380](https://www.schedulesdirect.org/lineups/report/PC%3A19380)

Ignore the guide data issues...my main concern is why Myth is pulling channel 33 differently than HDHomerun config gui and the HDHomerun setup app.  I have included some pics below.

Myth sees all 33 subs as same channel
[IMG]http://i.imgur.com/ZhgKmZp.png[/IMG]

Details of 33-1 in Myth.
[IMG]http://i.imgur.com/LZFnyqg.png[/IMG]

MythWeb showing same guide data for all 33 subs
[IMG]http://i.imgur.com/p0SZSqh.png[/IMG]

HDHomerun Gui in Mythbuntu shows correct names/numbers
[IMG]http://i.imgur.com/pYnLr8g.png[/IMG]

HDHomerun Setup on my WIN8 also shows correct numbers/names
[IMG]http://i.imgur.com/Fg0J9lo.png[/IMG]

If there are any log files I can provide please let me know.  I have to plead ignorance as I am not THAT familiar with Myth yet so I may need some guidance.  :)

TIA for the help!

John

Update:  I deleted all channels in Myth and manually added 33_5 with the correct xmltvid.  That channel is pulling correct data.

[img]http://i.imgur.com/bv4dEyR.png[/img]

I'll try the same with a few other 33 subs and see if the success continues.

John

UPDATE #2:  The success continues.  I manually added two more 33 subs and data looks good.  I'll do this for the rest and report back.  After that I'll run a channel scan to pull in all other channels.  My suspicison is that I will again get the bogus channels.  If that happens, I'll just mark those as invisible and leave my manually added ones as is.

[img]http://i.imgur.com/33CTXfJ.png[/img]

---

### Post by johnodon on 2015-05-31
UPDATE #3:  I added all of the 33 subs manually.  All of them have good EPG data.  I then did a full channel scan and this is what I ended up with:

[IMG]http://i.imgur.com/BeOTNyn.png[/IMG]

As you can see, I have dupe channels for the 33's (i.e. 33_1 and 33-1).  The 33_1 was the manually created one and the 33-1 was captured via a channel scan with a callsign like "1331".

Here is what 33-1 (1331) looks like:

[img]http://i.imgur.com/jykgc3c.png[/img]

I tried playing both channels in Kodi and neither worked.  The manually entered ones just spun for a bit and eventually came back as "Channel unavailable".  The 33 channels that were found via a scan refused to do anything (no sign of any life at all).

John

---

