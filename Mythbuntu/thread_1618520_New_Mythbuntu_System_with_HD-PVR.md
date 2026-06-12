---
title: "New Mythbuntu System with HD-PVR"
date: 2010-11-10
forum: Mythbuntu
---

### Post by thakk on 2010-11-10
I am getting back into myth after a two year hiatus. I grabbed the Mythbuntu 10.10 iso as it looks to be easier than installing Fedora and then myth on top. I wanted a sleeker system since I have upgraded to HD.

I've looked at the myth wiki with the hd-pvr and don't seem to see the howto on getting the IRBlaster and remote working.

During the mythbuntu install, it asked what type of tuner I have, but I didn't see the hd-pvr listed.

Post install I checked /dev and I have a video0 and I was able to cat /dev/video0 > temp.ts and was able to play that in VLC.

It looks like a quick test of my hardware has some stuff working.

Is there a newer howto on a full install with the hd-pvr? I have a new box I am using.
Also, I have 3 two TB hard drives I put in it and plan on LVMing them together. Will the install do this automatically for me or is this something I should ssh in after the fact and do some of that?

Or does someone have a better suggestion for what to do with these three drives? I was tempted to raid 5 them together so I have a failsafe, but I guess it is only TV afterall.

Thanks.

---

### Post by LowSky on 2010-11-10
HDPVR wiki has all the answers

to install onto mythtv
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Steps_to_Add_the_HD-PVR_as_a_Capture_Device_in_MythTV_.280.22_or_later.29](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Steps_to_Add_the_HD-PVR_as_a_Capture_Device_in_MythTV_.280.22_or_later.29)

to get the remote working
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support](http://www.mythtv.org/wiki/Hauppauge_HD-PVR#IR_Transmitter_Support)

Sorry I'm horrible with drive info

---

### Post by thakk on 2010-11-10
I was thru that document already, but during the mythbuntu install I don't know what to pick for capture. Also the remote setting I'm not sure what to pick.

Do I just do I hit none at that point and run the myth control centre after everything is installed?

Thanks.

---

