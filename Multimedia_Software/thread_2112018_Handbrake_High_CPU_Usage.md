---
title: "Handbrake High CPU Usage"
date: 2013-02-03
forum: Multimedia Software
---

### Post by speartip on 2013-02-03
Running 12.04 with latest version of Handbrake.
When ripping dvds using the H264 codec & .mp4 container, my cpu usage is between 97-99%.
Will running the cpu at that rate for maybe 60-90 minutes cause any damage to my computer?

---

### Post by Mark Phelps on 2013-02-03
Running at that utilization is going to drive up the heat of your CPU tremendously.  

If you have thermal limits enabled in your BIOS, what will happen, if the processor exceeds that, is that your PC will suddenly shut down. That is likely to cause corruption to the filesystem due to sudden shutdown.

If you don't have thermal limits enabled in your BIOS, the PC could still crash -- but this is likely to damage it in the process.

Sorry, but if you expect to drive your CPU at that utilization level that long, you should seriously look into after market processor cooling solutions.

---

### Post by JohnAStebbins on 2013-02-03
> **speartip said:**
> Running 12.04 with latest version of Handbrake.
When ripping dvds using the H264 codec & .mp4 container, my cpu usage is between 97-99%.
Will running the cpu at that rate for maybe 60-90 minutes cause any damage to my computer?

Despite what the previous responder says, all modern systems already have sophisticated thermal management and are not likely to fail unless there is a pre-existing hardware flaw.

Even desktop CPUs throttle themselves to control temperature these days.  When they get too warm, then lower the clock speed.  Laptop CPUs have done this for a decade.

If you are concerned about your hardware, install lm_sensors and monitor temperatures for a while.  Do some googling to find out what the thermal limits of your particular CPU are.

---

### Post by The Spectre on 2013-02-03
Another thermal protection feature that most modern computers have is that when the CPU or GPU is under load and starts to heat up the Fans are automatically increased in speed to dissipate the additional heat that is being generated.

I agree with JohnAStebbins that it would be a good idea to install a Temperature Monitoring Program on your computer to keep an eye on you Temperatures.

You probably have nothing to worry about.

I do a lot of Video Encoding on my Computers and I have never had a CPU fail on me.

I still have a old Athlon 64 X2 4600+ CPU that is being used in a Home Theater PC and sometimes it is recording as many as four shows at a time while I am watching something else and as you can imagine that puts a pretty good workout on the CPU.

---

### Post by speartip on 2013-02-04
OK...
Thanks for your reply guys.
I have instaled lm-sensors & psensor. I Have set there temp limits to 60c, (about 10c less than max) & am about to rip a 20 min DVD. Will report back.

---

### Post by speartip on 2013-02-04
After having ripped a 23min DVD to .mp4, it only took about 8mins with dual pass, and max temp reached 55c, (cpu 80-99%) that was also with rhythmbox & Google Chrome running.
 So I guess that temp is well within the temp range of my HP G5370UK Desktop with an i3 550 processor.
Thanks all for your help. I'll mark this thread as solved.

---

