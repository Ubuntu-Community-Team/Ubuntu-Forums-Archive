---
title: "Using RTC for video timing"
date: 2009-10-22
forum: Mythbuntu
---

### Post by cabbage on 2009-10-22
Dear all,

I'm getting intermittent tearing on playback which I'm putting down to video timing issues as described here:

[INDENT][http://www.mythtv.org/wiki/Frame_display_timing](http://www.mythtv.org/wiki/Frame_display_timing)[/INDENT]

I'm running mythbuntu 9.04 with 0.21-fixes.

I'd like to get the RTC timing option working but I'm getting a permissions error:

[INDENT]RTCVideoSync: Could not open /dev/rtc, Permission denied.[/INDENT]

Now /dev/rtc links to /dev/rtc0 which has owner and group of root 770.

So how do I change the group on /dev/rtc0 to include mythtv?


Thanks,

Cabbage.

---

### Post by cabbage on 2009-10-24
OK... Thanks to inspiration from this thread:

[INDENT][http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)[/INDENT]

I've created a udev rule to modify the group permission on the rtc0 device:

[INDENT]KERNEL=="rtc0", ATTR{name}=="rtc_cmos", GROUP="mythtv"[/INDENT]

This works... but now I get the following error from mythfrontend:

[INDENT]RTCVideoSync: Could not set RTC frequency, Permission denied.
[/INDENT]

I've already modified sysctl.conf and set:

[INDENT]dev.hpet.max-user-freq = 1024[/INDENT]

What else do I need to do?

---

### Post by xinix on 2009-10-26
I'm not sure I can see a difference while using RTC.  But I did get past this error. ```
RTCVideoSync: Could not open /dev/rtc, Permission denied
```

I did this by changing the permissions for /dev/rtc0 so that all users have access to it.  Not a pretty fix but it does give the results you want.

Use this command, as sudo/root, to do it manually:
```
chmod 666 /dev/rtc0
```

After doing this you will see something like this in your mythfrontend log:
```
2009-10-25 22:32:28.893 Video timing method: RTC

```

---

