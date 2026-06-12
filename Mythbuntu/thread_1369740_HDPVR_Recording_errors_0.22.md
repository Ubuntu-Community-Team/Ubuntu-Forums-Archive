---
title: "HDPVR Recording errors 0.22"
date: 2010-01-01
forum: Mythbuntu
---

### Post by Chuffinora on 2010-01-01
Over xmas I took the plunge and upgraded to 0.22 on a new hard drive to use the HDPVR that I have been sitting on.

I appear to have everything working, including the IR remote, but am getting 99% failure on recording.  At some point during the recording (Either Live TV or recording) the recording will stop, the HDPVR red-light stays on but the box is locked up the IR no longer works.  I have to cycle the power,  rmmod HDPVR, then modprobe HDPVR driver to get it back.   The point in the recording can be a few seconds in or 50 mins,  usually it happens in the first 10 mins.

The backend log gives the following error message

2010-01-01 12:33:24.470 DevRdB(/dev/video0) Error: Poll giving up
2010-01-01 12:33:24.535 MPEGRec(/dev/video0) Error: Device error detected
2010-01-01 12:33:24.598 DevRdB(/dev/video0): Stop(): Not running.


I am also seeing a lot of these errors in my log (But am not sure if they are related to the lockup)

2010-01-01 12:30:03.499 AFD Error: Unknown decoding error
2010-01-01 12:30:03.555 [h264 @ 0x18d7620]B picture before any references, skipping
2010-01-01 12:30:03.610 [h264 @ 0x18d7620]decode_slice_header error
2010-01-01 12:30:03.199 TVRec(1): RingBufferChanged()
2010-01-01 12:30:03.666 [h264 @ 0x18d7620]no frame!


I am running Ubuntu 9.10  Kernel 2.6.31-16,  
Mythtv  0-22-fixes [23034] from the Avernard repository
I am using the HDPVR driver that is patched for the IR remote from [www.mythtv.org/wiki/Hauppauge_HD-PVR#Compile_Drivers_for_IR_Transmitter_Support](www.mythtv.org/wiki/Hauppauge_HD-PVR#Compile_Drivers_for_IR_Transmitter_Support)

The WAF is taking a serious hit here.

---

### Post by Chuffinora on 2010-01-02
I believe I have solved the problem (or found a workaround).    I replaced the HDPVR driver with the stock Ubuntu 9.10 driver,  and have just had 4.5hrs of trouble free recording.  Yesterday, it fialed 10-15x, every single recording.  

It looks like the patched driver for the IR remote is causing problems.   Dont knw enough about or drivers to troubleshoot this one further.

I have put my PVR-150 card back into the system and am using that for the IR remote.

---

### Post by Kheops_74 on 2010-03-10
What you mean by :"I replaced the HDPVR driver with the stock Ubuntu 9.10 driver"?

I have the same problem but i'm unable to solve it.

Thanks

---

### Post by Chuffinora on 2010-03-10
Its a bit hazy now  (Mine has been working fine since then... touch wood)  

 I think if you followed the instructions here

[www.mythtv.org/wiki/Hauppauge_HD-PVR](www.mythtv.org/wiki/Hauppauge_HD-PVR)

for compiling LIRC modules for IR transmitter support, you can just reverse the process

ie.  You find your backed up copy of the driver  using "locate hdpvr.ko"     and replace it

---

### Post by timconradinc on 2010-03-11
I had a similar experience. I'd set up the HD-PVR to work under Mythbuntu, and everything was working fine. I then tried to set up the IR modules using the instructions on the fore-mentioned wiki link, and the HD-PVR couldn't record for very long (I think I only tried live tv). I ended up reverting my changes by putting back the original hdpvr.ko module.

I've generally just used a wireless keyboard for controlling mythtv, and I've just gone back to doing that.

Also, I've had better results with recording with a slight sleep in the change channel script. With no sleep, I'd get recordings with no audio or video. Adding 4 seconds of sleep seems to have rectified this problem.

---

