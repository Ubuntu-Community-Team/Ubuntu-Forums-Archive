---
title: "live tv fails"
date: 2008-10-03
forum: Mythbuntu
---

### Post by 4dognight on 2008-10-03
I am running the latest version of mythbuntu.This is on a secondary backend, connected to a cable box via firewire. I have a backend running same version. I started watching live tv on one channel succesfully. But when I changed the channel, it started doing this, and receive the following error in the frontend log.
It hangs and then displays an error and returns to the main menu.

2008-10-02 23:12:36.802 RingBuf(/var/lib/mythtv/recordings/2812_20081002231229.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/2812_20081002231229.mpg'.



The really weird part is the file exists, on the frontend/secondary backend!

 ls -l
total 0
-rw-r--r-- 1 mythtv mythtv 0 2008-10-02 23:12 2812_20081002231228.mpg
-rw-r--r-- 1 mythtv mythtv 0 2008-10-02 23:12 2812_20081002231229.mpg

At least for a few minutes. Then it goes away!

 ls -l
total 0


I tried to find what the -1 file descriptor is, but no luck.
Is it possible it is opening the file on the frontend, but is looking for it on the backend for playback? This might explain why it exists on the frontend. But if it is looking for the file on the bacend, it will never find it.

Anyone got any suggestions where to look to solve this?

Thanks

---

