---
title: "Identifying channels"
date: 2009-06-09
forum: Mythbuntu
---

### Post by AKADAP on 2009-06-09
How do I identify which sub-channel is being tuned for a particular channel?

I have a translation table for Comcast in San Jose, CA that lists the frequency, the sub-channel,the cable channel, the call signs for the station, and the channel that Comcast maps it to (which is the number than schedules direct uses for its channel number) This table was extracted from the output of a script that someone on the AVS forum created that reads out the table that Comcast sends to its cable boxes. I have no cable boxes, so I have no means of verifying the channel numbers.

The problem I am having is that with Myth Backend, and Mythweb, I can find the cable channel number (the old analog cable channel number), but not the sub channel.

This is a problem because there can be as many as 34 subchannels on a single channel (in this specific instance, these are mostly FM Radio stations). 

MythTV identifies these channels with a name. For instance UNKNOWN96#24 is KFOG an FM radio station. I learned this because I happened to hear a station ID. If I look at the mapping table, I find that FM-KFOG is on channel 96, sub-channel 34 at 99000000Hz and should be mapped to 984.
The number before the # is consistently the old analog cable channel number, but the number after the # does not seem to correlate to anything, and is sometimes zero which is not a legitimate sub-channel number.

I know Myth TV must store this information somewhere, because it can properly tune the channel, but I need to get at it so I can get proper channel numbers, names and TV listings for myth TV

---

### Post by crez79 on 2009-06-09
What I did was used mythweb. Goto http://<serverip>/mythweb/settings/tv/channels and tune one of the unknown channels. Find it under the callsign column. Figure out what channel it is by watching or listening to it. Look up the xmlid and the channum and callsign and name and fill them out. I used zap2it because that is the source of information for schedulesdirect.org, i think. It was a big pain in the butt, but I couldn't find any other way. I  started with the stations I would actually want and worked to the less watched channels. If you don't want to see that channel i the guide you can un check the visible box. When you are done, click save at the bottom. Then backup your database so you don't have to do that again! I spend days watching random channels watiting for a station identifier. You can also try [silicondust's lineup server]("http://www.silicondust.com/hdhomerun/channels_us") to help narrow down your choices, but be aware they don't specifiy which provider each channel uses, so it may be inaccurate.

---

### Post by klc5555 on 2009-06-09
> **AKADAP said:**
> How do I identify which sub-channel is being tuned for a particular channel?

I have a translation table for Comcast in San Jose, CA that lists the frequency, the sub-channel,the cable channel, the call signs for the station, and the channel that Comcast maps it to (which is the number than schedules direct uses for its channel number) This table was extracted from the output of a script that someone on the AVS forum created that reads out the table that Comcast sends to its cable boxes. I have no cable boxes, so I have no means of verifying the channel numbers.

The problem I am having is that with Myth Backend, and Mythweb, I can find the cable channel number (the old analog cable channel number), but not the sub channel.

This is a problem because there can be as many as 34 subchannels on a single channel (in this specific instance, these are mostly FM Radio stations). 

MythTV identifies these channels with a name. For instance UNKNOWN96#24 is KFOG an FM radio station. I learned this because I happened to hear a station ID. If I look at the mapping table, I find that FM-KFOG is on channel 96, sub-channel 34 at 99000000Hz and should be mapped to 984.
The number before the # is consistently the old analog cable channel number, but the number after the # does not seem to correlate to anything, and is sometimes zero which is not a legitimate sub-channel number.

I know Myth TV must store this information somewhere, because it can properly tune the channel, but I need to get at it so I can get proper channel numbers, names and TV listings for myth TV

You can assign any arbitrary channel number 1 to 9999 and beyond, name, and callsign that you want to a "subchannel". Doesn't matter where Comcast would have set it on its cable box. What matters is that you have SchedulesDirect's xmltvid number for the station, and when you're ready to enter data for the station, you assign each one a unique callsign. (That is, if you get, say, station "WBBM" in analog, SD, and HD versions, you'll need to assign unique callsigns like WBBM, WBBM-DT, and WBBM-HD, etc., so mythtv can tell them apart for recording purposes if they happen to use the same xmltvid number.)

