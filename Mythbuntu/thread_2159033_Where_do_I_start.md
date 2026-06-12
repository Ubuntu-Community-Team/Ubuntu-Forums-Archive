---
title: "Where do I start"
date: 2013-07-01
forum: Mythbuntu
---

### Post by wlraider70 on 2013-07-01
Sorry this is a noob question. I check the stickies but some of the links are dead and others are older than my children. 

I'm thinking of setting up a PVR (is that different from a DVR?)

i have lots of old computer hardware. I would like to use that so I was thinking of a card with some processing power on it. 
I'm only really interested in 1 channel at a time for now.
I have cable from charter I have an HDMI out. 

Can I do all this with one card? Any recommendations? 
Will I have any issues with HDCP?


Bonus Question
Is a raspberry pi beefy enough for a front end?

---

### Post by BicyclerBoy on 2013-07-02
I suggest you start by finding out if there is any material you can record.

The HDMI output of any cable box will be HDCP protected and force you to use analogue VGA/component output & an hd-pvr type encoder device.
This will get you H264 encoding in a mpeg2video country but then cutting/editing H264 streams is more problematic.

Alternatives:
 use a cable-card device (ceton etc)
Note you still have to check the "copy-once/copy-freely" flags..
Only windows-media-centre is an approved playback device.
The analogue recording does not have this problem but you need 2 boxes & channel changing scripts IR blasters etc.

Plenty of people are giving cable away & going to (legit) internet sources IPTV/HLS & OTA dvb-t (antenna).
AIUI Some cable providers are changing to aggregating local TV & providing multicast/HLS streams.

For video playback:
VDPAU on nVidia is best but if your source material is all progressive scan or just SD then most modern GPUs are okay.
The best power efficiency comes from intel iCPU/GPUs.
Haswell GPU could be as good as nVidia VDPAU (PQ only)

IMO the best low power system would use CULV/mobile iCPU & nVidia 610/620 in a mini-ITX format.

IMO The RPi does h264 _progressive scan_ video playback just okay but it is not powerful enough for usable frontend.
There are much better ARM SOC devices emerging from their proprietary binary blobs..

---

### Post by AlecJ on 2013-07-05
> **wlraider70 said:**
> 
Bonus Question
Is a raspberry pi beefy enough for a front end?


Not really beefy enough, but I've seen it done using XMBC
[http://siphon9.net/loune/2013/02/raspberry-pi-as-a-xbmc-mythtv-front-end/](http://siphon9.net/loune/2013/02/raspberry-pi-as-a-xbmc-mythtv-front-end/)

---

### Post by wlraider70 on 2013-07-07
> **BicyclerBoy said:**
> analogue VGA/component output & an hd-pvr type encoder device.
This will get you H264 encoding in a mpeg2video country but then cutting/editing H264 streams is more problematic.


Can anyone recommend a good component card? I've seen a few, but they all seem to be external.
Is there any advantage or disadvantage to this?

I'm in the US. I don't plan to edit much (if any) of what is saved.

---

