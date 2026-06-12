---
title: "Frequent frontend lockups since upgrade to Precise/0.25"
date: 2012-05-02
forum: Mythbuntu
---

### Post by geoffp on 2012-05-02
Anyone else getting this? I've had it freeze on me while sitting at the main menu, and also when seeking backwards in Live TV.

This is with Nvidia/VDPAU, but I'd be surprised if that affected the main menu.

---

### Post by Patrick27 on 2012-05-04
Happening to me.  Fresh install, using the 'slim' option.  Frontend hard drive thrashes for awhile, then after a certain amount of time it stops.  I can't do anything during it to troubleshoot once it starts, so it must be a real-time process that's taking over...?

---

### Post by nickrout on 2012-05-04
> **Patrick27 said:**
> Happening to me.  Fresh install, using the 'slim' option.  Frontend hard drive thrashes for awhile, then after a certain amount of time it stops.  I can't do anything during it to troubleshoot once it starts, so it must be a real-time process that's taking over...?

logs?

---

### Post by Patrick27 on 2012-05-04
> **nickrout said:**
> logs?

I do believe most of the traffic is writing to the ext4 journal (based on iotop), but I don't see anything unusual in the log files.

EDIT: It actually seems to be reading a tremendous amount of data in the mythfrontend.real --syslog local7 process.

---

### Post by Patrick27 on 2012-05-04
While I can't confirm this works completely yet, after some repeated testing I've found that turning off realtime priority threads has made things much better for me (in brief testing).

I'll report back in a day or so..

EDIT: This did not solve the problem.

---

### Post by andrewc6l on 2012-05-05
I've run into similar symptoms with 0.25 on 10.04 LTS. The thread for that is
[http://ubuntuforums.org/showthread.php?t=1974121](http://ubuntuforums.org/showthread.php?t=1974121)

---

### Post by nickrout on 2012-05-05
> **andrewc6l said:**
> I've run into similar symptoms with 0.25 on 10.04 LTS. The thread for that is
[http://ubuntuforums.org/showthread.php?p=1190909](http://ubuntuforums.org/showthread.php?p=1190909)

wrong thread i think.

---

### Post by Patrick27 on 2012-05-11
> **Patrick27 said:**
> While I can't confirm this works completely yet, after some repeated testing I've found that turning off realtime priority threads has made things much better for me (in brief testing).

I'll report back in a day or so..

No better with the most recent version, and I still don't have enough data to pin down the problem to anything.  It seems unrelated to the backend, but the frontend just cranks away, reading something from the disk.

The realtime priority threads didn't fix the problem.

---

### Post by geoffp on 2012-05-29
I think I've got it.

The last thing in the frontend log I see upon discovering a freeze is mythweather trying to pull down some weather data. I uninstalled the mythweather plugin, and I haven't had a freeze since.

EDIT: 4 days now and no lockups. Looking good.

---

