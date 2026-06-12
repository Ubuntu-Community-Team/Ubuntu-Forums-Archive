---
title: "Possible To Display Live Video w/HD-PVR?"
date: 2009-11-29
forum: Mythbuntu
---

### Post by brianafischer on 2009-11-29
Is it possible to display live video from MythTV?

I have an HD-PVR and my wife would like to watch Comcast On-Demand.  When browsing through the menu's there is a 3-4 second delay.  I don't want to record this content, just view it.

Also, is there a way to capture video/control the HD-PVR outside of MythTV?

MythBuntu 9.10
MythTV 0.22
HD-PVR
AirStar Air2PC HD5000
Hauppage WinTV HVR-1600 MCE

---

### Post by theophile on 2009-11-29
> **brianafischer said:**
> Is it possible to display live video from MythTV?

I have an HD-PVR and my wife would like to watch Comcast On-Demand.  When browsing through the menu's there is a 3-4 second delay.  I don't want to record this content, just view it.
Certainly. 0.22 has support for the HD-PVR as an other capture device. You can record or watch live TV as you please. There will always be a delay when using the cable box's native controls because that's how a DVR works. Live TV is recorded and played back simultaneously. If you plan to use the COmcast ondemand system with MythTV, you'll either have to live with the delay, or connect the passthrough ports on the back of the HD-PVR to your TV, then switch over your TV input to watch straight off the cable box.

> Also, is there a way to capture video/control the HD-PVR outside of MythTV?
See here:
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Bitrate_and_Picture_Controls](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Bitrate_and_Picture_Controls)
Make sure to shut down your backend first, to avoid hardware conflicts.

---