When you have identified a station and have it up onscreen in livetv, the "e" keyboard shortcut brings the menu where you can edit in name, callsign, channel number, and xmltvid number for this station. (You could also do this in Channel Editor in the backend, but it's less convenient) 

The edits basically take affect immediately; the guide information will begin to fill in correctly for the day _after_ the next mythfilldatabase run.

---

### Post by AKADAP on 2009-06-09
So far I have not seen a good answer.

The translation table I have lists 149 channels. This is not a complete list as it does not cover any of the HD broadcast channels that show up as unencrypted QAM256, and may not include other unencrypted QUAM256 signals.

MythTV channel scan is the only way to add digital channels, one can not specify sub-channels, so one can not manually add a digital channel.

MythTV channel scan can not reliably find unencrypted channels, so one must scan with the unencrypted only flag disabled. This means one gets many useless channels anytime one rescans.

You can disable a channel such that a re-scan will not add it to the list, but if in one of Comcasts many channel reshufflings an unencrypted channel moves to where an encrypted one previously resided that you had disabled, it will not show up in the channel list.

Removing encrypted channels from the lineup is painful and slow. When you tune to an encrypted channel using live TV, it dumps you back at the menu. Sometimes an encrypted channel can cause a DVB to crash which makes other channels appear to be encrypted even though they are not. The only way to recover from this crash is to power cycle the computer as a reboot is insufficient. An encrypted channel can also cause the MythTV front end to lock up with 100% CPU usage requiring mythTV be killed.

Identifying unencrypted channels is also difficult. There are multiple copies of similarly named channels which have similar but not exactly the same schedules. (analog versions of a station will have a different schedule number than the digital version of the same channel). Some stations don't have a bug, and must be watched for the hourly station ID to get some clue as to what station it is. If you are lucky, you can sometimes catch a couple of station IDs on the hour, as they don't quite do their IDs at exactly the same time. Some cable only stations never do a station ID.

Now if I could get MythTV to tell me the actual sub channel for its list of stations, I could use the translation table I have to quickly identify 149 of those stations, saving me many hours of trying to catch elusive station IDs.

---

### Post by AKADAP on 2009-06-09
> **klc5555 said:**
> You can assign any arbitrary channel number 1 to 9999 and beyond, name, and callsign that you want to a "subchannel". Doesn't matter where Comcast would have set it on its cable box. What matters is that you have SchedulesDirect's xmltvid number for the station, and when you're ready to enter data for the station, you assign each one a unique callsign. (That is, if you get, say, station "WBBM" in analog, SD, and HD versions, you'll need to assign unique callsigns like WBBM, WBBM-DT, and WBBM-HD, etc., so mythtv can tell them apart for recording purposes if they happen to use the same xmltvid number.)

