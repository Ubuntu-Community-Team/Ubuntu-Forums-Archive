---
title: "New Script: Daily Show downloader/importer"
date: 2010-07-14
forum: Mythbuntu
---

### Post by handyman5 on 2010-07-14
Since Comcast took away my unencrypted Comedy Central, I've ginned up a script to download the Flash video files from thedailyshow.com, join and transcode them, and then import them into MythTV with full metadata (just as if they'd been recorded). Works for Colbert Report too!

*Removed*

Feedback and suggestions welcome.

Thanks,
Adam

---

### Post by larsolav on 2010-07-14
Awesome, I am going to try this tonight after the kiddos are in bed!
I'm kinda a novice at this stuff, so please forgive me when I ask: what do I do once I click on the link in your post?:grin:

---

### Post by LowSky on 2010-07-14
OR go out and buy a Hauppauge HD PVR, and then you can record any channel you get from your cable box over component cables (up to 1080i)

---

### Post by SnafuFlux on 2010-07-14
[s]FWIW Component can do 1080p.[/s] - never mind, I see the HDPVR only goes up to 1080i.  strange.

also, are there recording flag restrictions on the HDPVR?  I know when I record using the firewire port on, say, a sa3250 STB, I can only record certain channels due to the whole flag thing...

record once, record always, record never...

---

### Post by LowSky on 2010-07-14
> **SnafuFlux said:**
> FWIW Component can do 1080p.

also, are there recording flag restrictions on the HDPVR?  I know when I record using the firewire port on, say, a sa3250 STB, I can only record certain channels due to the whole flag thing...

record once, record always, record never...

I tried doing the record using Firewire and its horrible (using a SA4250HD), most channels come up blocked and the firewire link sometimes fails... its a nightmare as you dont know what will work or wont.

Component can do 1080p but TV networks only broadcast HD in 720p or 1080i. Its probably why the HD PVR only supports up to 1080i...

There are no flag restrictions on the HD PVR, the only restrictions will come from your cable box, and if they dont block component output then it will work just fine.

---

### Post by SnafuFlux on 2010-07-14
I've had success with my sa3250.  I haven't tried a sa4250.  but you are right.  since some (most) channels are blocked using firewire, it can be a pain.  I don't know what all I can actually record.

I'm going to re-rail the thread and take our conversation to pm.

---

### Post by handyman5 on 2010-07-14
larsolav, what you really need is the script itself: [http://github.com/handyman5/ds_downloader/raw/master/ds_downloader.py](http://github.com/handyman5/ds_downloader/raw/master/ds_downloader.py)

Download that, and then download rtmpdump: [http://rtmpdump.mplayerhq.hu/download/rtmpdump-2.3.tgz](http://rtmpdump.mplayerhq.hu/download/rtmpdump-2.3.tgz)

Once you have rtmpdump downloaded and uncompressed, edit the first file (my script) to point the variable RTMPDUMP to where you saved the rtmpdump executable.

If you already have MythNetTV set up, you can also fix that path in the MYTHNETTV variable; if you don't, setting it up is a little out of the scope of this response.

Once all that's done, run the script with the URL of an episode:

```
ds_downloader.py http://www.thedailyshow.com/full-episodes/thu-july-8-2010-marilynne-robinson
```

And then it should download the episode for you and save it in the current directory as "output_######.avi". You can then play that with mplayer or xine or whatever, or if you set up MythNetTV it'll get imported into MythTV automatically.

- Adam

---

### Post by handyman5 on 2010-07-14
LowSky, I just researched what you were talking about, and that's interesting.

Right now I have a HD HomeRun, and I was able to record full-HD for broadcast channels along with SD for the cable channels, which was fine with me. Then Comcast locked down the encryption on even SD cable channels, so now all I can record is broadcast (and HGTV, which for some strange reason is still unencrypted).

To use a Hauppage box, I'd have to actually _get_ a HD cable box from Comcast, and then get the Hauppage box and tear out my HD HomeRun... but then I could record cable channels again. I'll have to think about it.

Thanks,
Adam

---

### Post by LowSky on 2010-07-14
Why tear out the HD HomeRun? keep it to record broadcast channels... then you can record 3+ channels (multirec) at one time.

---

### Post by nickrout on 2010-07-15
> **handyman5 said:**
> *Removed for violating Comedy Central ToS*

I don't know what the rules are in this forum, but the mythtv devs will never adopt a script that does what you are doing if it contravenes the web site's terms of use.

So does it?

---

### Post by larsolav on 2010-07-15
> **nickrout said:**
> I don't know what the rules are in this forum, but the mythtv devs will never adopt a script that does what you are doing if it contravenes the web site's terms of use.

So does it?
Here is a link to THEDAILYSHOW.COM Terms of use agreement:
[http://www.thedailyshow.com/help/terms](http://www.thedailyshow.com/help/terms)
I'm having a hard time finding anything in the agreement that would be problematic...

---

### Post by tgm4883 on 2010-07-15
Looks problematic to me

> You shall not, nor will you allow any third party (whether or not for your benefit) to reproduce, modify, create derivative works from, display, perform, publish, distribute, disseminate, broadcast or circulate to any third party (including, without limitation, on or via a third party web site), or otherwise use, any Material without the express prior written consent of Comedy Partners or its owner if Comedy Partners is not the owner.

Closing thread. PM me if you feel this is in error.

---

