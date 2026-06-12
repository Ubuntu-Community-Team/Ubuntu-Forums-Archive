---
title: "Mouse and keyboard freeze when running pavucontrol, skype calls"
date: 2011-07-01
forum: Multimedia Software
---

### Post by zettabyte on 2011-07-01
I'm running Ubuntu 10.10, 64-bit.

When I run `pavucontrol` (0.9.9), or start a call on Skype (2.2.0.25), my mouse and keyboard freeze (no input is accepted).

The OS continues to run fine, video plays, the Skype call works without issue.

All mouse input events cease (when running `evtest /dev/input/event4`).  The mouse and keyboard start responding again after killing pavucontrol from an SSH session, or hanging up the call on Skype.

From what I can tell, X doesn't freeze (video, UI events continue to occur), the OS runs fine, audio output continues to speakers and headset.  Only the mouse and keyboard freeze, and probably because the events stop reaching the kernel?


If anyone can shed some light on why this might happen, and how I might go about debugging the problem, I would be very appreciative!


Thanks!

---

### Post by zettabyte on 2011-09-12
For the record, I was able to solve this problem by plugging my USB Keyboard and Mouse directly into my computer.

They were plugged into a USB Hub (Belkin F5U407), and for whatever reason that hub stopped taking input when pavucontrol or Skype were running (obviously something to do with PulseAudio)...

Anyway, hopefully this will help someone else in the future.

---