When you have identified a station and have it up onscreen in livetv, the "e" keyboard shortcut brings the menu where you can edit in name, callsign, channel number, and xmltvid number for this station. (You could also do this in Channel Editor in the backend, but it's less convenient) 

The edits basically take affect immediately; the guide information will begin to fill in correctly for the day _after_ the next mythfilldatabase run.

If one can identify the channel enough to add the xmltvid number, one can also put in the correct Comcast channel number. In fact one must first identify the correct Comcast channel number to figure out the xmltvid number as the list of xmltvid numbers is listed by Comcast channel number on the schedules direct web page.

This is in fact the primary reason I got the translation table in the first place, so I could identify the correct xmltvid number for the channels I am receiving. But, unless I can get the sub-channel number from MythTV, it is proving useless.

---

### Post by klc5555 on 2009-06-09
> **AKADAP said:**
> If one can identify the channel enough to add the xmltvid number, one can also put in the correct Comcast channel number. In fact one must first identify the correct Comcast channel number to figure out the xmltvid number as the list of xmltvid numbers is listed by Comcast channel number on the schedules direct web page.

This is in fact the primary reason I got the translation table in the first place, so I could identify the correct xmltvid number for the channels I am receiving. But, unless I can get the sub-channel number from MythTV, it is proving useless.

I've never noticed mythtv having a problem distinguishing unencrypted QAM from encrypted, but I guess your mileage may vary. Mythtv does not keep track of the local cable provider's arbitrary virtual channel assignment; it only detects transport "channel" and "subchannel". The virtual channel number assignments and adding the xmltvid numbers are a manual process. 

The one site I know of which keeps track both of transport channel numbers and the cable provider's virtual assignment in a particular area is the HD Homerun site: [http://www.hdhomerun.com/hdhomerun/channels_us](http://www.hdhomerun.com/hdhomerun/channels_us) But this site is sometimes slow to be updated and may have errors. Otherwise, the stations just have to be identified initially by watching them.

---

### Post by AKADAP on 2009-06-09
> **klc5555 said:**
> I've never noticed mythtv having a problem distinguishing unencrypted QAM from encrypted, but I guess your mileage may vary. Mythtv does not keep track of the local cable provider's arbitrary virtual channel assignment; it only detects transport "channel" and [SIZE="4"]"subchannel"[COLOR="Red"][/COLOR][/SIZE]. The virtual channel number assignments and adding the xmltvid numbers are a manual process. 



I am well aware of this. I am not asking for automatic translation, I am asking for some way to get MythTV to report that subchannel number so I can do the translation manually. So far, I have not been able to access that number, and no it is NOT the number after the number sign in the "UNKNOWNchannelnumber#randomnumber" channel name mythTV creates for each channel it detects.

One would think that since mythweb shows the "freqid" which is the channel number, they would also show the "subchannel", but they don't, So I get lists with 20 or 30 channels that all claim to be on channel 96 with no way of determining which is which besides watching each channel until they just happen to show a station ID.

MythTV allows one to manually enter a channel, but they only allow you to manually enter the channel number, not the subchannel. This makes it useless for manually entering digital channels.

BTW, I discovered that MythTV does not detect unencrypted channels very well by doing a channel scan with the hide encrypted channels check box checked, then looking for and not finding some channels I knew I should have been getting and not finding them. I rescanned with that checkbox off, and found the channels I was missing along with several hundred encrypted channels that really confuse MythTV when you accidentally tune to them.

---

### Post by AKADAP on 2009-06-09
It appears that people are misunderstanding what I am asking for, I will attempt to clarify.

MythTV has several pieces of information:
It REQUIRES channel frequency (indexed by freqid which is the usual old style analog channel number).
It REQUIRES [COLOR="Red"][SIZE="4"]subchannel[/SIZE][/COLOR] number to pick out the proper stream from the tuned frequency. This is the number that I can not get access to for reading or writing.
It allows the attachment of a call sign, eg "KGO"
It allows the attachment of a channel name, eg "San Fransisco ABC station"
It allows one to edit the channel number (this is the number you enter to get MythTV to tune that station while watching live TV).
It requires you to manually enter the xmltvid so it knows which schedule goes with which channel.

So, I WANT to add the xmltvid to each station mythTV has found. To do this, I have extracted a list of comcast stations from Schedules Direct that for each station has:
Comcasts random channel number assignment
the xmltvid number
for MOST but not all stations, it also has the callsign, and a description of the channel.

Using a program I downloaded from the AVS forum, I was able to xtract from the broadcast comcast uses to tell their cable boxes what frequency their channels are on, a list of channels that contains:
The frequency to tune for the channel
The old analog cable style channel number
The [COLOR="Red"][SIZE="4"]subchannel[/SIZE][/COLOR] number
Comcast random channel number assigned to this channel
The name of this channel (note that these do not exactly match the names or descriptions that Schedules Direct has)

What I'd like to be able to do is go to a mythTV channel, look up the channel number (which I can get), and the subchannel (which I can't), use this information and the extracted table to figure out Comcasts random channel number, then take this random channel number to the schedules direct list to look up the xmltvid for this station so I can enter that number into the mythTV data for this channel so I can get schedules for this channel.

Have I finally made it clear that without extracting the subchannel number that mythTV MUST have in order to be able to tune the channel in the first place, that I can not get the xmltvid number from schedules direct? I mean, yes I could guess, and be right most of the time, but I'd rather just find a way to access the subchannel directly and eliminate the uncertainty.

---

### Post by AKADAP on 2009-06-11
Is there some tool that I can use to access the MythTV database in some human readable form?

---

### Post by inovermyhead on 2009-06-12
akadap,

I've been struggling with precisely the same problem you describe for over a week now and haven't found an acceptable solution either. I wasn't aware of AVS Forum utility you mentioned(I'm also on Comcast, in Atlanta GA).  I found my digital channels by scanning with my HD TV.   The TV shows the digital channels as "ACTUAL-VIRTUAL" for example 81-21, 103-101, etc.  For some transports, the assignments are nice and straightforward, for example 103-101, 103-102 ... 103-112.  Assigments for other transports seem completely haphazard, e.g. 93-1, 93-3, 93-8, 93-12, 93-56, 93-75, 93-111.  However, all of the actual and virtual channel designations assigned by my TV's scan correlate precisely with the TV channel listings for my zip code on the hdhomerun site, so the assignments are clearly determined by some bit of information in the stream from Comcast.  Information which I can only assume mythtv should also be privy to.

The mythtv backend scan on the other hand results in all of the channels showing as UNKNOWN(no surprise there), and the designations as for example 103#0, 103#1...103#10 in the first case, and 93#0, 93#1...93#6 in the second case.  Unfortunately, nowhere in the channel info table in mythweb is the virtual channel shown.  For example all of the 103 channels list the same information in the freqid and finetune columns, 103 and 0 respectively.  The channum, callsign and name columns are unique but this looks to be just textual information, not anything used for tuning purposes.  As you said, mythtv knows how to tune the channels so the data(virtual channel) has to be in there somewhere, it just isn't showing it to us in mythtweb.

