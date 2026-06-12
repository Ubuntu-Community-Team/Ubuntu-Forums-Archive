---
title: "tv schedules missing for 2 channels"
date: 2012-02-08
forum: Mythbuntu
---

### Post by nhtrader on 2012-02-08
ubuntu 10.10 (64bit)
xfce 4.8.0
MythTV v0.24.2.7
Cable TV - comcast

I have long given up trying to get the TV schedule for one channel (a PBS channel). I haven't seen its schedule for months. But on Sunday, I lost the ability to see the TV schedule for another channel (NBC).

BTW, I see the schedules for 30 other stations/channels and all other functions of MythTV appear to work fine, except for the fact that for only one channel, MythWeb will only play the Spanish soundtrack (all others english).

Any ideas on how to get MythTV to show these two channels schedules?


=====================
This is what I've tried....

1. I used MythTV BackEnd Setup to rescan channels.
2. I used MythTV BackEnd Setup | 3. Video Sources and tried all three options for "Listings Grabber":
[LIST=1]
[*]Transmitted Guide Only
[*]North America (DataDirect) xmltv
[*]North America ([www.directtv.com](www.directtv.com)) xmltv
[/LIST]3. I used MythTV BackEnd Setup | 3. Video Sources and tried all three options for "Channel Frequency Table":
[LIST=1]
[*]us-cable
[*]us-cable-hrc
[*]us-cable-irc
[/LIST]4. I used the following terminal mode commands:
[LIST=1]
[*]mythfilldatabase --refresh-today
[*]mythfilldatabase --max-days 1
[*]mythfilldatabase --refresh-today --refresh-all
[/LIST]
Still no joy. Both PBS and NBC show schedules "Unknown" despite the fact that when I select these channels the broadcast appears (video and audio work fine). MythTV just doesn't show the schedules.

---

### Post by nickrout on 2012-02-09
> **nhtrader said:**
> ubuntu 10.10 (64bit)
xfce 4.8.0
MythTV v0.24.2.7
Cable TV - comcast

I have long given up trying to get the TV schedule for one channel (a PBS channel). I haven't seen its schedule for months. But on Sunday, I lost the ability to see the TV schedule for another channel (NBC).

BTW, I see the schedules for 30 other stations/channels and all other functions of MythTV appear to work fine, except for the fact that for only one channel, MythWeb will only play the Spanish soundtrack (all others english).

Any ideas on how to get MythTV to show these two channels schedules?


=====================
This is what I've tried....

1. I used MythTV BackEnd Setup to rescan channels.
2. I used MythTV BackEnd Setup | 3. Video Sources and tried all three options for "Listings Grabber":
[LIST=1]
[*]Transmitted Guide Only
[*]North America (DataDirect) xmltv
[*]North America ([www.directtv.com](www.directtv.com)) xmltv
[/LIST]3. I used MythTV BackEnd Setup | 3. Video Sources and tried all three options for "Channel Frequency Table":
[LIST=1]
[*]us-cable
[*]us-cable-hrc
[*]us-cable-irc
[/LIST]4. I used the following terminal mode commands:
[LIST=1]
[*]mythfilldatabase --refresh-today
[*]mythfilldatabase --max-days 1
[*]mythfilldatabase --refresh-today --refresh-all
[/LIST]
Still no joy. Both PBS and NBC show schedules "Unknown" despite the fact that when I select these channels the broadcast appears (video and audio work fine). MythTV just doesn't show the schedules.

Why aren't you using schedules direct?

---

### Post by LowSky on 2012-02-10
More than likely the listings channel ID and the one from your list do not match.. These things happen and you need to edit them in the channel lineup.

You should also be using SchedulesDirect. Yes it cost money but you get the correct lineups.

---

### Post by nhtrader on 2012-02-13
> **LowSky said:**
> More than likely the listings channel ID and the one from your list do not match.. These things happen and you need to edit them in the channel lineup.

You should also be using SchedulesDirect. Yes it cost money but you get the correct lineups.

Well, not understanding how to edit the "channel lineup", I did the following:

1. Entered MythTV BE Setup
  a. selected "5. Channel Editor" - everything looked correct. changed nothing.
  b. selected "4. Input Connection" - everything ok. changed nothing.
  c. selected "3. Video Input" - everything ok. changed nothing.
  d. exited BE.

