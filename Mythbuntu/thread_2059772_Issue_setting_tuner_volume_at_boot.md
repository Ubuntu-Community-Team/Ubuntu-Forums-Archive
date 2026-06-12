---
title: "Issue setting tuner volume at boot"
date: 2012-09-18
forum: Mythbuntu
---

### Post by jdk82 on 2012-09-18
Hi all,

I'm having an issue setting tuner volume at boot. I'm running 12.04 with .25-fixes and separate frontends/backend. I have two HVR-2250's and in order to avoid blowing out my ears I want to lower the volume on the analog tuners to match the volume on the digital tuners. I noticed a couple of different things while trying to accomplish this:

1) Setting the volume in the "Recording Profiles" section of the backend setup didn't work (it actually didn't change the volume level at all).
2) Running 'v4l2-ctl --get-ctrl=volume -d /dev/video0' returned 'volume: 0' even though the volume was still extremely high.
3) Running 'v4l2-ctl --set-ctrl volume=0 -d /dev/video0' changed the volume to an appropriate level, even though the previous command indicated that the tuner was already using that setting value.

So, I added the command 'v4l2-ctl --set-ctrl volume=0 -d /dev/videoX' (where X is the appropriate device number) for each card to /etc/rc.local, which is executable for owner, group, and others. After a reboot the volume in mythtv was reset to it's previous (very high) level, even though item 2 from above returned the same. When I ran the command from item 3 above, it had the desired effect.

My question is how to properly set that command at boot.

Thanks,

Josh

---

