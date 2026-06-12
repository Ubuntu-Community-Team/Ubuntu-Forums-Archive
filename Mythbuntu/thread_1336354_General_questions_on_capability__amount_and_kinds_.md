---
title: "General questions on capability / amount and kinds of capture cards, etc."
date: 2009-11-24
forum: Mythbuntu
---

### Post by tdiaz on 2009-11-24
I'm looking for some advice, and throwing out some comments on what I'm doing with, and would like to do with, a mythTV install.

I've been wanting to make the all in one server with at least RAID 5 for quite some time now, ever since hacking the original Xbox and experiencing XBMC.  A place to park all those videos and watch them from wherever a client would do it. Enter MythTV. 

So, finally- I put together a dual Xeon 2.8 with 4GB and a 2TB RAID5 with two additional 250GB drives, one of the 250's is for Mythbuntu, (/, swap and an additional partition for whatever)  the other is just for the DVR recordings. The additional 250's will get RAID1 treatment. The RAID5 is for the main deal, media, music, pictures, etc- organization. 

I have currently, a PVR-150 and HVR-1600. so in theory thats three tuners. But it's really two, because Cable QAM is near useless. I could probably get more channels over the air. Even though the silicondust listings show lots more options, there really are not that many as only the local networks + CSPANs are clear QAM. 

Cable companies have used digital/QAM as a way to return to charging you for every TV by virtue of not selling converter boxes. 

So what I have figured out in the last several days:

LiveTV is not a strong point. 

If liveTV is active on a FrontEnd someplace, you can't choose that input/source on another FrontEnd. that means if two people are going to watch TV separately, you need a capture card for each one of them in the BackEnd. (Or PiP sessions). 

What happens then, if LiveTV users are using three FrontEnds and a scheduled recording comes  up? Does a client get the boot, or does the schedule go missed?

Setting up QAM is just a big pain in the..  it seems like a total crap shoot. I think I just decided to try over-the-air on that connection.

Should I presume that each QAM capture source will need it's own cable converter box/IR blaster setup? (unless it's taking in ATSC over-the-air)

FireWire- Is adding channels via FireWire as much of a hassle as QAM and the HVR-1600?

Is that cable box thats connected via FireWire restricted to that FireWire connection, generally? Or can it be used simultaneously with a TV as a cable converter would be normally?

I realize that question may also be equipment specific, and the FireWire box option my provider offers  (Cox, San Diego North) may be the limiting factor, but in general how does it work out?

My idea of the Mythbox is to place the iTunes library on it, iPhoto/Aperture, things like Lynda.com discs, videos downloaded from usenet, etc, on the RAID5. That way content is available wherever I place a front end, (AppleTV, Xbox, etc) and additionally, a webcam pointed toward the west outside. 

I've pretty much concluded I should not use LiveTV if for anything other than testing connectivity. Should I then presume that the quality I'm getting on LiveTV viewing is the same quality that will be recorded? It's somewhat.. awful. Although I'm basing this off analog, which has always looked nasty on a computer monitor. I have yet to view a digital broadcast via MythTV. Even following the HVR-1600 wiki page.

---

### Post by hackmeister on 2009-11-24
> **tdiaz said:**
> 
Should I presume that each QAM capture source will need it's own cable converter box/IR blaster setup? (unless it's taking in ATSC over-the-air)
One of my two capture devices is an HDHomerun. It can do OTA ATSC or unencrypted cable via QAM. Obviously you are limited to open un-encrypted cable channels. This varies greatly depending on who your provider is. The industry trend seems to be only OTA stations are left open (CBS, NBC, ABC, CW, Fox, PBS). I have a 4 way splitter coming in from cable connection. One goes to my cable box, one goes to my cable modem and the remaining two go to my HDHomerun. QAM is a bit of a pain to initially setup but once it done you're good to go. You don't need a cable box or IR blasters. The QAM tuner will tune the frequency for you in a similiar fashion as the Hauppauge PVR150 did with analog signals. Silicondust (the company behind the HDHomerun) has a nice utility telling you what QAM frequencies you should get based on zip and provider. It's very accurate:
[http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us)

