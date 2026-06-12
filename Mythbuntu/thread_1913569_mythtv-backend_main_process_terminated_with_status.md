---
title: "mythtv-backend main process terminated with status 254"
date: 2012-01-22
forum: Mythbuntu
---

### Post by B34N on 2012-01-22
I've been running Mythbuntu 9.04 flawlessly for a few years. Now I'm getting the "mythtv-backend main process terminated with status 254" respawning message upon startup. I am able to get running on a previous kernel (.22 instead of .23)

I made two changes since my last reboot. First, to get HDMI audio working with a new TV, I setup created asound.conf to identify HDMI as my default. Second, to stop dhcp from stating each time, I installed BUM and turned DHCP off.

I'm still learning my way through linux, but I think this is the part of my mythbackend.log for this issue:```
2012-01-22 18:07:30.899 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2012-01-22 18:07:30.960 Using runtime prefix = /usr
2012-01-22 18:07:31.004 Using configuration directory = /home/mythtv/.mythtv
2012-01-22 18:07:31.049 Empty LocalHostName.
2012-01-22 18:07:31.093 Using localhost value of HTPC-backend
2012-01-22 18:07:31.145 New DB connection, total: 1
2012-01-22 18:07:31.183 Unable to connect to database!
2012-01-22 18:07:31.227 Driver error was [1/2003]:
2012-01-22 18:07:33.791 UPnPautoconf() - No UPnP backends found
2012-01-22 18:07:33.840 No UPnP backends found
2012-01-22 18:07:34.107 Deleting UPnP client...
2012-01-22 18:07:34.566 Failed to init MythContext, exiting.
```

---

### Post by nickrout on 2012-01-22
Use the previous kernel than!

However you are ruunning a very old version of mythtv. You should upgrade to 0.24-fixes.

---

### Post by B34N on 2012-01-22
> **nickrout said:**
> Use the previous kernel than!

However you are ruunning a very old version of mythtv. You should upgrade to 0.24-fixes.

I've been running this old version because it took me a long time to get it working and I'm afraid that if I change it, I will break something (as I did). I did change the repositories to point to old-releases so that I could upgrade the restricted drivers to get my HDMI video to work. 

Is upgrading to the latest fixes straight forward or do I need to do a whole system upgrade?

---

### Post by nickrout on 2012-01-22
> **st8ofmi9d said:**
> I've been running this old version because it took me a long time to get it working and I'm afraid that if I change it, I will break something (as I did). I did change the repositories to point to old-releases so that I could upgrade the restricted drivers to get my HDMI video to work. 

Is upgrading to the latest fixes straight forward or do I need to do a whole system upgrade?

Actually I think you would need to upgrade to at least 10.04 which is an LTS release. But you might as well wait for 12.04 which will also be LTS.

---

### Post by B34N on 2012-01-22
> **nickrout said:**
> Actually I think you would need to upgrade to at least 10.04 which is an LTS release. But you might as well wait for 12.04 which will also be LTS.

Understood. I'll do that once I get a backup drive large enough to backup what I have currently working. Too bad prices have gone up so much recently...hopefully they will come back down soon.

With luck I'll get LinuxMCE working with my HVR-2250 so then I can retire my old Mythbuntu system which has served me so well for so very long.

---

