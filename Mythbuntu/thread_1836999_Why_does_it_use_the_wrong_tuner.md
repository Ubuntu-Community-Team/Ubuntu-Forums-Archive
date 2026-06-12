---
title: "Why does it use the wrong tuner?"
date: 2011-09-01
forum: Mythbuntu
---

### Post by movieman on 2011-09-01
So one of our TV stations just switched from analogue to digital. I deleted the old channels from MythWeb and scanned for channels and the channel exists on my digital tuner but not the analog.

So why is MythTV determined to record programs on that channel using the analog tuner where the channel doesn't exist, rather than the digital tuner where it does?

What's particularly bizarre is that MythTV normally seems to pick the tuner with the lowest ID, yet in this case it's skipped over the two digital tuners which can actually record the channel (2 and 3) and using tuner 4 which can't.

---

### Post by movieman on 2011-09-01
Oh, and it does this even when I set the 'preferred input' to be an actual input that's actually capable of actually recording the actual channel.

---

### Post by klc5555 on 2011-09-01
Reminds one how useless mythweb actually is.

In your real mythbackend setup, you presumably have (at least) two Video Sources set up, one for Digital and one for Analog. The Digital Video Source is presumably coupled to your digital tuner in Input Connections, while the Analog Video Source is presumably linked to the analog tuner in Input Connections. Each of the two Video Sources presumably has its own singular list of channels and frequencies, the one digital and the other analog.

The defunct analog channel(s) should be individually deleted in Channel Editor from the Analog Video Source. 

The digital tuner should be rescanned in Input Connections on your Digital Video Source. When it has found the new digital version of the defunct channel, go into Channel Editor and assign this new digital channel a virtual channel number that is slightly different than the old analog channel's number was. (If the analog channel was, say, "44" make the digital version, say, "4401". 

In this screen for your new digital channel in Channel Editor, add the xmltvid number for the listings in Schedules Direct in the right box and (this is important) give the digital station a slightly different callsign and name than the analog version of the station had, say, "WWTW-SD" instead of "WWTW". Mythtv tells channels apart first by callsign, rather than channel number or xmltvid. Identical callsigns always confuse mythtv.

Finish up, exit, and run: 

mythfilldatabase --refresh-today --refresh-all 

to get the listings correct and up to date on the new channel and to eliminate traces of the old one from the scheduler for the next two weeks, and you're done.

---

### Post by tgm4883 on 2011-09-01
Yep, disconnect the analog recorder in mythtv-setup. Problem solved.

---

### Post by movieman on 2011-09-01
> **klc5555 said:**
> Each of the two Video Sources presumably has its own singular list of channels and frequencies, the one digital and the other analog.

Uh, no. Schedules Direct only has one listing for this post code so it contains both digital and analog channels; I'm amazed that MythTV will skip over two tuners which can record a channel in order to pick a tuner that definitely can't.

I eventually had to set up a second lineup on Schedules Direct for a different post code so that I could set one to be just the digital channels and one to be just the analog channels. That's dumb.

---

### Post by klc5555 on 2011-09-02
SchedulesDirect itself has nothing really to do with how your backend and Video Sources are configured. SchedulesDirect just supplies program scheduling data in accordance with xmltvid numbers. It doesn't know how your Video Sources are set up, nor whether particular tuners exist, nor whether they are digital or analog. Mythfilldatabase will pull down a selection of this undifferentiated mass of SchedulesDirect data by itself proceeding Video Source by Video Source in accordance with what xmltvid numbers you have given to channels you have configured in each individual Video Source. 

You can use the exact same single ScheduleDirect lineup across two Video Sources or twelve, if you had twelve tuners and reason to be that specific with what channels were being fed to which tuners. Because of lirc configurations across three backends, I have 5 separate Video Sources configured. But I only need the one SchedulesDirect lineup for my zipcode.

The point is that if a particular channel had been deleted from a particular Video Source feeding a particular tuner in your Channel Editor, and mythfilldatabase had been run, the Mythtv scheduler could not schedule a recording on that defunct channel which had been removed from that Video Source, because the Mythtv scheduler would no longer know that the channel existed.

But you have to configure the mythtvbackend properly; this isn't something done in mythweb.

---

