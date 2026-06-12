---
title: "Cards are aparently constantly busy on startup so can't get a channel lock, help!"
date: 2010-05-15
forum: Mythbuntu
---

### Post by bergqvistjl on 2010-05-15
Hi, whenenver mythbackend (using 10.04 x64, with autobuilds 0.24 on (turning that on seemed to fix it for a while, yet its started doing it again) starts for the first time (i.e when the system boots) it can never open the cards (two hvr-1300's) as they are 'busy', so therefore i cant get a channel lock at all. however, if i go into mythtv setup, and just exit it again (i.e closing and starting the backend again), they obviously load fine. i tried the solution posted by db260179 here: [http://ubuntuforums.org/showthread.php?t=1481488](http://ubuntuforums.org/showthread.php?t=1481488)

but i still got the device busy error:
```
2010-05-15 11:34:00.015 DVBChan(1:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
			eno: Device or resource busy (16)
```
in the logs, (it does this for around 20 times for each card, then i presume gives up and continues to load the backend as normal).
Any ideas?

---

### Post by bergqvistjl on 2010-05-18
Bump, this is a major problem, for me, it would be nice to get any suggestions.

---

### Post by LowSky on 2010-05-18
.24?

.23 Just came out. Why would you be using a developement version?


Anyway the problem is that Myth is starting before the driver is loaded. The only thing you can do is restart the backend on boot.

You can look at this, it seems to fix things for many people
[http://ubuntuforums.org/showpost.php?p=9292366&postcount=3](http://ubuntuforums.org/showpost.php?p=9292366&postcount=3)

---

### Post by bergqvistjl on 2010-05-19
would this solution possibly work?: [https://bugs.launchpad.net/mythbuntu/+bug/556204](https://bugs.launchpad.net/mythbuntu/+bug/556204)

Its strange though, i think it knows the cards are theyre, it says there 'busy' rather than not found. I'll give it a go though. Plus ive found some updated drivers which might work.

---

### Post by bergqvistjl on 2010-05-19
OK it hasnt worked despite updating the drivers and trying the above solution i posted. No effect whatsover, even when putting a sleep in it. very annoying. I don't think its starting before the driver has loaded either, I think when it starts first time, it tells the cards to do something, which prevent them from doing anything else like getting a lock, and the cards can only be 'cleared' if i reboot the backend.

---

