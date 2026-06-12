---
title: "RT2500 goes slow after ~1 minute"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by kiwibonga on 2009-11-12
Hi there,

I've been reading about a lot of people having trouble getting their RT2500-based card to stay at 54M... Their speed is fine and normal for a while, and then suddenly slumps down to < 200 kB/s; iwconfig reveals that the rate is set to 1M, and manually setting it back to 54M temporarily fixes the issues.

But this seems to be an issue with older versions of the driver; I'm running Karmic and my rate is always 54M... I do experience the same symptoms though.

The only thing I can do is disconnect from the wireless network and reconnect; transfers jump back to max speed (1.2MB/s) instantly. Wired connection doesn't suffer from this issue, nor does Windows XP.

Any idea how I could diagnose this?

Thanks in advance!

---

### Post by Bart6114 on 2009-12-26
I can confirm this. I have exactly the same problem.

RT2500 @ 64-bit Karmic

Regards

Edit:
I think I just found a workaround in this topic: [http://ubuntuforums.org/showthread.php?t=1304759&highlight=karmic+rt2500](http://ubuntuforums.org/showthread.php?t=1304759&highlight=karmic+rt2500)

the solution:
> sudo iwconfig wlan0 txpower auto
and then disable/enable wifi connection

Edit2:
Unfortunately this didn't fix it, it still went slow after about 5 minutes.

---

### Post by Bart6114 on 2009-12-29
I read somewhere that this should be fixed in the 2.6.32 kernel. I installed it, but unfortunately it doesn't fix the speed problem. It remains the same. After connecting the speed is normal, after a few minutes it drops to about 80kbytes/s (instead of 1mbp/s).

Through all this iwconfig says the bitrate is at 48Mb/s. Setting it manually doens't do anything.

Does anyone have any ideas?

---

### Post by peterx14 on 2009-12-30
Your problem sounds a bit different to mine, but it might be worth trying [the command in this post](http://ubuntuforums.org/showpost.php?p=8585746&postcount=2) to see if it fixes it.

---

### Post by Bart6114 on 2010-01-03
Thanks for your suggestion, but it doesn't work either.
I also tried te following, but to no avail: [http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/]("http://sprayfly.com/2009/11/17/improve-wireless-performance-in-ubuntu-karmic-on-asus-eeepc-1005ha/")

Regards

---