Annoying, but I figured no big deal, they're probably assigned in order sequentially, so 103-101 must correlate to 103#0, 103-102 to 103#1, 93-1 to 93#0, and 93-111 to 93#6.  I checked just a few of these by tuning them in the mythtv frontend and they seemed to line up that way.  I then set about editing in the xmltvid's in mythweb using this assumption.  I got through just a few of my channels when I realized this assumption was in fact incorrect, they don't align as one would think intuitively, so several of the assignments I entered were wrong(i.e. wrong xmltvid for a given ACTUAL#VIRTUAL channel), and of course once I hit the first misaligned channel on a given transport, all of the rest on that transport were off also.  Irritating all get out.

With no logical correlation that I can divine, the only way to tell which channel is which is by tuning every bloody one manually.  With the frontend hanging or crashing left and right every time it hits a channel entry it doesn't like, and then having to wait for commercials to end and a logo to appear, this is even more of a PITA than one might think.  Making matters even worse, the channel name is often truncated in the mythtv frontend so I sometimes can't even tell what ACTUAL#VIRTUAL channel I'm trying to identify.

Let me know if you find an acceptable solution.  I'll do the same.

inovermyhead

---

### Post by AKADAP on 2009-06-12
I just went through and hid all of the encrypted channels on my system. There were 264 of them and it took about a minute each to verify that an encrypted channel was encrypted.

I do not have any other QUAM tuners other than the ones in my MythTV system. No HDTV tuner or cable box to use as a reference. When I have checked the Silicon Dust website, it has been wrong for my cable system.

The tool that was on the AVS form (look under the San Fransisco Comcast thread, it is burried in there somewhere) extracts the list that is sent to the boxes for basic cable. This is only a subset of the channels, and only seems to cover extended basic service, and only standard definition channels. On top of that, it is in a nonstandard format, so this tool will only work on Comcast cable systems. It also requires a DVB (a tuner card), it does not work with HDHomeRun.

From the discussion on the AVS forum it appears that Silicon Dust is working on a solution for the HDHomeRun, but it appears that is a windows only solution.

---

### Post by LowSky on 2009-06-12
maybe you should ask your quesiton here?
[http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/)

---

### Post by inovermyhead on 2009-06-12
Regarding the hdhomerun listings being incorrect, I recall this being a problem for me 9 months ago when I first got the HD TV and was looking to double-check whether I was pulling in all the stations that I should.  I seem to remember that I was able to pick a nearby zipcode and from that find a TV listing that did correspond correctly.  I think it was assuming I was on a different Comcast headend than I actually was, though they've corrected it since.  You might also try entering some adjacent zipcodes at the silicondust site and see if that helps.

---

### Post by inovermyhead on 2009-06-12
Well after some more googling I've found out that among the interesting fields in the database that mythweb isn't showing us are: mplexid, serviceid, and atscsrcid.  Now I need to figure out how to properly get into and work mysql so I can dump them manually from the command line.  It doesn't look like there's any way to customize mythweb to display them.

---

### Post by AKADAP on 2009-06-12
> **inovermyhead said:**
> Well after some more googling I've found out that among the interesting fields in the database that mythweb isn't showing us are: mplexid, serviceid, and atscsrcid.  Now I need to figure out how to properly get into and work mysql so I can dump them manually from the command line.  It doesn't look like there's any way to customize mythweb to display them.

If you figure this out, please post how you did it.

---

### Post by AKADAP on 2009-06-12
> **inovermyhead said:**
> Regarding the hdhomerun listings being incorrect, I recall this being a problem for me 9 months ago when I first got the HD TV and was looking to double-check whether I was pulling in all the stations that I should.  I seem to remember that I was able to pick a nearby zipcode and from that find a TV listing that did correspond correctly.  I think it was assuming I was on a different Comcast headend than I actually was, though they've corrected it since.  You might also try entering some adjacent zipcodes at the silicondust site and see if that helps.

It is unlikely that any of them are correct at the moment since Comcast has been playing musical channels lately. A handful of channels got shuffled around, unfortunately, this requires a complete rescan on mythTV.

---

### Post by AKADAP on 2009-06-13
> **LowSky said:**
> maybe you should ask your quesiton here?
[http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/)

That forum is rather slow. I posted there yesterday, and today, 18 hours later, my post is still the most recent post on that forum.

---

