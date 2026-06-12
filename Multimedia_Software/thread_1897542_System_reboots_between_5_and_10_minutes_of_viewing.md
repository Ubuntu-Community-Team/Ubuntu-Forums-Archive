---
title: "System reboots between 5 and 10 minutes of viewing video file"
date: 2011-12-19
forum: Multimedia Software
---

### Post by chandra on 2011-12-19
I am on a Kubuntu 11.10 AMD 64 system with an on-board ATI HD 3200 graphics processor and an ATI SB ALC889A card.

Since 17 Dec 2011, when I view a video file in full screen mode, the system restarts sometime between 5 and 10 minutes of start of viewing, making it impossible to view anything longer. This problem did not surface previously.

I thought it might be a vlc problem and switched to smplayer, but the problem remains.

Has anyone else experienced this and are there any hints on what the cause might be? FYI, my system software is up-to-date.

Thanks in advance.

---

### Post by azmyth on 2011-12-19
I know this may sound wrong but I would check your CPU fan. Samething happened to me and it was a cpu fan that slipped off and any high CPU intense operations caused the computer to shutdown.

---

### Post by inobe on 2011-12-19
i second the post above and want to add that dust packed in heatsinks, poor ventilation will cause over heating and ultimately a shutdown/ reboot.

also a possible sign that the power supply could be on it's way (insufficient power) to keep it running. 

a side note: i repair pc's for a living.

---

### Post by chandra on 2011-12-20
Thank you azmyth and inobe for drawing attention to overheating.

I have today thoroughly vacuumed my system and CPU fans and cleaned the CPU heat sink as best I can. My two core temperatures via the plasmoid are 31 and 35 degrees Celsius.

The 450 W Zebronic power supply is less than a year old and I hope that it is not the source of the problem.

After that, I fired up System Monitor to realize that akonadi/nepomuk were hogging CPU for close to 100% upon startup. I deleted the respective directories as suggested in some posts on the Web and the hogging now happens only for a few minutes after a reboot.

The video problem still persists, and is perhaps related to moving the slider or mouse or touching the video player's window edge as far as I can tell. If I leave it running with no other applications open, it does not seem to switch off. I need to investigate further.

Could X be implicated? Or screensavers or power-management?

Have there been any recent updates/backports that might have led to this?

Thanks one more.

---

### Post by inobe on 2011-12-20
> **chandra said:**
> 
The video problem still persists, and is perhaps related to moving the slider or mouse or touching the video player's window edge as far as I can tell. If I leave it running with no other applications open, it does not seem to switch off. I need to investigate further.


moving that slider to a different point of the video does draw lots of resources from the cpu and gpu.

question, do you have thermal paste on the cpu, or is it a thermal pad?

also is the heatsink firmly set?

---

### Post by dabl on 2011-12-20
> **chandra said:**
> 

The 450 W Zebronic power supply is less than a year old and I hope that it is not the source of the problem.

Even if it's 5 minutes old, if there's a defective solder joint or a weak component on it, then a full power draw from the CPU + GPU might be enough to cause it to reset.  The only way to confirm that the PSU is the source of your reboot would be to substitute a different known-working PSU.

> 


Could X be implicated? Or screensavers or power-management?



No.  Software, by itself, does not cause a computer to hard reset.  Stress on the hardware (PSU or CPU), caused by a heavy workload (like playing full screen video) might be enough if the PSU has a defect, or if the CPU thermal dissipation system is not functioning correctly.  As posted above, the problem is either the CPU heatsink is not doing its job for some reason, or the PSU has a weakness that is triggered by heavy workload.

---

### Post by azmyth on 2011-12-20
I would check that your cpu cooler isn't loose. What type of CPU do you, Intel or AMD? IMO, the intel ones are a bit trickier as I had one come lose causing the same thing that is happening to you. The video would get funny right before shutdown as the pixels would jump around. Kind of hard to explain.

May also want to try running RAM memtest even though I don't think it's your problem as mem issues tend to cause reboots at whenever but it's worth running as I've had that issue to :(

---

### Post by rajeev1204 on 2011-12-23
I would suggest  monitoring temps, easier under windows frankly with coretemp or similar to make sure overheating is not the problem.

From your post i feel it could be a faulty PSU. And if that is fine then it is mostly the mobo.

---

### Post by chandra on 2011-12-30
> **inobe said:**
> 
question, do you have thermal paste on the cpu, or is it a thermal pad?

also is the heatsink firmly set?

It is the thermal pad or foam that was supplied originally with the CPU/heatsink/fan combination.

The heatsink is set very firmly and is locked in place by two latches.

---

### Post by chandra on 2011-12-30
> **azmyth said:**
> I would check that your cpu cooler isn't loose. What type of CPU do you, Intel or AMD?

The CPU is an AMD Athlon 64 X2 5200+ Dual Core 

> **azmyth said:**
> May also want to try running RAM memtest even though I don't think it's your problem as mem issues tend to cause reboots at whenever but it's worth running as I've had that issue to :(

I have not tried that yet but I will and report here if it is the cause.

---

### Post by chandra on 2011-12-30
> **rajeev1204 said:**
> I would suggest  monitoring temps, easier under windows frankly with coretemp or similar to make sure overheating is not the problem.

I have installed a plasmoid to monitor core temperatures and they are usually in the high twenties to low thirties Celsius.

> **rajeev1204 said:**
> From your post i feel it could be a faulty PSU. And if that is fine then it is mostly the mobo.

The PSU is a cheap Zebronic 450W unit that I have now discovered does not deliver the "stated" power. It might be the cause. I am not an intense graphics user, except for the odd video and hence have never stressed it.

I hope it is not the mobo. Another, identical Gigabyte mobo gave up just after the warranty expired. So, there is a precedent there that I hope will not be repeated.

Having said that I think mobo failures are usually digital or catastrophic. The other mobo simply stopped booting; this one works well otherwise.

---

