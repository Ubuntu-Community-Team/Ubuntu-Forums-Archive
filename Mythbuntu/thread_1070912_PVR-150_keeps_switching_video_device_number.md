---
title: "PVR-150 keeps switching video device number"
date: 2009-02-15
forum: Mythbuntu
---

### Post by konadad on 2009-02-15
I had originally configured my PVR-150 as /dev/video0 and it was working fine.  After installing my DVICO FusioHDTV5Lite as DVB0, I now am seeing on random start attempts of the mythbox that the PVR-150 will sometimes be listed in the Frontend as "unavailable".

Probing around more one of the times that this happened, I then found in the Backend Capture card setup that the /dev/video0 was being probed as my DVICO card.  Just changing the device for the PVR-150 to /dev/video1 gave me correct probed info, I restarted the backend, and was back up and running great.

Now this morning I started it up again, and the PVR-150 was once again unavailable and even though it was still setup as /dev/video1 I had to switch it back now to be /dev/video0 to get it to probe to the correct card.

Any ideas what could cause this?  Is there a way to permanently lock a card to the correct device setting?  

I think that what it is trying to do is even though the DVICO card is being used as DVB (ATSC tuner) it is still picking the card up as an additional device for analog???  That's fine, but I just need a way to lock it in to a given device number.

---

### Post by konadad on 2009-02-16
Okay, so more digging around and I think I found the applicable bug, which appears to have been fixed in the last month or so.

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/126812](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/126812)

So being relatively new to Linux - will this fix just automatically come through with the normal updates that you can download - or is there some way that I need to go get it and apply it myself?

I can definitely wait a few weeks for it, but if it won't come by itself I would love some help in how to go get this update so I stop having to go into backend setup every time I restart.

---

### Post by azmyth on 2009-02-17
Write a udev rule and you'll never worry about them switching again.

```

#udevinfo -q path -n /dev/video0
#cd /sys/then/path/from/previous/command

cat the vendor and devise

```

Then add a file to the /etc/udev/rules.d like 55-custom.rules

with
```
KERNEL=="video[0-1]", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYMLINK+="pvr150"
KERNEL=="video[0-1]", SYSFS{vendor}=="0x1131", SYSFS{device}=="0x7133", SYMLINK+="somename"
```

Then run mythsetup and change to the new links.

---

### Post by klc5555 on 2009-02-17
> **azmyth said:**
> Write a udev rule and you'll never worry about them switching again.

```

#udevinfo -q path -n /dev/video0
#cd /sys/then/path/from/previous/command

cat the vendor and devise

```

Then add a file to the /etc/udev/rules.d like 55-custom.rules

with
```
KERNEL=="video[0-1]", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYMLINK+="pvr150"
KERNEL=="video[0-1]", SYSFS{vendor}=="0x1131", SYSFS{device}=="0x7133", SYMLINK+="somename"
```

Then run mythsetup and change to the new links.

Might be easier just to edit the "options" file  (under /etc/modprobe.d ) and add one line for the PVR 150 along this vein:

options ivtv  ivtv_first_minor=1

which should compel the pvr 150 always to load as /dev/video1

Then, after the reboot, set the card to the /dev/video1 in the backend setup, as usual. 

See also this thread on the mythtv forum from a couple of years ago: [http://www.gossamer-threads.com/lists/mythtv/users/274420](http://www.gossamer-threads.com/lists/mythtv/users/274420)

Cheers! :)

---

### Post by konadad on 2009-02-17
thanks klc5555!!  That was super easy and I am 2 for 2 now on reboots with it recognizing the pvr150 properly.

---

### Post by konadad on 2010-01-10
So with mythbuntu working great for around a year, I decided to upgrade to 9.10 this weekend.  Now this problem is back again - every time I restart my computer the PVR-150 is switching video device numbers again, which takes the tuner offline when it doesn't match to my assigned Capture Card settings.

I verified that the Options file (options.dpkg-bak) in /etc/modprobe.d still has the ivtv line that klc5555 suggested, but apparently that is not even working now?

Anyone have any ideas?  Easiest thing right now is just leave the machine on 24/7 once it is setup, but not what I call a robust fix.

---

### Post by yonkiman on 2010-01-11
> **konadad said:**
> every time I restart my computer the PVR-150 is switching video device numbers again

Here you go: [http://ubuntuforums.org/showthread.php?t=753434](http://ubuntuforums.org/showthread.php?t=753434)

---

