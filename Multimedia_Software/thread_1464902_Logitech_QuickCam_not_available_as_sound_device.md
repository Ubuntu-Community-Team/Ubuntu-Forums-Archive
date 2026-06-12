---
title: "Logitech QuickCam not available as sound device?"
date: 2010-04-28
forum: Multimedia Software
---

### Post by rslee on 2010-04-28
I have a Logitech QuickCam Communicate STX that worked fine with Skype in 64-bit Jaunty, but since I've upgraded to Karmic, it no longer captures sound (video still seems to be working well).  In Skype options, the only option for all three sound devices is PulseAudio server (local), and I know this was not the case before.

Here are the relevant lines from the output of lsusb:

Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX
Bus 002 Device 002: ID 046d:c318 Logitech, Inc. 

I'm not sure how to test the webcam as audio input device in an app other than Skype.  The Sound Recorder app only shows "Capture" as a possible input.

How do I add the webcam as an audio input device, or otherwise troubleshoot the issue?

Thanks!

---

### Post by rslee on 2010-04-28
Just fixed the problem; it looks as though PulseAudio was incompletely or incorrectly installed/configured.  Following these instructions got things working. [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

