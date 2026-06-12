---
title: "AVerMedia DarkCrystal HD Capture Pro"
date: 2012-12-31
forum: Mythbuntu
---

### Post by fabricator4 on 2012-12-31
I'm currently setting up my first media center, but being on a budget it seems like a frame grabber is the way I'll be going.  I can't find much specific information, and a lot of the general information I'm finding is very old - five or more years old in fact.

This card seems to fit the specs - component video capture in 1080 HD which looks like it will work with the satellite HDTV box (also not set up yet).

The lack of information makes me hopeful that this card will just work out of the box with Ubuntu/Linux, but I'm very wary since I know this is an area where hardware support has been quite difficult.

An alternative card appears to be the Black Magic Intensity Pro card but it appears to be twice the price for no apparent benefits on paper.

Has anyone used either of these cards, or know of any compatibility issues?

Thanks,
       Chris

---

### Post by nickrout on 2012-12-31
> **fabricator4 said:**
> I'm currently setting up my first media center, but being on a budget it seems like a frame grabber is the way I'll be going.  I can't find much specific information, and a lot of the general information I'm finding is very old - five or more years old in fact.

This card seems to fit the specs - component video capture in 1080 HD which looks like it will work with the satellite HDTV box (also not set up yet).

The lack of information makes me hopeful that this card will just work out of the box with Ubuntu/Linux, but I'm very wary since I know this is an area where hardware support has been quite difficult.

An alternative card appears to be the Black Magic Intensity Pro card but it appears to be twice the price for no apparent benefits on paper.

Has anyone used either of these cards, or know of any compatibility issues?

Thanks,
       ChrisI believe that neither of these cards works with linux. Linux.tv.org has a wiki with details of what is supported, I can't find either there.

If you want to capture analogue high definition you will need a hauppauge HDPVR 1212. Pretty sure that's the only supported one in linux.

---

### Post by fabricator4 on 2013-01-01
> **nickrout said:**
> I believe that neither of these cards works with linux. Linux.tv.org has a wiki with details of what is supported, I can't find either there.

If you want to capture analogue high definition you will need a hauppauge HDPVR 1212. Pretty sure that's the only supported one in linux.

This seems to give me some hope: [blackmagic gstreamer plugin]("http://ubuntuforums.org/showthread.php?t=1333927")

Avermedia's stance on Linux is friendly, but they don't appear to get involved in development: [LinuxTV]("http://www.linuxtv.org/wiki/index.php/AVerMedia")

Blackmagic appear to be advertising Linux compatibility (drivers) however if the open Gstreamer plugin doesn't work, it might mean paying for the Blackmagic ones:  [Linux friendly PRO hardware]("http://www.kdenlive.org/forum/linux-friendly-pro-hardware-blackmagic-design").

Generally, I'm still very wary: Having spent enough time in hardware compatibility Hell I'm very keen on avoiding any more of it, however budget constraints may force me down one of these paths.

There's much better information on tuner cards available which I find strange - I had thought that the HD device preliferation would have generated a lot more interest (and information) on capture cards.

Chris

---

### Post by fabricator4 on 2013-01-01
> **nickrout said:**
> I believe that neither of these cards works with linux. Linux.tv.org has a wiki with details of what is supported, I can't find either there.

If you want to capture analogue high definition you will need a hauppauge HDPVR 1212. Pretty sure that's the only supported one in linux.

I've been having a look at the Hauppauge devices.  Anything with "PVR" in the model appears to be a personal video recorder.  It doesn't appear to have any way of communicating with the PC, however it's about the same price as the Black Magic Intensity Pro.

Actual capture devices - either digital or frame grabbers all appear to have "Win" as part of the model name.  That's almost enough to scare me spitless right there.

Chris

---

### Post by nickrout on 2013-01-01
> **fabricator4 said:**
> This seems to give me some hope: [blackmagic gstreamer plugin]("http://ubuntuforums.org/showthread.php?t=1333927")

Avermedia's stance on Linux is friendly, but they don't appear to get involved in development: [LinuxTV]("http://www.linuxtv.org/wiki/index.php/AVerMedia")

Blackmagic appear to be advertising Linux compatibility (drivers) however if the open Gstreamer plugin doesn't work, it might mean paying for the Blackmagic ones:  [Linux friendly PRO hardware]("http://www.kdenlive.org/forum/linux-friendly-pro-hardware-blackmagic-design").

Generally, I'm still very wary: Having spent enough time in hardware compatibility Hell I'm very keen on avoiding any more of it, however budget constraints may force me down one of these paths.

There's much better information on tuner cards available which I find strange - I had thought that the HD device preliferation would have generated a lot more interest (and information) on capture cards.

Chris

[1] If you came here for advice, you got it. Buy an hauppauge 1212 - $189 on newegg right now.

If you want to buy  something else and play with it, maybe write a linux kernel driver, then you are welcome to do so, but it doesn't seem to be where you are coming from.

mythtv does not use gstreamer to capture.

Question: when you capture from HDMI with the mediamagic gstreamer plugin, does it (illegally if you are in the US at least) strip the HDCP protection that will inevitably be there? If it doesn't, then it is useless in linux for capturing TV (although it may be great for the uses the they advertise it for - capturing from your HD camera).

