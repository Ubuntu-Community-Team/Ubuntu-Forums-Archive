---
title: "HDHR ATSC Multiple Channels per Tuner?"
date: 2015-09-16
forum: Mythbuntu
---

### Post by lordviperz on 2015-09-16
I'm assuming but would like confirmation. I assume the HDHR cannot record 2 different ATSC channels on a tuner like it can on cable. With cable, as long as the 2 channels are on the same stream, only one tuner is used. But with ATSC I assume it can only record one channel. But what happens if I'm recording 2 shows on the same channel at different times but over record one of the shows?

For example, say I want to record Show A at 8 and Show B at 9. Both shows are on the same channel but I set Show A to record 30 minutes after the end. I do this in case a show starts late. Will I be using 2 tuners for this because tuner 1 is busy recording Show A when Show B starts?

---

### Post by MoebusNet on 2015-09-16
I'm a newbie to Mythbuntu but my experience is that OTA & cable both will alternate tuners: ie tuner 0 records first program, tuner 1 records second program, tuner 0a records third program, tuner 1a records fourth program. Tuners 0a & 1a are only used if on subchannel of tuner 0 or 1. For example tuner 1 records channel 23-1, tuner 1a can record only channel 23-x (OTA). This behavior may change based on backend setup.

---

### Post by lordviperz on 2015-09-16
Thanks for the reply. So now I'm wondering if Show A is set to record from 8pm to 9:30pm and it's using tuner 0, will Show B use tuner 0a if it's on the same channel at Show A but starts at 9pm?

---

### Post by MoebusNet on 2015-09-16
Interesting question. Because my local cable company places channels seemingly at random, I haven't found a good way to know which channels are a subchannel of others. OTA channel labelling seems much more straightforward to me. My example of OTA channel 23-1 with subchannels 23-x speaks to that. In a practical sense, you don't really care because Myth will tell you if there is a conflict. You can Edit Schedule to record a program only at that time, or at any available time to resolve conflicts. I'm still learning to use recording priorities, schedule options, storage options, post processing options, etc.

---

### Post by lordviperz on 2015-09-16
I'm currently setup on cable but dropping it for OTA soon. I'm trying to figure out how many atsc tuners I will need to record without conflicts. My cable setup uses 1 tuner and can record 2 shows on the same stream. My cable company has ABC, CBS and FOX on one stream. ABC and The CW are one 2 other streams. I have 2 HDHR Dual tuners and because max recordings is set to 2 for each tuner, I have up to 8 tuners. However I have only seen mythtv use 1 of the tuners on the second HDHR. 95% of the time it only uses the 2 tuners on the first HDHR utilizing the same streams.

I record almost everything on the local networks and a few on The CW. So that's a possibility of 5 tuners needed if there is something on all 5 channels at the same time. Then you add the fact that I've got a handful of shows to end late by up to an hor or more in case some sports programs run over. That's where my calculations for tuners becomes difficult.

If a tuner can record 2 programs on the same channel due to start times overlapping due to end late times, then I might be ok. If not then I need more tuners.

---

### Post by MoebusNet on 2015-09-16
I've got the HDHR Plus (now called Extend) with 2 tuners plus available subchannel tuning. I don't count on having subchannel recording available; YMMV. If/when I get another HDHR tuner it will have the cable card capability and 3 tuners (I forget the model name). Something to consider: the cable company here is hinting that they will be scrambling ALL channels in 2016. Customers will need a cable box or maybe a cable card to descramble even basic limited cable. My TV's tuner will be useless.

---

### Post by lordviperz on 2015-09-16
You're talking about the HDHR Prime. It has 3 tuners and can use a cable card. The prime does not do multiple recordings on a tuner. It also does not do ATSC OTA so it isn't an option for me. My cable company, Wowway, still has open QAM but their pricing is getting way too high so I'm moving to an antenna.

---

### Post by MoebusNet on 2015-09-16
My Mythbox is in my RV; I travel a lot and need both cable and OTA. Thanks for reminding me that the Prime doesn't do OTA recording. OTOH, many places where I need OTA won't have more than 2 programs worth recording at a time! :-)

---

### Post by lordviperz on 2015-09-16
Mythtv in the RV? What a great concept. But my wife would kill me if I geeked out the camper. Then again one could always do something like a plex server and remotely access their recordings from home over the internet. Hummm, got me thinking now.

---

### Post by MoebusNet on 2015-09-16
Biggest limitation is connectivity; most RV campgrounds offer dialup equivalent WiFi. Cellular data is limited by tower availability, data caps, throttling, etc. I mainly use Myth to timeshift. A significant challenge: changing locale in SchedulesDirect plus Mythtv for each new location. Very dependent on connectivity.

---

