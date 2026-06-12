---
title: "Need help watching TV with new mythbuntu install"
date: 2012-09-07
forum: Mythbuntu
---

### Post by jkgiant on 2012-09-07
Having trouble with a new mythbuntu install as frontend and backend.  I believe I have the backend setup correctly. I've configured a HDHomeRun Prime and successfully scanned for and added channels.  However, when I select watch tv on the frontend, the screen only flashes a "please wait" for a split second before returning to the menu.  I'm a noob and not sure where to even start looking. Would appreciate help troubleshooting this issue.

Mythbuntu 12.04.1 32 bit, HDHR Prime.

---

### Post by nickrout on 2012-09-08
> **jkgiant said:**
> Having trouble with a new mythbuntu install as frontend and backend.  I believe I have the backend setup correctly. I've configured a HDHomeRun Prime and successfully scanned for and added channels.  However, when I select watch tv on the frontend, the screen only flashes a "please wait" for a split second before returning to the menu.  I'm a noob and not sure where to even start looking. Would appreciate help troubleshooting this issue.

Mythbuntu 12.04.1 32 bit, HDHR Prime.

You need to look in the frontend and backend logs under /var/log/mythtv.

---

### Post by jkgiant on 2012-09-08
Backend is reporting unknown tuner type.

Sep  8 15:03:33 Dimension-8300 mythbackend[1668]: E TVRecEvent dtvmultiplex.cpp:325 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
Sep  8 15:03:33 Dimension-8300 mythbackend[1668]: E TVRecEvent dtvchannel.cpp:308 (SetChannelByString) DTVChan(192.168.1.12-0): SetChannelByString(3_1): Failed to initialize multiplex options
Sep  8 15:03:33 Dimension-8300 mythbackend[1668]: E TVRecEvent tv_rec.cpp:3681 (TuningFrequency) TVRec(1): Failed to set channel to 3_1. Reverting to kState_None

---

### Post by uteck on 2012-09-09
> **jkgiant said:**
> Backend is reporting unknown tuner type.

Sep  8 15:03:33 Dimension-8300 mythbackend[1668]: E TVRecEvent dtvmultiplex.cpp:325 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
Sep  8 15:03:33 Dimension-8300 mythbackend[1668]: E TVRecEvent dtvchannel.cpp:308 (SetChannelByString) DTVChan(192.168.1.12-0): SetChannelByString(3_1): Failed to initialize multiplex options
Sep  8 15:03:33 Dimension-8300 mythbackend[1668]: E TVRecEvent tv_rec.cpp:3681 (TuningFrequency) TVRec(1): Failed to set channel to 3_1. Reverting to kState_None

Is channel 3_1 a working channel?  You can go into the mythtv-setup and change the default channel to something else if that is not a working channel.

---

### Post by robhaynes on 2012-09-10
Hey, I'm having exactly the same problem.  This setup worked for me in an earlier incarnation of mythbuntu, but I did a total clean install and oonfiguration.  It doesn't matter for me what channel I select, it seems to always return that error in the log.

DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
DTVChan(1311519D-0): SetChannelByString(2): Failed to initialize multiplex options
Failed to set channel to 2. Reverting to kState_None

I can also run the "HDHomeRun Config GUI" and tune and view the same channels it tries to tune to.

---

### Post by nickrout on 2012-09-10
> **robhaynes said:**
> Hey, I'm having exactly the same problem.  This setup worked for me in an earlier incarnation of mythbuntu, but I did a total clean install and oonfiguration.  It doesn't matter for me what channel I select, it seems to always return that error in the log.

DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
DTVChan(1311519D-0): SetChannelByString(2): Failed to initialize multiplex options
Failed to set channel to 2. Reverting to kState_None

I can also run the "HDHomeRun Config GUI" and tune and view the same channels it tries to tune to.They aren't encrypted channels are they?

---

### Post by jkgiant on 2012-09-10
I have it working now.  I hadn't configured a grabber.  I setup and configured schedules direct and downloaded their channel list.  I'm still not certain how this affected backend from not seeing the tuner.  The channels I tried were not encrypted.  The channel scan identified 3_1, which is CBS here locally.  I also tried entering as 3.1 with no luck.

---

### Post by robhaynes on 2012-09-10
Like the other poster, its CBS.  I'm not sure if my cable provider encrypts that channel or not.

---

### Post by robhaynes on 2012-09-10
I tried configuring a grabber, schedules direct.  That did not help at all.  There must have been something else.  Probably something pretty basic.

---

### Post by Bonte on 2013-05-06
> **robhaynes said:**
> I tried configuring a grabber, schedules direct.  That did not help at all.  There must have been something else.  Probably something pretty basic.

Did you ever figure this out? I'm dead in the water..

Bonte

---

### Post by Bonte on 2013-05-06
> **jkgiant said:**
> I have it working now.  I hadn't configured a grabber.  I setup and configured schedules direct and downloaded their channel list.  I'm still not certain how this affected backend from not seeing the tuner.  The channels I tried were not encrypted.  The channel scan identified 3_1, which is CBS here locally.  I also tried entering as 3.1 with no luck.

I'm am having the same exact problem as you did and were able to resolve. I'm going to send you a PM, perhaps you can assist me with a copy of your database?

Thanks,
Bonte

---

### Post by tgm4883 on 2013-05-06
This thread is old. Please open a new thread for your issue.

---

