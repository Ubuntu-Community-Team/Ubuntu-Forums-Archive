---
title: "Autoexpire early to keep disk space free?"
date: 2010-08-03
forum: Mythbuntu
---

### Post by JMcFly on 2010-08-03
My DVR (9.10, 2.4ghz P4 single core, 2gb ram, recording to a ~750gb SATA drive with the database and system on a ~200gb PATA drive) used to record both ATSC and NTSC perfectly using a Hauppauge 1600, but over the last 2-3 months my OTA recordings have been getting progressively worse with tiling, audible stutters, etc.  I think this is due to relying on autoexpire instead of deleting shows from the drive manually, just last night I found out about the bug causing slow delete and the web interface to not delete anything.  Could autoexpire deleting during recording cause enough disk read/writes to disrupt the recording?
 
Is there a way to set autoexpire (or write a script) that deletes the oldest autoexpire-eligible shows until a certain amount of disk space (say 10-20gb) is free every day at a set time (before primetime, when most of my shows will be recorded)?

---

### Post by LowSky on 2010-08-03
I would first check your OTA connection or your tuner card, tiling and audible stutters are a sign of a bad digital connection.

If you see this occuring during LiveTV its a clear sign of a bad connection.

Lastly there is an option under setup in the frontend for autoexpire, and I know you can set how much free space and belive you can set when things will expire. You might be better off setting a date for the recodings, instead of relying on oldest recoding gets dumped. Using the method of timed autoexpire is a great way to keep the system space freed.

---

### Post by newlinux on 2010-08-03
What filesystem are you using for your recordings? You might consider using a filesystem better optimized for deleting large files like XFS or JFS, if you can take the time to convert it over (backup files, then recopy to newly formatted partition). These filesystems delete large recording files almost instantaneously, so they'd have less impact on disk access.

But as mentioned, the place to start is with your signal. If you can, check it outside of myth.

---

### Post by LowSky on 2010-08-03
I use JFS and its one of the oldest, most stable formats I have ever used. It does have some faults, like you cant shink a JFS partition. But its one of the best fomats for large recordings.

And I had another thought. Check your CPU usage. If it is high or the chip is overheating you might see perfomance suffer. And those older P4's were known to run really hot. If you can try to run a recoding from another PC

---

### Post by JMcFly on 2010-08-04
I tried playing with the antenna (Newegg $10 special, gets USB power to boost signal) last night, turning it 90deg and plugging the USB into a different port removed the tiling on all channels but some are still stuttering (kinda odd as I had never moved the antenna since I set it up last October). For example, the 720P 16:9 on 2-1 stutters while the 4:3 feed on 2-2 does not. This PC has always seemed underpowered, I try not to watch shows while its recording an HD program and it also has issues with Hulu desktop, I can't play shows without stuttering. 
 
What's the best way to check CPU usage while recording?

---

### Post by LowSky on 2010-08-04
If its a digital recording there will be little if any CPU usage. Analog needs to be converted and if the card has hardware encoding then CPU usage will remain low.

Try rescaning your channels. 

Try chaning the profile used for playback under TV settings.

---

### Post by newlinux on 2010-08-04
Still sounds like signal problems to me. Do you have your progrms set to commercial flag while recording? That could eat up some CPU. You should install htop and then run htop from a terminal while recording/playing back something to see what CPU usage is. What kind of video card do you have?

---

### Post by JMcFly on 2010-08-04
Commercial flagging is run after recording, I don't transcode; video card is an 8x AGP ATI with 512megs, not sure on the exact model number.

---

### Post by JMcFly on 2010-08-17
While watching an HD recording, around a bad period of stutter/tiling using the slim playback profile:
1min load average: 3.67
5min : 2.98

---

