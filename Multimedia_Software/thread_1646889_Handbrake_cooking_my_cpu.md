---
title: "Handbrake cooking my cpu"
date: 2010-12-16
forum: Multimedia Software
---

### Post by GrannyTux on 2010-12-16
Hello I have been hunting for a couple of days on this topic so I decided to post. I have been using handbrake for years and the last snapshot has caused havoc on my system . CPU temp go through the roof and my system shuts down. Encoding with acidrip does not do this but I prefer handbrake and would like to find out if there is a way I can throttle down CPU usage . I don't mind if it takes longer to rip , better than the whole computer shutting down.

I am using Ubuntu 10.04 with all the updates, HandBrake svn3707 , amd II x4 940 , 4gigs ddr2 , mb chipset is 790GX and using onboard gpu.

Anything else I am using to encode does not do this .

---

### Post by rubylaser on 2010-12-16
I'd post this question on the Handbrake forums and provide them a logfile as well as dumping your cpu core temps out to a text file.  I run 3707 on three 64 bit boxes and haven't seen any change in temps.

---

### Post by Yellow Pasque on 2010-12-16
Your system should never shut down from overheating, even it's running with full load for a while (especially if it's a desktop). Either your temp sensor is inaccurate or your cooling system is inadequate. Can you overheat your CPU by running multiple instances of CPUburn (or some other instensive benchmark that pegs all your cores)?

I don't really see it as a Handbrake issue. Perhaps the latest version of Handbrake is better multi-threaded and makes more use of the CPU to get the job done quicker. That's not a problem with Handbrake though.

---

### Post by inobe on 2010-12-16
sounds like your cpu heatsink is caked with dust bunnies or the heatsink needs thermo paste.

that said, lets learn howto apply some [http://www.techpowerup.com/articles/overclocking/134](http://www.techpowerup.com/articles/overclocking/134)

also you may want to talk with the manufacturer to see if it's under warranty before tampering, if it's custom built' i would talk with the builder and ask him why he forgot thermal paste !

now if the heatsink fan is loaded with dust, that has to be clean no matter what.

---

### Post by GrannyTux on 2010-12-17
Well i build my own units and keep them pretty clean , I just updated to the Dec 12th snapshot of handbrake and the issue went away go figure..
Thanks for the thought and ideas..

---

### Post by inobe on 2010-12-17
> **GrannyTux said:**
> Well i build my own units and keep them pretty clean , I just updated to the Dec 12th snapshot of handbrake and the issue went away go figure..
Thanks for the thought and ideas..

well if your a builder like most of us, we aren't perfect.

on one of my intel systems a heatsink tab popped loose and it went unnoticed for weeks, i heard the fan racing just opening firefox, i went to encode a video and the system shut down, this is when i noticed the popped tab, unfortunately the damage was done and the system dragged, eventually i had to replace the cpu.

btw i have the handbrake ppa and i receive upgrades on a regular basis, i haven't experienced this heat issue.

---

