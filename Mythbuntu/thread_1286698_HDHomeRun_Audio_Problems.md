---
title: "HDHomeRun Audio Problems"
date: 2009-10-09
forum: Mythbuntu
---

### Post by PBK on 2009-10-09
Hello - Thanks for reading...

  I have a Ubuntu 9.04 box running MythTV 0.21.0 using Hauppauge PVR-350 and PVR-500 tuners. I added the HDHomeRun tuner that initially worked fine other than me getting the available channels displayed correctly. HDHR firmware version is now at 20090830.

  Now when watching anything from the HDHR, the audio sounds almost like a sputtering. This sputtering is constant and does not change pitch. I cannot hear any of the desired audio mixed in. Picture is just fine. When changing channels coming from the HDHR, the sputtering stops while actually changing channels, but returns when the video from the new channel appears. Audio/video is still fine from the PVR's.

  I tried viewing channels via VLC and that displays just fine. I have removed all tuners from MythTV's database and re-entered them. No change.

  Any idea what I can look at to fix this?

Thanks.
Paul

---

### Post by bsntech on 2009-10-09
Hi PBK,

I had this same sort of problem with the digital side of my HVR-1600 on only one channel.

I fixed the problem by going into the Utilities/Setup - TV Settings.  I can't remember where it is, but there is an option in one of those pages to enable extra audio buffering.  After I checked to turn this on, my problem went away.

---

### Post by PBK on 2009-10-11
Hi bsntech,

  Thanks for the reply. I appreciate it. I tried your suggestion and it worked! Thanks. I went back to remove that option for extra buffering just to check and it works too!! Oh well, it's working now. Thanks again.

PK

---