### Post by inovermyhead on 2009-06-15
Sorry it took so long but the wife had too many overdue "honey do" projects this past weekend and had no intention of allowing me to spend it hunched over the keyboard playing with my toy.  Frustrating since I new I was close.

Anyway, the difficulty I had was trying to figure out how to correctly get into mysql with permissions and what not, and also how to select the right database.  I'm a complete linux and mythtv noob and had never done any of that before.  I'm on mythbuntu 9.04 release version.  In my case, to get into the database I typed the following at a terminal command line:

[INDENT]mysql -u root -p mythconverg

[/INDENT]I then entered the password when prompted(mythconverg is the name of the db, and -p tells it to prompt for a password, I think).  

That got me the mysql prompt which is what I'd been trying to do since Friday.  Didn't expect it to take me this long to figure it out but I find that this stuff is humbling me daily.  From there it was easy, lots of examples of how to use the "select" command to display individual channel table entries or the whole table based on some specified criteria.  In my case I just asked it to dump all rows with sourceid 2 which is what all of the channels found in the scan from the backend were assigned to(as also displayed in mythweb).  Not sure what fields are most interesting to you but in my case it was the serviceid field which corresponds to the virtual channel.  I used the following select command to yield a nicely formatted table that has everything I'm interested in:

[INDENT]mysql> select xmltvid, channum, callsign, name, freqid, serviceid, mplexid, atscsrcid from channel where sourceid='2';

[/INDENT]I chose to use basically the same column order as the "channel info" table in mythweb so that I can now easily cross reference between the two as I make the changes in mythweb.  

Hope this is helpful to you also.

---

### Post by AKADAP on 2009-06-16
> **inovermyhead said:**
> Sorry it took so long but the wife had too many overdue "honey do" projects this past weekend and had no intention of allowing me to spend it hunched over the keyboard playing with my toy.  Frustrating since I new I was close.

Anyway, the difficulty I had was trying to figure out how to correctly get into mysql with permissions and what not, and also how to select the right database.  I'm a complete linux and mythtv noob and had never done any of that before.  I'm on mythbuntu 9.04 release version.  In my case, to get into the database I typed the following at a terminal command line:

[INDENT]mysql -u root -p mythconverg

[/INDENT]I then entered the password when prompted(mythconverg is the name of the db, and -p tells it to prompt for a password, I think).  

That got me the mysql prompt which is what I'd been trying to do since Friday.  Didn't expect it to take me this long to figure it out but I find that this stuff is humbling me daily.  From there it was easy, lots of examples of how to use the "select" command to display individual channel table entries or the whole table based on some specified criteria.  In my case I just asked it to dump all rows with sourceid 2 which is what all of the channels found in the scan from the backend were assigned to(as also displayed in mythweb).  Not sure what fields are most interesting to you but in my case it was the serviceid field which corresponds to the virtual channel.  I used the following select command to yield a nicely formatted table that has everything I'm interested in:

[INDENT]mysql> select xmltvid, channum, callsign, name, freqid, serviceid, mplexid, atscsrcid from channel where sourceid='2';

[/INDENT]I chose to use basically the same column order as the "channel info" table in mythweb so that I can now easily cross reference between the two as I make the changes in mythweb.  

Hope this is helpful to you also.

Thank you. This worked. Now I should be able to identify the two unidentified channels and fix a few I misidentified.

---

### Post by AKADAP on 2009-06-16
I was able to fix 4 errors in my list of 410 channels, as well as identify the two unknown channels.

Thank you, that was exactly the information I was looking for. :)

---

### Post by inovermyhead on 2009-06-16
I'm glad it worked for you.  I'm still fixing mine.  Once I had all the data in front of me I realized I had things even more screwed up than I originally thought. It gave me a headache after a few minutes so I decided to put it off and go to bed.

---

### Post by Mister.Vash on 2009-06-18
It may make things easier if you install phpmyadmin on mythbuntu box.  See the sticky thread "Become famous, post your MythTV related How-to's here", [http://ubuntuforums.org/showthread.php?t=751719](http://ubuntuforums.org/showthread.php?t=751719) at the top of the forum for a link on how to do so.

Within phpmyadmin, you can open the mythcoverg database, go into the channel section, then browse it, you can then either edit individual entries or do an import/export from there.  Just a nice easy way to be able to see the data in rows and columns and be able to edit it live.  It does show the mplexid serviceid atscsrcid etc and you can easily sort by those or any of the other fields from within the database.

---

### Post by inovermyhead on 2009-06-19
I had already managed to clean up what I needed to in my channel table but I looked at and bookmarked your link.  Good stuff, and I'm sure it will come in handy sooner or later.  Thanks for the tip.

---