Summary: didn't find a spot to edit "channel lineup"

2. Opened browser and entered 127.0.0.1/mythweb
   a. selected Settings Menu.
   b. selected from left column "TV"
   c. selected from right side upper tab "Channel Info"
   d. scanned list - everything looks ok. But for kicks, I changed channel 207_1 freq id from 82 to 83 then selected save. Then I changed it the freq id again. I changed it back to 82 and save it (for reason of forcing the database to be changed and updated). 

Summary: the TV schedule still doesn't appear.

However, I don't know if this is what you meant by editing the "channel lineup"?


BTW, as for your reference that I should loosen my wallet and spend a few Dollars to use "SchedulesDirect.org", well, I would ask, why should an open-source project require a paid-subscription to work?

---

### Post by nickrout on 2012-02-13
Because good data costs money.

---

### Post by nhtrader on 2012-02-14
> **nickrout said:**
> Because good data costs money.

I'm disappointed. Normally you are like a laser and get right to the remedy. So it surprises me that you are using your expertise to promote a paid-subscription. 

Whereas the salient point is that there may be a bug in MythTV if a user manually rescans for TV channels and it still can't clear out a mismatch in the master database. In addition, if there is no way for a user to manually fix this event, even if they try 3 different listings grabbers, something is broken.

I was hoping that you would know a remedy for this. Throwing money at it (buying a subscription) doesn't change the fact that the other options provided don't work. This is still a problem, unless the MythTV team has abandoned these options; demoted these other options toward obsolescence; or has limited it's future development to only one listings grabber. In that case, "where's the memo"?

---

### Post by nickrout on 2012-02-15
You need to ensure:

1. that your listings provider (xmltv, and open source project which collects data from various sources, which may or may not be reliable) covers your channel.

2. that the xmltvid used by the xmltv source is matched in the database. This is easy to line up in mythweb (Settings|TV|Channel Info).

3. Your xmltv config file is set to process that channels's info (~/.mythtv/Sourcename.xmltv)

In the rest of the world we have to put up with random xmltv data of very variable quality. The data is usually either scraped from TV company websites, or obtained from EIT. It is sometimes massaged because the data is usually poor from either source. (Try recording every episode Dr Who, or is it Doctor Who or is it Dr. Who). In the US you have a brilliant service from SD. Make use of it, its very cheap.Believe me, you won't get better.

Also scraping a website against the website's T&C's is totally opposite to the ethos of open source. Open source respects copyright, in fact depends on it for its very existence.

So by paying, what is it $20 per year, you are respecting copyright, supporting the ethos of open source and getting damn good data.

---

### Post by nhtrader on 2012-02-15
> **nickrout said:**
> 
2. that the xmltvid used by the xmltv source is matched in the database. This is easy to line up in mythweb (Settings|TV|Channel Info).

3. Your xmltv config file is set to process that channels's info (~/.mythtv/Sourcename.xmltv)


Thanks for your insight into locating a file/database.


I scanned for the file you mentioned. This is what I found for MythTV v0.24.2-11

DIR: /home/mythtv/.mythtv/channels -> empty DIR
DIR: /home/mythtv/.xmltv -> empty DIR

DIR: /home/myusername/.mythtv/channels -> empty DIR
FILE: /home/myusername/.mythtv/Comcast.xmltv -> file length is 0 bytes

DIR: /home/myusername/.xmltv/supplement/tv_grab_eu_epgdata
FILE: /home/myusername/.xmltv/supplement/tv_grab_eu_epgdata/channels_ids -> 9207 bytes
FILE: /home/myusername/.xmltv/supplement/tv_grab_eu_epgdata/channels_ids.meta -> 130 bytes

The content of file "channels_ids" is

71;ard.de
37;zdf.de
38;rtl.de
39;sat1.de
40;prosieben.de
44;kabel1.de
41;rtl2.de
42;vox.de
43;superrtl.de
56;3sat.de
58;arte-tv.com
486;das-vierte.de
47;ndr.de
46;wdr.de
50;swr.de
51;br-online.de
#;3.br-online.de
104;alpha.br-online.de
48;mdr.de

(restricted contents to fist 20 lines b/c none of the entries were what I expected, which is an xml table of tv channels, freq_id, xmltv_id, etc)

