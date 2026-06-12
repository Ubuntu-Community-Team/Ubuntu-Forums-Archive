---
title: "HDHomeRun and FIOS: Unable to Scan"
date: 2009-10-24
forum: Mythbuntu
---

### Post by mars76 on 2009-10-24
HI All,

  I am using Mythbuntu 9.04 and have got HDHomeRun (Dual Tuner) .

 I am able to view the LiveTV when i use the HD Antenna which is connected to Tuner 0.

  I have connected the RF Cable output from FIOS Motorola STB to Tuner 1 of HDHomeRun.

  How ever when i try to perform a Scan for the channels i don't get any channel listing..

  Here is the output i am getting  
```

  Timeout scanning QAM-256 Chennel 2 -- no table
  Timeout scanning QAM-256 Chennel 3 -- no table
  Timeout scanning QAM-256 Chennel 4 -- no table
  Timeout scanning QAM-256 Chennel 5 -- no signal
  Timeout scanning QAM-256 Chennel 6 -- no signal

```I am not sure why it is giving the error no table for channels 2,3 ,4  & 39 !! For the rest of the channels it shows no signal.

 Is there a way i can import the channel list rather than using the scan utility of Mythtv ??

I tried running the hehomerun_config scan and it generated a file . Do i need to manually convert this into a valid channels.conf file ??

I have changed the priority of myth-backend in rc2.d file.

Thanks..

---

### Post by jaakan on 2009-10-25
Have you tried using a splitter and not going through the cable box? or just by-passing the cable box to test it?

---

### Post by mars76 on 2009-10-25
Hi,

  Thanks for your reply..

  I am doing it right now..The scan is complete it has found some channels and ran the mythfilldatabase.

Now when i go to Watch TV i only see the OTA Channels (If use my remote to change the channels it shows up only OTA Channels on Tuner 0).

Tuner 1 is connected to the FIOS Cable ( Bypassing the STB)

in mythWeb the listing shows all the channels it has scanned.

I am not sure how to switch the Tuner using my Remote ( if at all it is required).

thanks..

---

### Post by tgm4883 on 2009-10-25
The HDHomerun doesn't have an analog tuner, so you will be unable to tune anything from your STB, as it outputs in analog. You would be better off picking up either an HD-PVR (for HD, does component) or something like a PVR-150 (for SD)

---

### Post by mars76 on 2009-10-25
Hi,

  My STB is a HD STD . I guess all it's outputting in Digital..

  Again as i am by passing the STD , the second tuner is connected to the Cable wire.

  Also another issue i have is while vewing the  LiveTV with TUner 0 ( From HD Antenna) the Guide pops up on the screen every now and then without me doing any thing.!!

thanks..

---

### Post by tgm4883 on 2009-10-25
> **mars76 said:**
> Hi,

  My STB is a HD STD . I guess all it's outputting in Digital..

  Again as i am by passing the STD , the second tuner is connected to the Cable wire.

  Also another issue i have is while vewing the  LiveTV with TUner 0 ( From HD Antenna) the Guide pops up on the screen every now and then without me doing any thing.!!

thanks..

No. Doesn't matter what your STB is (HD, SD, both). Unless you are hooking up to it via Firewire, HDMI, or DVI (which AFAIK there are no tuners for the last 2), then you are outputting an analog signal from your STB. You will need an analog tuner to receive this content, which teh HDHomerun is not.

Let me dispel a common misconception. HD != Digital

---

### Post by mars76 on 2009-10-26
Hi tgm4883,

  Thanks for the info.

  I have connected the Cable to the Tuner Cards ( I have PVR-150 and AverMedia A180 and i used a Splitter and bypassed the STB)

  Now i am able to get the channels that are broadcasted by FIOS which are not encrypted.

  It seems i am getting more channels than the ones that are listed in the schedules direct listing..

  I have some issues with the TV Guide display which flickers quite often on the Live TV.

  The Remote and IR Blaster are working but not perfectly..

  I will try using a Firewire from my STB to one of the Tuner Cards and will post back how it goes..

Thanks..

---

### Post by djroketboy on 2009-11-24
mars76, 
I have the exact same setup as you. Setup the HDHR with a splitter. If you are using HD, i'm assuming it's the QIP-6200? I have it working for clear channels via firewire.

---