### Post by tgm4883 on 2011-09-02
> **movieman said:**
> Uh, no. Schedules Direct only has one listing for this post code so it contains both digital and analog channels; I'm amazed that MythTV will skip over two tuners which can record a channel in order to pick a tuner that definitely can't.

I eventually had to set up a second lineup on Schedules Direct for a different post code so that I could set one to be just the digital channels and one to be just the analog channels. That's dumb.

Yep, it sure is dumb that you had mythtv setup incorrectly.

---

### Post by movieman on 2011-09-03
> **klc5555 said:**
> You can use the exact same single ScheduleDirect lineup across two Video Sources or twelve, if you had twelve tuners and reason to be that specific with what channels were being fed to which tuners. Because of lirc configurations across three backends, I have 5 separate Video Sources configured. But I only need the one SchedulesDirect lineup for my zipcode.

How? All I can do is set up one lineup for my post code. I don't see any way to tell MythTV to ignore certain channels from that lineup for certain tuners.

And the fact remains that the channel is physically not recordable on that tuner -- a scan doesn't find it -- so no sane program would try to use it anyway.

Honestly, you do really think that people will flock to MythTV when it can't even pick a tuner based on whether it's capable of actually recording a channel? That's such a basic piece of functionality that my mind is simply boggling at their decision not to perform such a check before recording.

---

### Post by movieman on 2011-09-03
> **tgm4883 said:**
> Yep, it sure is dumb that you had mythtv setup incorrectly.

Thanks for your helpful comment.

So please, could you tell me where in mythtv-setup this magical setting is that I've configured incorrectly? Because I sure can't find it.

---

### Post by klc5555 on 2011-09-03
> **movieman said:**
> How? All I can do is set up one lineup for my post code. I don't see any way to tell MythTV to ignore certain channels from that lineup for certain tuners.

And the fact remains that the channel is physically not recordable on that tuner -- a scan doesn't find it -- so no sane program would try to use it anyway.

Honestly, you do really think that people will flock to MythTV when it can't even pick a tuner based on whether it's capable of actually recording a channel? That's such a basic piece of functionality that my mind is simply boggling at their decision not to perform such a check before recording.

I'm not here to defend Mythtv, I'm just trying to help you configure it more-or-less correctly. You haven't done so. It therefore does not do what you expect it to do.

So, to repeat: the standard way to accomplish what you're trying to do is to set up one Video Source for your analog tuner(s) and one Video Source for your digital tuner(s). These two Video Sources will use The SAME SchedulesDirect lineup in their SchedulesDirect grabber. You will bind the Digital Video Source and the Analog Video Source each to the appropriate tuner in Input Connections. You will also scan for visible channels on each tuner in Input Connections. 

In the Channel Editor, you will be able to edit or delete any of the channels, which are organized according to the Video Source they were assigned to during your channel scans in Input Connections. The usual editing for the QAM digital stations will include adding the xmltvid numbers for the SchedulesDirect programming info, assigning unique callsigns and names, and assigning virtual channel numbers to these digital channels that differentiate them SD from HD within the Digital Video Source and also from their analog counterparts in your program schedule. Xmltvids, callsigns, and names may also be added to the channels found under the Analog Video Source.

If an erroneous channel is found --in my case analog "48" is not ESPN Classic, but rather the Test Pattern Channel, you delete the channel in the Channel Editor by highlighting it and pressing the "d" key.

That's all there is to it.

Now admittedly the backend configuration section of the Mythtv manual [http://www.mythtv.org/wiki/User_Manual:MythTV_structure#Channel_Editor](http://www.mythtv.org/wiki/User_Manual:MythTV_structure#Channel_Editor) has an error their description of the Channel Editor. The sentence that reads: "you cannot use the XMLTV ID of Source 1 as the XMLTV ID for a channel that belongs to Source 2, even if the channels are the same" is incorrect. As long as the programming content is absolutely identical (as it generally is among digital, analog, and HD versions of the same station), you do in fact use exactly the same xmltvid number, even across Analog and Digital video sources. What mythtv uses to keep everything separated for recording purposes is first unique callsign (WTTW-DT as opposed to WTTW and WTTW-HD) and second unique virtual channel assignment for the scheduler ("4401" as opposed to "44") Xmltvid numbers are only relevant for the particular programming schedule package of data they pull down from SchedulesDirect.

But that's a topic for a different day.

---

