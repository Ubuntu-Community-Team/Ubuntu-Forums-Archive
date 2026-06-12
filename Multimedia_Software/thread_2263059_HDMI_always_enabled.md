---
title: "HDMI always enabled"
date: 2015-01-29
forum: Multimedia Software
---

### Post by panchon on 2015-01-29
Hi,

I have a problem with the HDMI output in the Asrock q1900m motherboard.

If it boots with the HDMI connected, the motherboard shows the video, without problems. The problem is boot the pc without the HDMI connected, when i connect the HDMI, the pc do not shown the video.
Is there any mode to have the HDMI always enabled?

thank you

---

### Post by efflandt on 2015-01-30
Are you booting with some other video initially connected or headless (no video at all)? X automatially configures video connections when it starts, but does not automatically sense any added video hot plugged in. How would it know what resolution and frequency to use with nothing connected? So you either need to log out of X and log back in, or possibly use "Detect Displays" button in Displays of System Settings. I don't know if there is some way to set a script or hot key to detect added or switched displays.

---

