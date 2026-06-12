---
title: "Mythbuntu Lockups"
date: 2013-02-06
forum: Mythbuntu
---

### Post by Al_Vampyre on 2013-02-06
For the last few weeks I've been getting strange lockups on my combined BE/FE. There is hard drive activity because the light is flashing but the system is completely unresponsive requiring me to manually restart the PC with the reset button.

When it happens I can't SSH in, MCE remote and keyboard don't work and occasionally it prevents me from accessing the network/internet on any computer attached to the same router until Mythbuntu is restarted.

There doesn't seem to be any trigger for it as sometimes it happens when the machine has been idle and sometimes it happens immediately after I've reset it.

I'm suspecting either hard drive or temperature but the temps seem OK and the SMART readings on all drives are reporting healthy.

Which logs should I be looking at to try and narrow it down. Also I've noticed that the Mythbuntu Log Grabber is complaining about the pastebin api but I can't seem to get it to upgrade to a newer version.

Thanks in advance

---

### Post by PhilWig on 2013-02-06
I think I'd start with hardware basics.
Test memory for several hours?  Power supply?  Clean inside box, re-seat cards?

Phil

---

### Post by Al_Vampyre on 2013-02-07
Thanks Phil, I have reseated the cards and cleaned inside the box. I'll try Memtest and the power supply next

---

### Post by tgm4883 on 2013-02-07
Someone on the mailing list had a similar issue that they believe they nailed down to a bad CPU. I had a similar issue which I nailed down to either a bad power supply, or a not large enough power supply (read: I replaced the power supply).

---

### Post by Al_Vampyre on 2013-02-08
> **tgm4883 said:**
> Someone on the mailing list had a similar issue that they believe they nailed down to a bad CPU. I had a similar issue which I nailed down to either a bad power supply, or a not large enough power supply (read: I replaced the power supply).

Thanks for that, power requirements haven't changed and the system was working fine but maybe the power supply itself has degraded over time.

I've been toying with the idea of an upgrade anyway, this might be just the push I need!

Any feedback on the LogGrabber issue (complaining about pastebin api)

---

### Post by chuckrp on 2013-02-09
I have had the same issues. Cable company had to make a repair to my service due to degrade in signal. Since then it has not locked up. Don't know if that had anything to do with it or not. I did the CPU and power checks, installed 8 g of new memory and nothing helped. So hopefully this has solved the problem for me.

---

### Post by Al_Vampyre on 2013-02-10
Thanks to all those that helped, I ran MemTest86+ and stick 1 of my memory errored out immediately. I reseated it and all seems to be OK now...I hope!

---

