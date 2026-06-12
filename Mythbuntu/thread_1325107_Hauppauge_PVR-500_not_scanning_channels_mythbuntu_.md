---
title: "Hauppauge PVR-500 not scanning channels mythbuntu 9.10"
date: 2009-11-13
forum: Mythbuntu
---

### Post by bcambre on 2009-11-13
Did a fresh install (with latest updates) of mythbuntu 9.10.

However, when trying to scan for channels in the Europe-West region (Belgium); the progress bar does not move...

when i do 
```
ivtv-tune /dev/video0 -t europe-west -c E10
```
and then record via
```
cat /dev/video0 > /tmp/test.mpg
```
it is working just fine and i can see what has been recorded

when I switch to this channel using the ivtv-tune command while the scan progress is running, the progress bar does move.

what could be causing this?

I used to have a Debian myth system (3 years old) that I want to move to this new platform. Is it possible that i somehow (my memory fails me if I had to do that 3 yrs ago) have to RESET the PVR-500 card to do a decent scan ?

---

### Post by DwalerXIII on 2009-11-22
hello,

I have a Hauppauge PVR-350 and also not able to scan the channels in the Europe-West region (Belgium).
On channel E2 (the first channel), mythbuntu says "Can not lock" (Kan niet vergrendelen).

---

### Post by bcambre on 2009-11-23
Were you able to tune and record via ?
```
ivtv-tune /dev/video0 -t europe-west -c E10
cat /dev/video0 > /tmp/test.mpg

```

If at all possible, download an older version 8.04 and try it again.  Then upgrade to next versions; worked for me. Seems only to be an issue with 9.10

Ultimately, it is also possible to skip channel scanning and to manually input every channel/frequency (you can get the list from zenders.be if you're on Telenet (formerly Integan)).  Easiest to do this is via mythweb.

---

