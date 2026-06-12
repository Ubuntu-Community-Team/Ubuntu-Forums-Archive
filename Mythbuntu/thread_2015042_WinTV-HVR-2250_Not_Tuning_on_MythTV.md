---
title: "WinTV-HVR-2250 Not Tuning on MythTV"
date: 2012-07-02
forum: Mythbuntu
---

### Post by sbcc on 2012-07-02
Hello,

I am a newbie to all things myth. I have recently set up Mythbuntu 12.04. I have successfully added my WinTV-HVR-2250 with much thanks to LowSky. I have also successfully added channels using scte65scan and creating a sql. I live in the US with Comcast so things have been tough. Right now I can view programming through mplayer with a channels.conf file I created. But when choose Watch TV and select the channel (or any channel) I just get a blue screen. I am running mythbuntu 12.04 64bit and mythtv 0.25.0+fixes.20120410.1f5962a-0ubuntu1. Hardware is Intel i5 and using onboard video. Also when I try to do a scan it shows all channels as locked. Any thoughts on where I am going wrong here?

Thanks

---

### Post by crbnrod on 2012-07-03
If you have a TV w/a digital receiver, you might try plugging the coax going into your mythbox into the TV and make sure you have unencrypted channels to tune. Comcast has spent the past year or so turning off most of the clear-QAM stuff afaik.

I would think you should still be able to get your local broadcast networks on mythtv, but I switched to OTA a year or so ago and haven't really stayed on top of comcast's madness since then.

---

### Post by sbcc on 2012-07-03
> **crbnrod said:**
> If you have a TV w/a digital receiver, you might try plugging the coax going into your mythbox into the TV and make sure you have unencrypted channels to tune. Comcast has spent the past year or so turning off most of the clear-QAM stuff afaik.

I would think you should still be able to get your local broadcast networks on mythtv, but I switched to OTA a year or so ago and haven't really stayed on top of comcast's madness since then.

Hi, yes I did check the feed to make sure the signal was there before attaching it to the tuner. The tuner is working fine. I can tune in all the channels showing up with "scan" using mplayer and VLC. I did notice this morning that after loading the channel data into mysql using the sql from scte65scan I did a mythdatabasefill from the myth backend setup and ended up with all the mplexid fields, on channels that I had enabled in Schedule Direct, in the channel table  changed to "32767" which is well beyond any field in the dtv_multiplex table. Not sure how that came about. I did change one channel back to the correct mplexid but still no joy. I'm sure this is something MythTV related just not sure where.

Is there a way to see what the tuner is doing while myth front end is trying to watch tv?

I tailed the front end log and not much information there other than polling is taking a long time.

Any ideas here would be great. 

I think I may try and load in 10.04 and upgrade into 12.04 see where that gets me.

---

### Post by nickrout on 2012-07-05
> **sbcc said:**
> Hi, yes I did check the feed to make sure the signal was there before attaching it to the tuner. The tuner is working fine. I can tune in all the channels showing up with "scan" using mplayer and VLC. I did notice this morning that after loading the channel data into mysql using the sql from scte65scan I did a mythdatabasefill from the myth backend setup and ended up with all the mplexid fields, on channels that I had enabled in Schedule Direct, in the channel table  changed to "32767" which is well beyond any field in the dtv_multiplex table. Not sure how that came about. I did change one channel back to the correct mplexid but still no joy. I'm sure this is something MythTV related just not sure where.

Is there a way to see what the tuner is doing while myth front end is trying to watch tv?

I tailed the front end log and not much information there other than polling is taking a long time.

Any ideas here would be great. 

I think I may try and load in 10.04 and upgrade into 12.04 see where that gets me.

I think you would be better looking at the backend logs.

---

### Post by sbcc on 2012-07-05
> **nickrout said:**
> I think you would be better looking at the backend logs.

Thanks for replying. 

I tailed both the front end and back end logs. Not much help. I will try and attach a copy. I am trying an older version of mythbuntu currently and will see how that performs.

---

