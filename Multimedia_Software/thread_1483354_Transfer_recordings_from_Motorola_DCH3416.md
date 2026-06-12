---
title: "Transfer recordings from Motorola DCH3416"
date: 2010-05-14
forum: Multimedia Software
---

### Post by gobbles414 on 2010-05-14
I've searched Google, Ubuntu Help, and these forums, but cannot find a solution to my problem... I'd like to transfer content from the DVR in my Motorola DCH3416 cable box (Comcast) to my Ubuntu 9.10 laptop.

My understanding is that drag-and-drop from DVR to computer isn't possible with the DCH3416, and my laptop doesn't have a video capture card, so I'm thinking that "real-time" transfer via IEEE 1394 (FireWire) is the best solution for me. I've tried connecting the two devices via FireWire, but nothing happens; I'm sure that configuration is required, but I'm not sure where to begin.

I'd prefer to record using VLC, but am certainly willing to consider other software. Also, it would be helpful to know of any procedural differences between Ubuntu 9.10 and Ubuntu 10.04 -- I plan to upgrade soon.

Thanks in advance for your help!

---

### Post by gobbles414 on 2010-05-15
I've installed/configured MythTV, and it seems to be working perfectly for the programs I want to transfer. I'll post detailed instructions within the next few days (I still have a lot to learn)

---

### Post by gobbles414 on 2010-06-07
Well, my problems is not solved after all! :-(  MythTV is splitting my "Watch TV" recordings into multiple files. On my computer, this seems to be happening on the 00 and 30 of every hour. I'm unsure why that's happening -- especially since MythTV doesn't display any TV guide data from my cable box.

The closest that I've been able to find to a solution for my problem is the last post in the [http://www.gossamer-threads.com/lists/mythtv/users/49172](http://www.gossamer-threads.com/lists/mythtv/users/49172) thread, but I cannot locate anything like the programs/mythbackend/scheduler.cpp file to modify. As described in the [http://ubuntuforums.org/showthread.php?t=727127](http://ubuntuforums.org/showthread.php?t=727127) thread, other Ubuntu users have experienced "splitting" problems similar to mine.

The folks at [http://www.gossamer-threads.com/lists/mythtv/users/438670](http://www.gossamer-threads.com/lists/mythtv/users/438670) have told me that MythTV may not be the best program for my needs, but they have yet to suggest a suitable alternative. **Please help!** Thanks!

---

### Post by gobbles414 on 2010-06-22
bump

---

### Post by gobbles414 on 2010-07-30
I've been unsuccessful in preventing MythTV from splitting my recordings into multiple files... Can anyone suggest a program other than MythTV to transfer recordings from my cable box to my computer? Thanks!

---

### Post by gobbles414 on 2010-08-10
bump

---

### Post by edwardof on 2010-08-10
Without any guide data, MythTV will assume every program is 30 minutes, hence the file breaks. I think in your situation all you really need to look for is a program that can capture video from the firewire port.

---

### Post by gobbles414 on 2010-08-10
Edwardof, you're 100% correct! I need a program that will allow my computer to capture unencrypted video from my cable box's DVR. I have attempted commands such as *sudo dvgrab -f hdv* without success; depending on the syntax of the command, I'd get errors such as: ""0.00 MiB 0 frames", "Error: no HDV", etc. I've also tried VLC, but either I don't know what I'm doing and/or VLC cannot capture from my cable box's DVR.

I'm willing to try any capturing program/command that you suggest! :-)

---

### Post by gobbles414 on 2010-09-12
bump

---

