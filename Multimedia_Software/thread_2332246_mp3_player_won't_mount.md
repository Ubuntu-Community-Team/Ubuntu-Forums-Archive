---
title: "mp3 player won't mount"
date: 2016-07-29
forum: Multimedia Software
---

### Post by acefromspace on 2016-07-29
I got a new mp3 player (claims it should show as removable drive) and it doesn't show up at all (tried both power off/on) Other mp3 players have worked fine, but clicking on my computer shows nothing. It does recommend windows (even XP) and shows connection though USB cable... but doesn't support Mac (even though when I ordered it it, I think it did) Any way around this?
mp3 player is AGPTek AO2 (S) model. Do I really need Windoze (been years since I did) or should I order another player? Any software ( free) that might solve this issue?

---

### Post by ajgreeny on 2016-07-29
To see if the mp3 player is detected plug it in and immediately run command ```
dmesg | tail
```

---

### Post by gordintoronto on 2016-07-30
Could you connect the MP# player, then turn it on, and then run the command: lsusb

What version of Linux?

---

### Post by acefromspace on 2016-07-31
OK, I got it to work. When I first connect it with USB cable (player off) it shows "choose connection type", but only for a few seconds. I hit center button on player (like enter) and it showed up. Loaded a few songs and tested... it works! I'm using Ubuntu 14.04 LTS. Seems like problem solved, but want to try again before marking thread as solved.

---

### Post by Yellow Pasque on 2016-07-31
It sounds like this mp3 player has poor documentation regarding MSC/MTP mode...

---

### Post by acefromspace on 2016-08-02
I did a few tests... I finally changed from Ubuntu 12.04 to 14.04 (very similar, just a few things different, might have thrown me off) First try I did not see drive (mp3 player) because it didn't show in computer. After I tried again (and clicked "charge and transfer", it also had "charge and play") now it showed up and worked fine. Now it works every time just connecting USB. It only gives you 5 seconds, and this confused me, but it works great and has other features like time, calendar, voice recording, video, ect. for less than $30 US. Very good battery (they claim up to 70 hours) All is well in Linux land... I should have ordered and extra for my wife (she stole my original mp3 player... my new one is better :)

---