If it does illegally break the DCMA then the mythtv developers (mostly US based) will not have a bar of it. Go to [1]. Do not waste $200.

---

### Post by fabricator4 on 2013-01-01
> **nickrout said:**
> [1] If you came here for advice, you got it. Buy an hauppauge 1212 - $189 on newegg right now.

If you want to buy  something else and play with it, maybe write a linux kernel driver, then you are welcome to do so, but it doesn't seem to be where you are coming from.

mythtv does not use gstreamer to capture.

Question: when you capture from HDMI with the mediamagic gstreamer plugin, does it (illegally if you are in the US at least) strip the HDCP protection that will inevitably be there? If it doesn't, then it is useless in linux for capturing TV (although it may be great for the uses the they advertise it for - capturing from your HD camera).

If it does illegally break the DCMA then the mythtv developers (mostly US based) will not have a bar of it. Go to [1]. Do not waste $200.

Unfortunately Newegg don't ship OS. Outlets in Australia I tried don't seem to have the 1212, but do have the HD-PVR2.  It's unclear whether it just an updated device, or a completely and possibly incompatible device.

The reason I specified the component input as given on both the Blackmagic and Avermedia cards was the problem of HDMI *possibly* being encrypted, however HDMI input would be beneficial otherwise.  (The hd-PVR2 has HDMI input also, probably to cater for the gaming market.  The 1212 does not appear to have HDMI input, but it's not a deal breaker.

Do you know if the HD-PVR2 is otherwise the same as the 1212 (ie compatible with MythTV?

Chris

---

### Post by nickrout on 2013-01-01
> **fabricator4 said:**
> Unfortunately Newegg don't ship OS. Outlets in Australia I tried don't seem to have the 1212, but do have the HD-PVR2.  It's unclear whether it just an updated device, or a completely and possibly incompatible device.

The reason I specified the component input as given on both the Blackmagic and Avermedia cards was the problem of HDMI *possibly* being encrypted, however HDMI input would be beneficial otherwise.  (The hd-PVR2 has HDMI input also, probably to cater for the gaming market.  The 1212 does not appear to have HDMI input, but it's not a deal breaker.

Do you know if the HD-PVR2 is otherwise the same as the 1212 (ie compatible with MythTV?

ChrisSorry I hadn't picked up your address. 

I beleive the HDPVR2 is different and not supported, but if investigations reveal otherwise I will post back.

You could get yourself a prezoom account - they provide a US shipping address and forward to you. I have used it successfully to NZ.

---

### Post by fabricator4 on 2013-01-01
> **nickrout said:**
> Sorry I hadn't picked up your address. 

I beleive the HDPVR2 is different and not supported, but if investigations reveal otherwise I will post back.

You could get yourself a prezoom account - they provide a US shipping address and forward to you. I have used it successfully to NZ.

I've got a lead on a secondhand unit.  If it doesn't come good I'll investigate prezoom and other outlets that will ship overseas. It seems that I can order one from Hauppaute direct, for about $60 shipping (nearly $300 US total).  I've just spec'd up a cheap box based on the AMD FX-6100 3.3GHz.  It's bang-for-buck at $379, but the wife is going to kill me...

If the HD-PVR2 is a different box, then it's very dissapointing that the all the Australian suppliers have dropped the HD-PVR in preference to it.  I think there were one or two I did find, but didn't consider because they were at least 2 1/2 times the US price.

Chris

---

### Post by nickrout on 2013-01-01
> **fabricator4 said:**
> I've got a lead on a secondhand unit.  If it doesn't come good I'll investigate prezoom and other outlets that will ship overseas. It seems that I can order one from Hauppaute direct, for about $60 shipping (nearly $300 US total).  I've just spec'd up a cheap box based on the AMD FX-6100 3.3GHz.  It's bang-for-buck at $379, but the wife is going to kill me...

If the HD-PVR2 is a different box, then it's very dissapointing that the all the Australian suppliers have dropped the HD-PVR in preference to it.  I think there were one or two I did find, but didn't consider because they were at least 2 1/2 times the US price.

ChrisHold off, the thought that you were australian crossed my mind in the middle of the night! Can't you get most of your programming via DVB-T - in that case you simply need some DVB-T cards, or an HDHomerun. Why are you going satellite?

---

### Post by fabricator4 on 2013-01-02
> **nickrout said:**
> Hold off, the thought that you were australian crossed my mind in the middle of the night! Can't you get most of your programming via DVB-T - in that case you simply need some DVB-T cards, or an HDHomerun. Why are you going satellite?

Yes, free to air is all terrestrial, Foxtel is all Satellite.  We've had it for years and are simply upgrading to HDTV and HD DVB-S along with it.  I've been thinking about the media center for years and now seems to be a good time. 

The side benefit is, my wife will finally have to start using an Ubuntu box for something.  Give me a couple of years and I might get her weened off Windows completely. ;-)  I'll encourage her to use the media center for other things as well, and eventually convince her to upgrade her office machine once she's happy with Libre Office.  Mythbuntu, the thin end of the wedge!

Chris

---

