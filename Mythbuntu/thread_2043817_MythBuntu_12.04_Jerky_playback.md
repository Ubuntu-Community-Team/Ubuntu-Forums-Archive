---
title: "MythBuntu 12.04 Jerky playback"
date: 2012-08-17
forum: Mythbuntu
---

### Post by image_editor on 2012-08-17
I have recently installed mythbuntu on an old pc.
The pc is an old hp dc7900. The unit records from livetv fine HD and SD however on playback every 3 to 4 seconds the playback from recorded tv stutters. The sound is fine.
Does anyone have any suggestions for this?:popcorn:

---

### Post by Lester_Burnham on 2012-08-17
Hi,

Try using a different video playback profile. I think they only have intel on board video, so try a few of the non VDPAU profiles, 
Utilities > setup > video from memory.
[http://www.mythtv.org/wiki/VAAPI](http://www.mythtv.org/wiki/VAAPI)

lester

---

### Post by GuiGuy on 2012-08-17
> **Lester_Burnham said:**
> Hi,

Try using a different video playback profile. I think they only have intel on board video, so try a few of the non VDPAU profiles, 
Utilities > setup > video from memory.
[http://www.mythtv.org/wiki/VAAPI](http://www.mythtv.org/wiki/VAAPI)

lester

Hi Lester, 
I have the same issue and have played with the profiles from 'til the cows come home. No fix. Fast action sports like the AFL are  un-watchable, so I have settled to use the screens inbuilt tuner. 

My observation is that I on the same hardware on early mythbuntu versions I did not have the problem. 



Cheers

---

### Post by nickrout on 2012-08-17
> **GuiGuy said:**
> Hi Lester, 
I have the same issue and have played with the profiles from 'til the cows come home. No fix. Fast action sports like the AFL are  un-watchable, so I have settled to use the screens inbuilt tuner. 

My observation is that I on the same hardware on early mythbuntu versions I did not have the problem. 



Cheers
Your first port of call is your frontend logs. However what video hardware do you have? Is there a difference between SD and HD?

---

### Post by Rotak on 2012-08-18
Well, sometimes it helps to install the driver for the video card, sometimes it helps to UNINSTALL the driver. That's what I found out.

The problem with the videp profiles was already handled here: [http://ubuntuforums.org/showthread.php?t=1956746](http://ubuntuforums.org/showthread.php?t=1956746)

Good Luck!!

---

### Post by GuiGuy on 2012-08-18
> **nickrout said:**
> Your first port of call is your frontend logs. However what video hardware do you have? Is there a difference between SD and HD?

There is no difference between HD and SD, with stop start motion being the norm. However, if I record the program and playback it is fine. 

Looking at the log for live tv sessions, the only significant messages I see are frequent lines stating:

> Decode Ringbuffer.cpp:1085 (Waitforavail) <path to livetv mpg> waited 8.0 seconds for data

---

### Post by GuiGuy on 2012-08-18
> **nickrout said:**
> Your first port of call is your frontend logs. However what video hardware do you have? Is there a difference between SD and HD?

OK, I managed to get better results by switching to VDPAU SLIM, using VAAPI Accelerator decoder. I'm on ATI graphics. 

on SD the stutter is gone, but remains everso slightly on HD. 

Thanks

---

### Post by image_editor on 2012-08-19
> **Lester_Burnham said:**
> Hi,

Try using a different video playback profile. I think they only have intel on board video, so try a few of the non VDPAU profiles, 
Utilities > setup > video from memory.
[http://www.mythtv.org/wiki/VAAPI](http://www.mythtv.org/wiki/VAAPI)

lester

Thanks Lester, i changed the playback profile to normal from one of the "VDPAU" profiles. The quality isnt quite as good. Playback looks grainier but theres no jerkiness.
Thanks heaps for the tip, my family appreciates it!
Regards Damian

---

### Post by GuiGuy on 2012-08-19
Out of curiosity, am I right to understand that VDPAU is not restricted to NVIDIA hardware? 

It seems to have made a world of difference on my ATI frontend, althought I do have to use the VAAPI Accelerator decoder.

---

### Post by GuiGuy on 2012-08-20
> **image_editor said:**
> i changed the playback profile to normal from one of the "VDPAU" profiles. The quality isnt quite as good. Playback looks grainier but theres no jerkiness.

I'm noticing similar degradition of the images...

---

### Post by nickrout on 2012-08-20
> **GuiGuy said:**
> Out of curiosity, am I right to understand that VDPAU is not restricted to NVIDIA hardware? 

It seems to have made a world of difference on my ATI frontend, althought I do have to use the VAAPI Accelerator decoder.

VDPAU only works on nvidia graphics cards with nvidia drivers, but if you have changed the details of the VDPAU profile, it is no longer the VDPAU profile and is something else.

---