The contents for channel_ids.meta is only contains 3 lines of data:
LastUpdated 1329149832
Url [http://supplement.xmltv.org/tv_grab_eu_epgdata/channel_ids](http://supplement.xmltv.org/tv_grab_eu_epgdata/channel_ids)
Last-Modified Sun, 01 Aug 2010 16:00:25 GMT

(again nothing what I expected to find)



Still no luck in finding the database which possibly contains the wrong TV channel info.

---

### Post by nickrout on 2012-02-16
When you set up xmltv properly through mythtv-setup it puts xmltv's setup file in ~/.mythtv/Sourcename.xmltv, where Sourcename is the name of the Video Source you set up. eg I have Freeview.xmltv and FreeviewHD.xmltv for my two Video Sources.

If you don't have such a file, you didn't set up xmltv through mythtv-setup.

Frankly I cannot recall whether this is created in ~mythtv or ~userwhoranmythtv-setup but I see you checked both anyway.

Anyway, you seem to have xmltv working after some fashion, so have you checked the xmltvid matches up in mythweb (Settings|TV|Channel Info)

Lastly (or probably firstly) are you even sure your xmltv script has support for the channels you are missing data for?

---

### Post by nhtrader on 2012-02-16
> **nickrout said:**
> 
Lastly (or probably firstly) are you even sure your xmltv script has support for the channels you are missing data for?

I don't know what you mean. What/which xmltv script? How do I manually run this script? How do I verify it was run?

But taking a stab at your statement, I assume so b/c all 11 TV channels share the same freq_id. They are all multiplexed to the same frequency. So the schedules for 9 channels appear and only 2 are missing. Again, the issue is why can't it read the EIT for these two channels but it can for the other 9?

BTW, I have elected to restrict my MythBox's TV recording ability to these 11 channels b/c they are multiplexed. This way I can utilize the power of MythTV and record 5 programs simultaneously. And if I were to allow all users access to the other channels, it would make it too complicated for everyone else in the house to understand the rules of using a single tuner for multiple simultaneous recordings.

---

### Post by nickrout on 2012-02-16
Your first post said you were using xmltv, so assumed you had given up on EIT (which is widely regarded as pretty hopeless in the US).

So are you using xmltv or EIT?

---

### Post by nhtrader on 2012-02-16
> **nickrout said:**
> Your first post said you were using xmltv, so assumed you had given up on EIT (which is widely regarded as pretty hopeless in the US).

So are you using xmltv or EIT?

Now you're getting to crux of my ignorance. I was under the impression that the two were the same. EIT = xmltv. That EIT is stored in xml format. Clearly, I don't know.

All I did is is explore the options cited earlier( datadirect; directtv; EIT). And I searched for files as described earlier (no *.xmltv). 

This explains why I created a new thread asking for help in transferring a TV schedule from one channel to another. I felt that it would be wise to keep these two question separate for future reference ( which I routinely use ).

---

### Post by nickrout on 2012-02-17
> **nhtrader said:**
> Now you're getting to crux of my ignorance. I was under the impression that the two were the same. EIT = xmltv. That EIT is stored in xml format. Clearly, I don't know.

All I did is is explore the options cited earlier( datadirect; directtv; EIT). And I searched for files as described earlier (no *.xmltv). 

This explains why I created a new thread asking for help in transferring a TV schedule from one channel to another. I felt that it would be wise to keep these two question separate for future reference ( which I routinely use ).

Ahhh I see why we have been at cross purposes!

EDIT: It's $25, but the point is no different. Under 50c per week.

EIT data is part of the DVB standard and the EPG info is in the DVB stream from the broadcaster. It's quality and availability depends on your provider. eg freeview|HD in New Zealand only provides EIT info for now and next - ie what is playing now and what is next on the channel. EIT in the US is widely regarded as a crap source.

xmltv is a separately developed open source program which downloads EPG data in xml format. It relies on "plugins" or "downloaders" for each "market". Those downloaders may ultimately scrape TV websites, or get them from some aggregator who scrapes web sources and makes the resulting xml files available to all and sundry. In both cases the T&C of the source websites are probably breached.

Myth can use either, or schedules direct, with SD being the best and most accurate data. Accurate data is the foundation of a PVR and your reluctance to pay $20 per year does yourself a disservice.

Call yourself an open source enthusiast, but reluctant to take a licensed and completely legal service. It simply doesn't make sense.

---

