---
title: "Mythtv sluggish after installing 2nd tuner"
date: 2008-04-18
forum: Mythbuntu
---

### Post by Afkpuz on 2008-04-18
I am running mythtv 20.2 and have two PChdtv 5500 tv tuners.  Originally, I was running only one 5500 and things worked great.  So, I decided to upgrade and now, the live tv stutters and even recordings made before stutter as well.  I don't even know where to begin to diagnose this problem.  My computer specs are below.  I think they are good enough to run two tuners?


3.0 Ghz hyper-threading P4
2.0 Gb of ddr2 ram
160 Gb hdd
Nvidia 8600 GT (This might not be exactly the right card, but it's a good Nvidia card)


Any help would be appreciated.

---

### Post by klc5555 on 2008-04-19
On a machine with similar specs (only 1.5 Gb memory), I installed 2 pchdtv5500s, and, since the analog half of these cards is pretty useless for recording, added a Hauppauge 150 for reliable analog reception/recording.

I found that while watching HD on the pchdtv5500s, live tv would stutter a bit every few minutes. Moreover, if I was recording an HD program, I could not record a second program simultaneously --HD, non-HD digital, nor even analog on the Hauppauge --without both recordings being ruined because of dropped frames, etc.

DVD play would also skip, and I decided that the culprit was how everything was being buffered onto the one hard disk, a 250 Gig IDE Western Digital.

So I added a second HD, a zippy 1 TB SATA drive, on which I put a single large partition and mounted as /var/lib/mythtv/recordings. Everything except for the recordings stayed on the 1st HD.

Stuttering stopped in this arrangement, and also I find I can now record two HD programs and an analog one simultaneously, and all three recordings come out fine.

So I suspect that the problem may be that all the disk writes for the OS, Mythtv, and the two tuners are stepping on each other in your single-disk arrangement.  Especially if it's a slower disk.

Good luck!

---

### Post by Afkpuz on 2008-04-19
So , you just set recordings to record to your second HDD?  Did you change any other settings or is it just because the newer drive is quick?

---

### Post by klc5555 on 2008-04-19
Just set it up correctly as the recordings directory. No other changes.

The SATA drive is much quicker, which is the main thing with the 5500s moving 6 Gb of data per hour. But also now swapfile writing and such does not step on the recording to the second disk.

I intend to add a fourth tuner to this setup, another Hauppauge for a second analog input, unless I discover Hardy has miraculously supplied a fixed dvb-v4l driver to rehabilitate the analog half of the 5500s. But in either event, I don't anticipate a hardware bottleneck affecting another tuner.

---

