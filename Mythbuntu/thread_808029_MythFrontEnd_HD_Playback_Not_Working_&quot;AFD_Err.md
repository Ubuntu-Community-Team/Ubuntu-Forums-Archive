---
title: "MythFrontEnd HD Playback Not Working &quot;AFD Error: Unknown decoding error&quot;"
date: 2008-05-26
forum: Mythbuntu
---

### Post by gasheets on 2008-05-26
Hello,

I've got a clean install of MythBuntu 8.04 on new hardware.  Everything installed fine, and I can record off of my HDHomeRun, or my pCHDTV 5500 without issue.  From the recordings window, I can even see the thumbnail version of the recording playback.  But when I go to watch, the screen just goes black - no playback.  I can play the recording in VLC without issue, it just seems to be MythFrontEnd.  I thought maybe I had a bad install,  or a 64Bit codec issue, so I tried the i386 version, and have the same issue.  This is all new hardware, so something could be bad, but every other piece of myth functions correctly.  Standard def recordings off the PVR-150 work without issue in MythFrontEnd....

I get this over and over in my frontend log:
2008-05-25 16:13:44.347 [mpegvideo_xvmc @ 0xb733ab88]get_buffer() failed (1 1073741824 2 (nil))
2008-05-25 16:13:44.347 AFD Error: Unknown decoding error
2008-05-25 16:13:44.798 NVP: Prebuffer wait timed out 10 times.
2008-05-25 16:13:45.966 [mpegvideo_xvmc @ 0xb733ab88]get_buffer() failed (1 1073741824 2 (nil))
2008-05-25 16:13:45.966 AFD Error: Unknown decoding error
2008-05-25 16:13:45.969 [mpegvideo_xvmc @ 0xb733ab88]get_buffer() failed (1 1073741824 2 (nil))
2008-05-25 16:13:45.969 AFD Error: Unknown decoding error
2008-05-25 16:13:45.974 [mpegvideo_xvmc @ 0xb733ab88]get_buffer() failed (1 1073741824 2 (nil))
2008-05-25 16:13:45.974 AFD Error: Unknown decoding error
2008-05-25 16:13:46.064 TV: Attempting to change from WatchingRecording to None
2008-05-25 16:13:46.065 [mpegvideo_xvmc @ 0xb733ab88]get_buffer() failed (1 1073741824 2 (nil))
2008-05-25 16:13:46.065 AFD Error: Unknown decoding error
2008-05-25 16:13:46.129 NVP: Prebuffer wait timed out 10 times.
2008-05-25 16:13:46.226 TV: Changing from WatchingRecording to None
2008-05-25 16:13:46.276 DPMS Reactivated.
2008-05-25 16:13:46.375 AFD: Opened codec 0xaf0cc7

I've been a KnoppMyth user for years, and wanted to make the switch, but I don't know how to correct this issue.  I may try KnoppMyth to see what happens on this hardware.

Anyone seen this before, or have any suggestions what might be wrong?

Thanks,

Tony

---

### Post by gasheets on 2008-05-27
I installed KnoppMyth, as I am more familiar with that distro, just to see if the problems persists.  It did not.  Playback via the frontend on KnoppMyth worked great.  So, it appears that it is not the hardware.  Codecs?  Drivers?  Can anyone tell me where to look?  I would really prefer to use MythBuntu.

---

### Post by johnlr on 2008-07-12
Yeah, I was having the same problem
Try a different tv playback profile.
I was getting the blank screen with CPU+, but CPU++ works for me.

CPU++ seems to be using about 50% CPU@1.8GHz on the athlon x2 3800
Gonna try fiddling with the profiles as I don't have HD telly and would like the cpu to drop back to 1GHz if possible

---

### Post by johnlr on 2008-07-12
Aha..

Allocating 64MB to the graphics in the BIOS also now lets me use CPU+ again. HD playback is managing on ~50% CPU at 1GHz

---

### Post by gasheets on 2008-07-14
John,

That's great info.  I'll try this next week when I have some time and report back.  Thanks!!!

---

