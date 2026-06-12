---
title: "HD-PVR - some help before I buy"
date: 2011-03-08
forum: Mythbuntu
---

### Post by Sternfan on 2011-03-08
Hi all,

I want to set up a Mythbuntu box to DVR tv shows.  My setup will be:

cable from outside -> Verizon box ->  component cable -> HD-PVR -> Mythbuntu box -> HDMI video out to TV

The verizon box also has an HDMI to the TV.

I need to know some basic functionality:

***Will the myth box only record what channel the verizon box is set to?  Or is is possible for me to watch (for instance) channel 100 while DVRing channel 300?**

And by extension, can you setup recording schedules for different channels?  Say at 1pm record channel 200 then at 3pm record channel 400 and so on?

Any help greatly appreciated before I drop $200 on a new HD-DVR.

Thanks,

Rob

---

### Post by LowSky on 2011-03-08
if you use the hd pvr you can only record the channel that the cable box is tuned to.

mythtv can schedule recordings. so yes program to record on channel 4 at 1pm then channel 2 at 1:30pm.. as long as they dont over lap both will record.

also the newest model oft the hd pvr is not as simple to install in linux, so be carefull the instrucitons on on this forum and on mythtv wiki.

the way the hd pvr works is it takes the component signal (which is a anaolog HD signal) and captures it to H264. So basically its capturing whatever is being sent to the tv. so there is no way to record two shows at once.

If you want to do that maybe try a normal digital tuner as well... most of them will recieve QAM channels, in other terms just the free and local channels like CBS and NBC, PBS... and so forth.

my setup uses a HVR-2250 and a HDPVR. I can record up to 5 TV chanels at once.. but its limited.

the hvr-2250 will only record channels like CBS, NBC, FOX, ABC and theCW and PBS... the HD PVR will reocrd my cable channels like comedy central or HBO.

for example see this output ```

mythtv-status

MythTV status for localhost
===========================
Status..........: Tue Mar 8 2011, 1:58 PM
Total Disk Space: Total space is 3,317.0 GB, with 2,286.7 GB used (68.9%)

Encoders:
jpc-desktop (1) - Idle
jpc-desktop (2) - Idle
jpc-desktop (3) - Idle
jpc-desktop (4) - Idle
jpc-desktop (5) - Idle

Scheduled Recordings:
2011-03-08 20:00:00 - Glee (Fox5-HD)
2011-03-08 21:00:00 - V (WABC-HD)
2011-03-08 21:01:00 - Raising Hope (Fox5-HD)
2011-03-08 21:31:00 - Traffic Light (Fox5-HD)
2011-03-08 22:00:00 - White Collar (USA Network)
2011-03-08 23:00:00 - The Daily Show With Jon Stewart (Comedy Central)
2011-03-08 23:31:00 - The Colbert Report (Comedy Central)
2011-03-09 00:01:00 - Tosh.0 (Comedy Central)
2011-03-09 21:31:00 - Mr. Sunshine (WABC-HD)
2011-03-09 22:00:00 - Off the Map (WABC-HD)
```

that is everything set to record  for today and part of tomorrow. My system is used as a server. basically there are 5 computers in the house and people can set recordins as they wish. and watch from their own room.

---

### Post by Sternfan on 2011-03-08
Thanks for the prompt reply.  This looks like bad news, I was hoping that the HD-PVR could record any channel, regardless of what channel the cable box was set to.

You state:
*mythtv can schedule recordings. so yes program to record on channel 4 at 1pm then channel 2 at 1:30pm.. as long as they dont over lap both will record.*
Does this mean that I need to manually change the cable box channel to 4 at 1pm, then change the channel to 2 at 1:30?

Thanks,
Rob

---

### Post by rhpot1991 on 2011-03-08
> **Sternfan said:**
> Thanks for the prompt reply.  This looks like bad news, I was hoping that the HD-PVR could record any channel, regardless of what channel the cable box was set to.

You state:
*mythtv can schedule recordings. so yes program to record on channel 4 at 1pm then channel 2 at 1:30pm.. as long as they dont over lap both will record.*
Does this mean that I need to manually change the cable box channel to 4 at 1pm, then change the channel to 2 at 1:30?

Thanks,
Rob

You would normally do this by either firewire or the included IR blaster that comes with the HDPVR.

---

### Post by Sternfan on 2011-03-14
OK - I did some checking - I went to Best Buy and looked at the actual HD-PVR - the box seems to imply that it can change channels (I am assuming with the IR blaster).

I then went to the Hauppage website and downloaded the manual.  It mentions the IR blaster cable and how to make it work changing channels etc.

So it looks like I get a partial solution - the HD-PVR will only record the channel that the cable box is set to, however, that if you use the IR blaster the HD-PVR can change channels when needed.  And I assume that once I set this up, I use the IR blaster as my main remote for the cable box?  Does all this sound right?

Thanks,
Rob

---

### Post by LowSky on 2011-03-14
yes thats the sum of it.

you do have other options... if you stick with Windows you can use a Ceton InfiniTV 4. It uses cable card so it will depend if your cable company complies to the standard, which they should. That set will cost you $399 and cable card rental usually under $5 a month

---

