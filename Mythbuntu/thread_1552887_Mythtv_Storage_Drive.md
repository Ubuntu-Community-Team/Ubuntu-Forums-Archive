---
title: "Mythtv Storage Drive"
date: 2010-08-14
forum: Mythbuntu
---

### Post by agentsmith23 on 2010-08-14
I have my system setup to use an external HDD for mythtv storage. For some reason when I first boot up the machine it detects the drive but it can't access it through mythtv until I click on the drive and open it. After clicking on it all is good. Is there some command I can run at startup to make the drive startup automatically so I don't have to click on it every time?


I looked a little further into the problem and it seems that each time my computer reboots the external drive needs to be remounted. On Ubuntu's site there is a section on automounting USB devices and everything is setup correctly for that. For automaounting it seems like it only works if I unplug the drive then plug it back in. I would really like to find a way to have this drive automount when it is plugged in during the boot process. Is there a command I could setup to autorun?

---

### Post by klc5555 on 2010-08-14
> **agentsmith23 said:**
> I have my system setup to use an external HDD for mythtv storage. For some reason when I first boot up the machine it detects the drive but it can't access it through mythtv until I click on the drive and open it. After clicking on it all is good. Is there some command I can run at startup to make the drive startup automatically so I don't have to click on it every time?

External USB or similar hard disks are detected at boot, but do not get automounted from the fstab file. The USB drivers load up after the disk check and fstab have already completed their jobs.

On my systems, I use external drives only for mythvideo storage, not for TV recording. To have the external drives automounted at boot, I put the mount commands for them in the rc.local file. The rc.local runs late enough in the boot process that the needed USB drivers have already loaded, and the drives mount without problems.

But for external drives intended for TV recording from mythbackend, there might conceivably be an additional issue with the fact that the mythtv backend seems to load before rc.local runs. But I don't know this for certain since my external drives don't participate in tv storage groups.

---

