---
title: "Lost correct resolution after upgrade"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by Miakehl on 2007-10-29
I upgraded from 7.06 to 7.10 via the upgrade feature and it all with pretty soothly but after the upgrade the resolution is messed up. I have the Intel 965 chip and a 1440x900 screen. In 7.06 I used the intel 915 fix but in 7.10 1440x900 gives me a weirdly shaped screen and the monitor give me the input not supported message. There something about the way 7.10 displays 1440x900 I guess.

Chip: Intel 965
Screen: HP w19b

History

I tried the 915 fix but it give me the distorted and not supported error.
I tried xorg conf but It gives me way too many other non screen resolution related settings to screw up

So far I'm fine with the upgrade but the screen resolution problem is becoming unbearable.

---

### Post by MrFSL on 2007-10-30
Get all the correct info about your monitor and run :

```
sudo dpkg-reconfigure xserver-xorg
```

---

