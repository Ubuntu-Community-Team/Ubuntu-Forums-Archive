---
title: "hardware switch on acer TravelMate 4500"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by anderssl on 2009-02-14
Hey,
I can't get the wireless network card to work on my acer travelmate 4501, after just having installed ubuntu 8.10. I have been following this howto:
[http://ubuntuforums.org/showthread.php?t=541953](http://ubuntuforums.org/showthread.php?t=541953)
However, after having done all it says, I get a strange result. The command
```
cat /sys/class/net/*/device/rf_kill
```
gives either 0 or 2, changing each time I press the hardware switch.
(Also I notice that if it's in the 0 state, the led blinks periodically - otherwise it stays off.)

This is kind of weird, because it worked before, on the same machine, when I used a previous version of ubuntu (not quite sure which - i had to delete and reinstall, long story).

Can anyone help me figure this out?

---

