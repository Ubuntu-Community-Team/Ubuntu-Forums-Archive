---
title: "[SOLVED] Livecd frontend problems"
date: 2008-05-29
forum: Mythbuntu
---

### Post by sjrice on 2008-05-29
Hi.  I'm having trouble playing recordings from a remote frontend running from the 8.04 Mythbuntu livecd.  I can play livetv just fine, but get a blank screen for a few seconds when I try to play a recording.  I do have the remote machine ip address in both places on the general backend setup screen on the server. Here's where it is failing in the mythfronend log.  It looks like it is trying to play the recordings from the local filesystem instead of from the remote machine (recordings dir on the remote machine is /mnt/store/mythtv, not /var/lib/mythtv/recordings).  The remote machine is an install of Mythbuntu 8.04, and works with other remote frontends (mythtv 0.21 compiled from source on Feisty).

Log:
2008-05-28 20:23:45.028 Connecting to backend server: 192.168.2.7:6543 (try 1 of 5)
2008-05-28 20:23:45.031 Using protocol version 40
2008-05-28 20:23:48.537 AFD: Opened codec 0x8448dc0, id(MPEG2VIDEO) type(Video)
2008-05-28 20:23:48.537 AFD: codec AC3 has 6 channels
2008-05-28 20:23:48.539 AFD: Opened codec 0x8449140, id(AC3) type(Audio)
2008-05-28 20:23:50.509 AFD: Opened codec 0x84c4220, id(MPEG2VIDEO) type(Video)
2008-05-28 20:23:50.509 AFD: codec AC3 has 6 channels
2008-05-28 20:23:50.511 AFD: Opened codec 0x84c4860, id(AC3) type(Audio)
2008-05-28 20:23:50.511 AFD: codec AC3 has 2 channels
2008-05-28 20:23:50.513 AFD: Opened codec 0x8d56880, id(AC3) type(Audio)
2008-05-28 20:23:52.766 NVP: prebuffering pause
2008-05-28 20:23:53.470 GetRecordBasename found no entry
2008-05-28 20:23:53.571 TV: Attempting to change from None to WatchingPreRecorded
2008-05-28 20:23:53.573 GetRecordBasename found no entry
2008-05-28 20:24:00.075 RingBuf(/var/lib/mythtv/recordings/): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/'.


I have tried using the frontend from the live cd from two different machines, and get the same results with the "Invalid file" message.

Any thoughts?

---

### Post by sjrice on 2008-05-31
I figured it out.  You need to set the timezone to your timezone and have Mythbuntu synchronize the time to internet servers. If you synch time up to the backend, previously recorded programs will play when using the livecd as a remote frontend.

---

### Post by dibuntux on 2008-11-18
Thanks, same problem, solved as you stated, setting time zone correctly on the client!

---

