---
title: "HD-PVR - almost there, but not working inside MythTV"
date: 2010-01-01
forum: Mythbuntu
---

### Post by yonkiman on 2010-01-01
Happy New Decade, everyone!

I'm running Mythbuntu 9.10, normal repos.

The HD-PVR seems installed correctly.  When I 
```
cat /dev/video1 > test1.ts
```
the resulting file is playable with video and sound.

And I have the channel changing bit working, too
```
mythchanger -c 750
```
changes the channel, and I entered "mythchanger -c " as my channel change command in MythBackend. 

I believe I've set everything up correctly in MythBackend - I'm getting all the channels from schedules direct, etc.

I can record and watch live TV with no problem on my ATSC tuner.

But I can't record or watch anything with the HD-PVR.  The channel doesn't change, no data is recorded, etc.

Does anyone have any ideas where to look next?  What & where is the best logfile to start with?

---

### Post by Chuffinora on 2010-01-01
I would look at the output of your mythbackend log

tail -50 /var/log/mythtv/mythbackend.log


It seems odd you can watch live tv but not record (My understanding is liveTV is essentially the same as recording)

---

### Post by yonkiman on 2010-01-01
> **Chuffinora said:**
> I would look at the output of your mythbackend log

Thanks - I'll do that.

> It seems odd you can watch live tv but not record

Using the HD-PVR I can not watch OR record.

I mentioned that I can watch AND record from my ATSC tuner just to indicate that my mythtv is working normally outside of the HD-PVR.

---

### Post by yonkiman on 2010-01-02
It seems to be working now...maybe all it needed was a reboot.

---

### Post by Kheops_74 on 2010-03-06
As you i can create a file using the cat command. I can't watch TV nor record. Can you help me by telling me how you install your hdpvr on your system. 

Do you change config files, do you compile something, do you update firmware? or everything work out of the box?

Thanks

---

### Post by Kheops_74 on 2010-03-06
Found the problem : "The error in the above log is that you have set the "preset tuner to
channel" setting for the HD-PVR... read the tooltip for it carefully--
it specifically cautions you that you should only set it on a device
with a tuner-- the HD-PVR has no tuner."

You don't have to put a preset channel.

---

