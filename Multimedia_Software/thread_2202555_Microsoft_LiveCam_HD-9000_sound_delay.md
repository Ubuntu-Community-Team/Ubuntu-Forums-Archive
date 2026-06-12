---
title: "Microsoft LiveCam HD-9000 sound delay"
date: 2014-01-29
forum: Multimedia Software
---

### Post by superian on 2014-01-29
It's a UVC webcam, with a mono microphone... and it's looking like it's the sound that's the issue.

Using guvcview...

.. when I try to record video with no sound or sound from the sound card's microphone, it works. Video and sound, in sync.

.. when I try to record video with sound from the webcam, there's a delay of a count of about 20 before the sound input is recognised (having the VU bars checkbox set is helpful here, and it takes that long for them to appear). Video and sound are that out of sync in the resulting file, if it is usuable. 

Anyone else had this, or have any suggestions?


ian:~$ lsusb
Bus 001 Device 002: ID 045e:0779 Microsoft Corp. LifeCam HD-3000

---

### Post by superian on 2014-01-30
Trying to use this as an input to Audacity confirms that there's an enormous delay - many seconds - when trying to record from it before any sound is captured.

---