I'm one of the co-hosts of the MythTVCast and we did a screen cast of a QAM card setup a while back:
[http://showmedo.com/videotutorials/video?name=7480010&fromSeriesID=748](http://showmedo.com/videotutorials/video?name=7480010&fromSeriesID=748)

Hope it helps in your setup. Let me know if you have questions.

---

### Post by tdiaz on 2009-11-25
Thanks for the reply;

So, in a nutshell this is what I come away with:

The Silicondust listing is what I should be able to get clear QAM.  (Which seems like an awful lot more than just the standard broadcast networks plus CPSAN, but okay.

The channel #-x is where X is the cable channel and the x is where it shows up in the lineup to associate itself with the rest. Or something. I don't get why they are different, but thats besides the point. 

If I go into the schedulesdirect.com site and get the XMLTVID of each of these and enter it in the mythWeb interface, and then do mythfilldatabase, it will work out the rest? 

This, after originally doing a scan?

On the MythFillDatabase, does it do more than just get programming data? Like does it also transfer all the frequency/call name data based on the XMLTVID matching, and no data present?

---

### Post by williammanda on 2009-11-25
> **tdiaz said:**
> If liveTV is active on a FrontEnd someplace, you can't choose that input/source on another FrontEnd. that means if two people are going to watch TV separately, you need a capture card for each one of them in the BackEnd. (Or PiP sessions).

One other option: There is the capability of your existing qam tuner to show / record more than one channel at a time. If you have 2 or more shows on the same transponder you may view them (as long as you setup the tuner for more than 1).

> **tdiaz said:**
> What happens then, if LiveTV users are using three FrontEnds and a scheduled recording comes up? Does a client get the boot, or does the schedule go missed?

If a conflict arises as you stated, mythtv will prompt you to make a decision whether you would like to continue watching live tv or start the recording.

---

### Post by hackmeister on 2009-11-25
> **tdiaz said:**
> 
The Silicondust listing is what I should be able to get clear QAM.  (Which seems like an awful lot more than just the standard broadcast networks plus CPSAN, but okay.
Make sure you only check off the cable system you're subscribed to. By default it will list OTA and all the cable systems available in your area. 

> **tdiaz said:**
> 
The channel #-x is where X is the cable channel and the x is where it shows up in the lineup to associate itself with the rest. Or something. I don't get why they are different, but thats besides the point. 
When you setup the QAM capture device do the scan. Cable 256 is what I used. Make sure you check off to only include unencrypted channels. The scan will take a while. You may also pickup audio only channels. You can remove those later. 

> **tdiaz said:**
> 
If I go into the schedulesdirect.com site and get the XMLTVID of each of these and enter it in the mythWeb interface, and then do mythfilldatabase, it will work out the rest? 
For my QAM channels I create a separate Schedules Direct lineup and only include the channels I can tune in. I then assign them into a channel range that's not used by my other lineup. I use 800-820 range. That insures that only that capture device is assigned when scheduling recordings for that channel. I update the channel listing and XMLTVID fields via mythweb. Once everything is working I'll delete the audio only stations I don't care about.  

> **tdiaz said:**
> 
This, after originally doing a scan?
Correct

> **tdiaz said:**
> 
On the MythFillDatabase, does it do more than just get programming data? Like does it also transfer all the frequency/call name data based on the XMLTVID matching, and no data present?
Mythfilldatabase just pulls down the guide info based on the XMLTVID you manually assigned via Mythweb. Its a pain to setup but once it's done you're golden. One issue I had with manually running mythfilldatabase:
For my QAM card it would only initially pull down a couple of days worth of programming info. I had to leave the box on all night and let the system run mythfilldatabase at it's normally scheduled time. After that I had 14 days of programming for the QAM channels.

---

### Post by williammanda on 2009-11-25
> **tdiaz said:**
> I have currently, a PVR-150 and HVR-1600. so in theory thats three tuners. But it's really two, because Cable QAM is near useless. I could probably get more channels over the air. Even though the silicondust listings show lots more options, there really are not that many as only the local networks + CSPANs are clear QAM.

Do you currently pay for cable tv? If so you should be able to pickup the lineup you pay for on your tuners except for encrypted channels.

> **tdiaz said:**
> Cable companies have used digital/QAM as a way to return to charging you for every TV by virtue of not selling converter boxes.

My personal experience is that I don't use a stb. I pay $13 / month for about 60 channels, unencrypted from comcast. You need to explore not using the stb.

---

### Post by tdiaz on 2009-11-25
Right now I'm paying for "Extended+Basic", from the analog era, the bill has been the same service since the early 90s and just added internet the day they offered it. There was no digital service. 

With a recently bought TV, it picks up about 10 or so channels as QAM clear broadcasts. CSPAN, PBS, and local broadcast networks.

Here's the steps I'm taking, using Mythbuntu Karmic

Delete all the channels
Scan using the digital lineup from schedules direct, cable frequency table, QAM-256 modulation, range 2 through T-1 (166) [X] Only Free

(I'm monitoring the 'channel' table in the database between each of these following steps)

So, when I scan with Cable256, "Cable" settings, with the coax plugged directly to the HVR-1600's digital (black centered) connector. I get about 60 returns, total. When it comes back it finds about 37 "conflicting" channels among various results:

QAM-256 Channel 106 -- Timed out, 11 possible channels
Program 1, Encrypted
Program 2, Encrypted ...
QAM-256 Channel 111 -- Timed out, no signal
QAM-256 Channel 113 -- Timed out, 59 possible channels

When it's done, I get:
Found 8 new non-conflicting ATSC channels.
(I 'insert all')

These are ID'ed as

1008_710, KGTV HD - 1008_107, NBC Plu - 1008_707, 1008_117, NBC US
1008_15 Azteca,  all on 75 freqID
1008_111 V-me, 1008_706 SD6 HD, and 1008_711 KPBS HD, on freqID 79

Found 27 new non-conflicting SCTE channels.

These add with no call signs/names and are assigned in the channum fields:
7, 18, 20, 94, 128-156, 437 and 480. Most of these have the same freqID, 87 with one each on 81, 92, 93, 100, 101 and two on 116. 

Found 37 new conflicting SCTE channels.  (should I just skip them, or are these possibly different than the earlier results they are conflicting with?)'

Next I do "Fetch channels from the listings source" and channel names, xmlIDs are added for things that correspond to channels listed in the lineup. 

I set the ones that fetched no name to invisible and added the XMLID to the few that didn't get it, but got  a name based on a scanned and detected channel #.

Quit setup, let mythfilldatabase run. 

..and I get "Error opening jump program file" on anything I choose.

At one point I was able to watch some shows.

---

