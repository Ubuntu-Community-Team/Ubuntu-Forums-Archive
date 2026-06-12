---
title: "Watch TV - Stopped working after I changed my resolution."
date: 2009-11-26
forum: Mythbuntu
---

### Post by Gamblor74 on 2009-11-26
Help,

I'm very new to MythTV and Mythbuntu, so please go easy. 

I've Install 9.10 Mythbuntu and all was working ok for a few days. I have a Win TV Nova T 500 card, and was able to watch TV ok, after playing arround with the resolution, it stopped working. I've set it back to as it was, but all I get is please wait, and sent back to the main Menu.

Can some point me in the right direction to check log files to help me find out why it's no longer working.

Many Thanks G

---

### Post by Gamblor74 on 2009-11-27
Ok,

after serveral reboots and a rescan of the channels, the Watch TV bit is now working again.

Not sure if the resolution makes a difference to TV performance when in full screen or not, and a bit wary of messing arround with the settings again!

---

### Post by SiHa on 2009-11-27
I doubt it's the resolution that caused the problem. There is a known issue with the firmware for this card and 9.10. If you want to confirm, have a look at your syslog: ```
cat /var/log/syslog|grep dvb
```
If you get lots of "i2c error" lines, then that's your problem.

For reference, your Myth logs should be in /var/log/mythtv.

There are a couple of workarounds which both seem to work. I'm using an older version of the firmware (v1.10) which I happened to have on an old install, so it was the simplest fix for me. You can also try disabling the Active EIT scan.

Have a look at [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1111829&highlight=nova+500) thread for some tips.

---

