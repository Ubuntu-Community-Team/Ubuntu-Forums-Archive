---
title: "2 Mythbuntu Questions"
date: 2009-08-05
forum: Mythbuntu
---

### Post by chip33az on 2009-08-05
Hi!

I have been happily using Mythbuntu for a few months and really like it.  

I do have two questions that I hope someone could help with.

1.  I switched the hard drive copied DVD playbacks to mplayer since I was having issues with the playback from the internal player.  Is there a way to bookmark the playback and resume where I left off?  I did the settings in Mythbuntu, but I don't think they apply to mplayer.  Not that pressing, but still annoying.

2.  I have a PVR 150 card and just set up an HDHR.  I just don't understand how to set up the two together.  The HDHR only grabs the local channels, but not in HD (I gather I have a trap on my cable connection that blocks the HD channels, but I can get the local channels through it).  Since I only have basic cable, I wanted to have 1 listing for all sources.  When I tried to add the HDHR to the same source as my PVR 150 I had nothing but issues (the PVR 150 would try to tune the HD channel i.e. 103.5).  I had to go to schedules direct and create a digital channel group and then used that as a source for the HDHR, but now I have 2 of each channel.  Is there a way to have it listed as only 1 channel (say channel 3) and use all capture cards for it?

Thanks for any suggestions!

---

### Post by klc5555 on 2009-08-05
> **chip33az said:**
> Hi!

I have been happily using Mythbuntu for a few months and really like it.  

I do have two questions that I hope someone could help with.

1.  I switched the hard drive copied DVD playbacks to mplayer since I was having issues with the playback from the internal player.  Is there a way to bookmark the playback and resume where I left off?  I did the settings in Mythbuntu, but I don't think they apply to mplayer.  Not that pressing, but still annoying.

2.  I have a PVR 150 card and just set up an HDHR.  I just don't understand how to set up the two together.  The HDHR only grabs the local channels, but not in HD (I gather I have a trap on my cable connection that blocks the HD channels, but I can get the local channels through it).  Since I only have basic cable, I wanted to have 1 listing for all sources.  When I tried to add the HDHR to the same source as my PVR 150 I had nothing but issues (the PVR 150 would try to tune the HD channel i.e. 103.5).  I had to go to schedules direct and create a digital channel group and then used that as a source for the HDHR, but now I have 2 of each channel.  Is there a way to have it listed as only 1 channel (say channel 3) and use all capture cards for it?

Thanks for any suggestions!

Don't know about 1., but re. 2.: the separate digital channel group (and, more importantly, an "analog channel group") with each group having its own Video Source (in the backend setup) is the correct way to go. The analog version of, say, ch. 3 is really a different channel and channel _type_ from SD 3.1 (or HD 3.2) and should be assigned to a different Video Source than the other two, digital, versions share. 

That's the way Mythtv keeps track of which particular tuner can tune which type of channel, so that when you schedule a recording Mythtv can automagically assign the correct type of tuner to a channel so your recording won't fail. Otherwise you'd have to assign the tuner yourself, manually, and if a conflict cropped up later, Mythtv would still try to reassign tuners itself to cover the schedule clog and likely would assign the wrong type because it couldn't tell the difference.

Similarly, while watching livetv, if you plunk in a channel number that the current tuner can't handle, Mythtv will fire up the correct type of tuner as part of the channel change, without you having to switch inputs manually. It can't do this if analog and digital channels are all glommed into a single Video Source.

The double (and with HD triple) guide listings are just a natural corollary of either you (or Mythtv) deciding which signal you really want to record.

(Your locals ought to also be freely available in HD on clear QAM from your cable provider, if they exist that way OTA in your area. Might want to do another channel scan. The Silicon Dust web site provides a listing by area code of everything digital that ought to be freely available in your area.)

Cheers! :)

---

### Post by chip33az on 2009-08-05
Thank you for the quick response.

Can I create two groups (Analog, Digital) and tie them back to the same listing in Schedules Direct?  Would there be only 1 listing per channel since the Schedules Direct information would be the same?

If so, I would then create the two sources (HDHR, IVTV) to the appropriate group (Analog, Digital) and that should be fine.  The TV listing would show 1 channel, but the tuners would know how to tune the channel.

I have to hack the database to get it working now, so I guess I can try it later today on an unimportant channel.

As for the HD issues, I know the cable company is supposed to allow HDTV even with basic, but talking to their tech support is a nightmare and I have the issue unresolved.  Next time I see a tech in the apartment complex I'm going to ask him.

---

### Post by klc5555 on 2009-08-05
> **chip33az said:**
> Thank you for the quick response.


Can I create two groups (Analog, Digital) and tie them back to the same listing in Schedules Direct?  Would there be only 1 listing per channel since the Schedules Direct information would be the same?

If so, I would then create the two sources (HDHR, IVTV) to the appropriate group (Analog, Digital) and that should be fine.  The TV listing would show 1 channel, but the tuners would know how to tune the channel.

I have to hack the database to get it working now, so I guess I can try it later today on an unimportant channel.

As for the HD issues, I know the cable company is supposed to allow HDTV even with basic, but talking to their tech support is a nightmare and I have the issue unresolved.  Next time I see a tech in the apartment complex I'm going to ask him.

Each group of related channels (say your local CBS analog version, digital version, and HD version) carry identical content and therefore share the same xmltvid number. If all the xmltvid numbers are already set in your current SchedulesDirect profile, you don't change anything with them.

In your Mythtv guide, you will end up with 1 listing for each analog channel, 1 listing for each SD channel, and if you receive it 1 listing for each HD channel. It has to be this way --if you go into the guide and decide you want to record or watch something from there, you decide whether you want to watch or record the program in analog, SD, or HD. Three choices, three separate distinct channels (Analog, SD, HD), therefore, three listings. (Or, without HD, two listings). It's just the broadcast content of the three channels that is identical, the channels themselves are distinct.

Or, as a different example, you might want to watch a program live in SD (or analog) because, say, your particular frontend is underpowered, but at the same time you want to record it in HD for later editing and transfer to a DVD. I've done this a few times. In this case you would be accessing two of these distinct channels with identical content simultaneously on two separate tuners.

If you don't want the listings from analog channels, SD channels, and HD channels to interfile in the guide, you assign these channels different channel number ranges in Channel Editor, or with "e" while watching livetv. Say channel numbers 2-99 for the analogs, 102-199 for the SDs, and 802-899 for the HDs. Likewise from Channel Editor (or "e") you assign the channels different call signs (Myth doesn't care what these are, so long as each one is unique). So that, if one analog channel is, say, "WTTK", then you might assign the SD as "WTTK-DT" and the HD maybe "WTTK-HD".

---

### Post by chip33az on 2009-08-05
Thanks again for the very quick response.

I'm going to have to play around with it.  I still can't get to what I want.

What I would really like is to have 1 of each channel (say 3 - KTVK) listed in the program guide.  From there, I would like to watch the channel and be able to change the source from IVTV (analog) to HDHR (digital) from the OSD.  Since I don't get HD, it seems pointless to have multiple listings when only the picture quality (and tuner) is different.

I'll play with it some more.

---

