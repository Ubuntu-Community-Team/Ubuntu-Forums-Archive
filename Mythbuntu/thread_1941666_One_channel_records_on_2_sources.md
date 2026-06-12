---
title: "One channel records on 2 sources"
date: 2012-03-16
forum: Mythbuntu
---

### Post by comptechgeek on 2012-03-16
About a week or so ago my cbs channel started to duplicate its upcoming recordings to other source.

It only happens on that one channel.  When the recording is over I get 2 different files one from each source.

I have totally removed both sources in the backend setup and re-added and the problem still exists.

If I hide or remove the channel from one source it breaks the other.

How do get it to stop using up both tuners?

Here is my setup:
HDHomerun is connected to OTA antenna
HDPVR is connected to satellite

---

### Post by nickrout on 2012-03-16
> **comptechgeek said:**
> About a week or so ago my cbs channel started to duplicate its upcoming recordings to other source.

It only happens on that one channel.  When the recording is over I get 2 different files one from each source.

I have totally removed both sources in the backend setup and re-added and the problem still exists.

If I hide or remove the channel from one source it breaks the other.

How do get it to stop using up both tuners?

Here is my setup:
HDHomerun is connected to OTA antenna
HDPVR is connected to satellite

HDPVR is NOT connected to satellite because it is not a satellite tuner. I suspect you mean that it is connected to a satellite set top box.

If you want your system to recognise two channels as the same. so as to avoid double recording, I think you need to ensure they have the same xmltvid (assuming an xmltv epg), callsign and channum.

PS mythweb is the easiest place to sort this out.

---

### Post by comptechgeek on 2012-03-16
> **nickrout said:**
> HDPVR is NOT connected to satellite because it is not a satellite tuner. I suspect you mean that it is connected to a satellite set top box.Yea it was late.


The only thing different in mythweb was the channel# and I set it to be the same.  That made only one channel appear in the listings but it still records both sources even though I only select the HDHomerun.  The same happens when I choose the HDPVR.

I then tried to hide the satellite cbs.  This time it did not break the channel.  So now its kinda fixed and only records the HDHomerun source.

---

