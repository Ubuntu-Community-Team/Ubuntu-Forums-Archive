---
title: "MythTV and PVR-350"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by MauroKTM on 2007-02-25
I bought a new Hauppeage PVR 350 and I want to use it only to capture video from S-video. But I did'd understand how I  configure it in MythTV-setup. How can I make a channel that call a S-video input?

On mythtv setup I found dev/video0, dev/video16, dev/video24 and dev/video32. What i should use?

Many Thanx

M.

---

### Post by SyvanX on 2007-02-25
In the tuner setup (I think) is where you can tell it to use S-Video in.  You'll want to use /dev/video0 but make sure that you have the input set from S-video.  If you set it manually, it constantly resets itself, I've tried. 

I know the option is in mythtv-setup, so let me know if you can't find it.

---

### Post by MauroKTM on 2007-02-26
Thank you for the answer. Now I understood to use the card as Tuner and I can watch th TV. But I didn't understand yet how can I switch channel on S-Video or Composite input. In Mythtv-Setup I can edit a new channel I can decide the frequency but how can I say it to "tune" on S-Video or Composite Input?

Thnx, M.

---

### Post by SyvanX on 2007-02-28
Sorry for the delay.

The setting you're looking for is in mythtv-setup.  Choose option #2 "Capture Cards."  Select your capture card, it should say [MPEG: /dev/video0] or something like that.  At the bottom of the next screen there is a field that says default input.  Make sure this is set to S-Video1.  You should then be good to go.  It just tells your pvr350 to record from the S-Vid input rather than the Tuner input.  I think you can choose composite here as well, but I don't have experience with Composite in.

---

