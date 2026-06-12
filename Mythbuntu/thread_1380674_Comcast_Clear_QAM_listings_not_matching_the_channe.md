---
title: "Comcast Clear QAM listings not matching the channels."
date: 2010-01-13
forum: Mythbuntu
---

### Post by jquintana on 2010-01-13
I have setup my schedulesdirect.org account with Comcast cable in my zip code. I went into the MTVBE setup and downloaded the channel listing again.

Upon exiting the setup I was asked to update the database so I did. However, the channels still do not match the program guide.

Any help is greatly appreciated!

---

### Post by williammanda on 2010-01-14
My experience with comcast, from two different cities, has been just as you described. Once the channels are scanned, I wouldn't have any recognized channels (like nbc, abc, etc...), mainly the channel number was assigned by mythtv. I would open mythfrontend and start watching tv. I would open zap2it for the current tv guide and xlmtv. Once I figured out the channel I would enter the channel data by selecting "e". This would be repeated for all the channels. Then I would open mythbackend and delete all unused channels ie encrypted and then run mythfilldatabase.

---

### Post by klc5555 on 2010-01-14
> **jquintana said:**
> I have setup my schedulesdirect.org account with Comcast cable in my zip code. I went into the MTVBE setup and downloaded the channel listing again.

Upon exiting the setup I was asked to update the database so I did. However, the channels still do not match the program guide.

Any help is greatly appreciated!

They won't. Not by default anyway.

The program guide listing for Comcast's QAM channels will be the virtual channel number that Comcast assigns. What Myth's channel scanner is giving you is the actual physical "channel" and "subchannel" that the signal is being transmitted on over the cable. (You probably see things in the channel listings like "88#6" or the like.)

For each of these QAM channels you happen to receive, you may assign whatever virtual channel number you wish, matching Comcast's listings or not as you prefer (it makes no difference in your ability to schedule and record shows). You can do this either "en masse" from the Channel Editor in the backend setup (which may not be the easiest way), or channel-by-channel from the frontend, by simply watching a channel in livetv, pressing the "e" key for "edit" and then in the popup form entering the desired channel number, the desired callsign ("WZZW-DT", "WUXX-HD" or whatever) and then the xmltvid number for the channel that SchedulesDirect lists for it online. (You may find and print your complete list of these xmltvids by logging into Schedules Direct on the web, check "add a new lineup", and then, instead of adding anything, "preview" the lineup you are actually already using.)

Once your QAM data for all the channels has been added in, as above, then do a "mythfilldatabase --refresh-today" and all the listings and schedules should fill in properly for all your channels. (Or after editing simply "mythfilldatabase" and the schedules data will start filling beginning midnight the next day.)

Comcast also from time to time moves some of its channels around without warning. Myth won't pick this up automatically, and so occasionally you'll need to rescan and adjust.

---

### Post by Saquili on 2011-03-25
mythfilldatabase --dd-grab-all

Worked for me

Hope that helps someone

---

### Post by AKADAP on 2011-03-26
A couple of useful resources:

[http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)
type in your zip code and choose your provider, this will get you a mapping between Comcast channel numbers and the frequency IDs those channels are broadcast on. Beware that this listing is not always accurate, partly because cable networks don't follow zip code boundaries, and partly because cable companies continually change their channel mappings.

scte65scan
[http://www.mythtv.org/wiki/Scte65scan](http://www.mythtv.org/wiki/Scte65scan)
this tool will extract the mappings and callsigns used by the cheap SD set top boxes on Comcasts networks. Unfortunately this only covers the standard definition clear QAM channels (and sometimes not all of them).

In any case you will have to edit the channels to assign the XMLid to each channel. The easiest channel editor I have found is the one in MythWeb.

---

